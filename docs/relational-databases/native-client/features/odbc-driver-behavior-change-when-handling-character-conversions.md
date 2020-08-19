---
description: Changement de comportement du pilote ODBC lors de la gestion des conversions de caractères
title: Conversions de caractères de gestion des modifications ODBC
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 682a232a-bf89-4849-88a1-95b2fbac1467
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 48c2230327a92a560291aacbf802ae775b99fe8f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498893"
---
# <a name="odbc-driver-behavior-change-when-handling-character-conversions"></a>Changement de comportement du pilote ODBC lors de la gestion des conversions de caractères
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] pilote ODBC de Native Client (SQLNCLI11.dll) a modifié son mode de conversion de SQL_WCHAR * (NCHAR/NVARCHAR/nvarchar (max)) et SQL_CHAR \* (char/varchar/NARCHAR (max)). Les fonctions ODBC, telles que SQLGetData, SQLBindCol et SQLBindParameter, retournent (-4) SQL_NO_TOTAL comme paramètre de longueur/indicateur lors de l'utilisation du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client. Les versions antérieures du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client retournaient une valeur de longueur, ce qui peut s'avérer incorrect.  
  
## <a name="sqlgetdata-behavior"></a>Comportement de SQLGetData  
 La plupart des fonctions Windows vous permettent de spécifier une taille de mémoire tampon de 0, et la longueur retournée correspond à la taille des données renvoyées. Le motif suivant est bien connu des programmeurs Windows :  
  
```  
int iSize = 0;  
BYTE * pBuffer = NULL;  
GetMyFavoriteAPI(pBuffer, &iSize);   // Returns needed size in iSize  
pBuffer = new BYTE[iSize];   // Allocate buffer   
GetMyFavoriteAPI(pBuffer, &iSize);   // Retrieve actual data  
```  
  
 Toutefois, **SQLGetData** ne doit pas être utilisé dans ce scénario. Le motif suivant ne doit pas être utilisé :  
  
```  
// bad  
int iSize = 0;  
WCHAR * pBuffer = NULL;  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)0x1, 0, &iSize);   // Get storage size needed  
pBuffer = new WCHAR[(iSize/sizeof(WCHAR)) + 1];   // Allocate buffer  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)pBuffer, iSize, &iSize);   // Retrieve data  
```  
  
 **SQLGetData** ne peut être appelé que pour récupérer des blocs de données réelles. L’utilisation de **SQLGetData** pour récupérer la taille des données n’est pas prise en charge.  
  
 Ce qui suit montre l'impact du changement de pilote lors de l'utilisation d'un motif incorrect. Cette application interroge une colonne **varchar** et une liaison au format Unicode (SQL_UNICODE/SQL_WCHAR) :  
  
 Demande  `select convert(varchar(36), '123')`  
  
```  
SQLGetData(hstmt, SQL_WCHAR, ....., (SQLPOINTER*) 0x1, 0 , &iSize);   // Attempting to determine storage size needed  
```  
  
|Version du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client|Résultat de longueur ou d'indicateur|Description|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client ou antérieur|6|Le pilote a déduit par erreur que la conversion de CHAR en WCHAR serait obtenue en multipliant la longueur par 2.|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client (version 11.0.2100.60) ou ultérieur|-4 (SQL_NO_TOTAL)|Le pilote ne suppose plus que la conversion de CHAR en WCHAR ou WCHAR en CHAR est une action (Multiply) \* 2 ou (Division)/2.<br /><br /> L’appel de **SQLGetData** ne retourne plus la longueur de la conversion attendue. Le pilote détecte la conversion vers ou depuis CHAR et WCHAR, puis retourne (-4) SQL_NO_TOTAL au lieu du comportement *2 ou /2 qui peut être incorrect.|  
  
 Utilisez **SQLGetData** pour récupérer les segments des données. (Pseudo-code illustré :)  
  
```  
while( (SQL_SUCCESS or SQL_SUCCESS_WITH_INFO) == SQLFetch(...) ) {  
   SQLNumCols(...iTotalCols...)  
   for(int iCol = 1; iCol < iTotalCols; iCol++) {  
      WCHAR* pBufOrig, pBuffer = new WCHAR[100];  
      SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get original chunk  
      while(NOT ALL DATA RETREIVED (SQL_NO_TOTAL, ...) ) {  
         pBuffer += 50;   // Advance buffer for data retrieved  
         // May need to realloc the buffer when you reach current size  
         SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get next chunk  
      }  
   }  
}  
```  
  
## <a name="sqlbindcol-behavior"></a>Comportement de SQLBindCol  
 Demande  `select convert(varchar(36), '1234567890')`  
  
```  
SQLBindCol(... SQL_W_CHAR, ...)   // Only bound a buffer of WCHAR[4] - Expecting String Data Right Truncation behavior  
```  
  
|Version du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client|Résultat de longueur ou d'indicateur|Description|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client ou antérieur|20|**SQLFetch** signale qu’il existe une troncation à droite des données.<br /><br /> La longueur correspond à la longueur des données retournées, et non au contenu stocké (suppose une conversion *2 de CHAR en WCHAR, laquelle peut être incorrecte pour les glyphes).<br /><br /> Les données stockées dans la mémoire tampon sont 123 \ 0. La mémoire tampon est alors certaine de se terminer par une valeur NULL.|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client (version 11.0.2100.60) ou ultérieur|-4 (SQL_NO_TOTAL)|**SQLFetch** signale qu’il existe une troncation à droite des données.<br /><br /> La longueur indique -4 (SQL_NO_TOTAL), car le reste des données n'a pas été converti.<br /><br /> Les données stockées dans la mémoire tampon sont 123\0. - La mémoire tampon est alors certaine de se terminer par une valeur NULL.|  
  
## <a name="sqlbindparameter-output-parameter-behavior"></a>SQLBindParameter (comportement du paramètre OUTPUT)  
 Demande  `create procedure spTest @p1 varchar(max) OUTPUT`  
  
 `select @p1 = replicate('B', 1234)`  
  
```  
SQLBindParameter(... SQL_W_CHAR, ...)   // Only bind up to first 64 characters  
```  
  
|Version du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client|Résultat de longueur ou d'indicateur|Description|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Native Client ou antérieur|2468|**SQLFetch** ne retourne plus de données disponibles.<br /><br /> **SQLMoreResults** ne retourne plus de données disponibles.<br /><br /> La longueur indique la taille des données retournées du serveur, et non de celles stockées dans la mémoire tampon.<br /><br /> La mémoire tampon d'origine contient 63 octets et un terminateur NULL. La mémoire tampon est alors certaine de se terminer par une valeur NULL.|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client (version 11.0.2100.60) ou ultérieur|-4 (SQL_NO_TOTAL)|**SQLFetch** ne retourne plus de données disponibles.<br /><br /> **SQLMoreResults** ne retourne plus de données disponibles.<br /><br /> La longueur indique (-4) SQL_NO_TOTAL, car le reste des données n'a pas été converti.<br /><br /> La mémoire tampon d'origine contient 63 octets et un terminateur NULL. La mémoire tampon est alors certaine de se terminer par une valeur NULL.|  
  
## <a name="performing-char-and-wchar-conversions"></a>Réalisation de conversions CHAR et WCHAR  
 Le pilote ODBC [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client propose plusieurs manières d'effectuer des conversions CHAR et WCHAR. La logique est similaire à la manipulation d’objets BLOB (varchar (max), nvarchar (max),...) :  
  
-   Les données sont enregistrées ou tronquées dans la mémoire tampon spécifiée lors de la liaison avec **SQLBindCol** ou **SQLBindParameter**.  
  
-   Si vous n’effectuez pas de liaison, vous pouvez récupérer les données par segments à l’aide de **SQLGetData** et **SQLParamData**.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
