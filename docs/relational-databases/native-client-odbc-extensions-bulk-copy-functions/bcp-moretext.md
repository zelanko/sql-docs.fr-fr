---
title: bcp_moretext | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_moretext
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_moretext function
ms.assetid: 23e98015-a8e4-4434-9b3f-9c7350cf965f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 239bc3a5957c69e1262bf8229b6bdf85fae4ea67
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85783415"
---
# <a name="bcp_moretext"></a>bcp_moretext
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Envoie une partie d'une valeur de type de données longue et de longueur variable à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_moretext (  
        HDBC hdbc,  
        DBINT cbData,  
        LPCBYTE pData);  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *cbData*  
 Nombre d’octets de données copiés vers SQL Server à partir des données référencées par *pData*. Une valeur de SQL_NULL_DATA indique NULL.  
  
 *pData*  
 Pointeur vers le segment de données long, de longueur variable, pris en charge à envoyer à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Remarques  
 Cette fonction peut être utilisée conjointement avec des [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) et des [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) pour copier des valeurs de données longues de longueur variable en SQL Server dans plusieurs segments plus petits. **bcp_moretext** peut être utilisé avec des colonnes qui ont les types de données SQL Server suivants : **Text**, **ntext**, **image**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, type défini par l’utilisateur (UDT) et XML. **bcp_moretext** ne prend pas en charge les conversions de données, les données fournies doivent correspondre au type de données de la colonne cible.  
  
 Si **bcp_bind** est appelé avec un paramètre *pData* non null pour les types de données pris en charge par **bcp_moretext**, **bcp_sendrow** envoie la valeur de données entière, quelle que soit la longueur. Toutefois, si **bcp_bind** possède un paramètre *pData* null pour les types de données pris en charge, **bcp_moretext** peut être utilisé pour copier des données immédiatement après un retour réussi de **bcp_sendrow** indiquant que toutes les colonnes liées avec des données présentes ont été traitées.  
  
 Si vous utilisez **bcp_moretext** pour envoyer une colonne de type de données prise en charge dans une ligne, vous devez également l’utiliser pour envoyer toutes les autres colonnes de type de données prises en charge dans la ligne. Aucune colonne ne peut être ignorée. Les types de données pris en charge sont SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT et SQLXML. SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY et SQLVARBINARY appartiennent également à cette catégorie si la colonne est un varchar (max), nvarchar (max) ou varbinary (max), respectivement.  
  
 L’appel de **bcp_bind** ou [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) définit la longueur totale de toutes les parties de données à copier dans la colonne SQL Server. Une tentative d’envoi d’SQL Server plus d’octets que ce qui est spécifié dans l’appel à **bcp_bind** ou **bcp_collen** génère une erreur. Cette erreur se produit, par exemple, dans une application qui a utilisé **bcp_collen** pour définir la longueur des données disponibles pour une colonne de **texte** SQL Server sur 4500, puis appelée **bcp_moretext** cinq fois en indiquant à chaque appel que la longueur de la mémoire tampon de données était de 1000 octets.  
  
 Si une ligne copiée contient plus d’une colonne de longueur variable, **bcp_moretext** envoie tout d’abord ses données à la colonne à numérotation ordinale la plus basse, suivie de la colonne numérotée ordinale suivante, et ainsi de suite. Il est important de définir correctement la longueur totale des données attendues. Il n'existe aucun moyen de signaler, en dehors du paramètre de longueur, que toutes les données pour une colonne ont été reçues par copie en bloc.  
  
 Lorsque les valeurs **var (max)** sont envoyées au serveur à l’aide de bcp_sendrow et bcp_moretext, il n’est pas nécessaire d’appeler bcp_collen pour définir la longueur de la colonne. Au lieu de cela, pour ces types uniquement, la valeur se termine en appelant bcp_sendrow avec une longueur de zéro.  
  
 Une application appelle normalement **bcp_sendrow** et **bcp_moretext** dans les boucles pour envoyer un certain nombre de lignes de données. Voici un aperçu de la procédure à suivre pour une table contenant deux colonnes de **texte** :  
  
```  
while (there are still rows to send)  
{  
bcp_sendrow(...);  
  
for (all the data in the first varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
for (all the data in the second varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
}  
  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment utiliser **bcp_moretext** avec **bcp_bind** et **bcp_sendrow**:  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      idRow = 5;  
char*      pPart1 = "This text value isn't very long,";  
char*      pPart2 = " but it's broken into three parts";  
char*      pPart3 = " anyhow.";  
DBINT      cbAllParts;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, "comdb..articles", NULL, NULL, DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idRow, 0, SQL_VARLEN_DATA, NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
cbAllParts = (DBINT) (strnlen(pPart1, sizeof(pPart1) + 1) + strnlen(pPart2, sizeof(pPart2) + 1) + strnlen(pPart3, sizeof(pPart3) + 1));  
if (bcp_bind(hdbc, NULL, 0, cbAllParts, NULL, 0, SQLTEXT, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Send this row, with the text value broken into three chunks.   
if (bcp_sendrow(hdbc) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart1, sizeof(pPart1) + 1), pPart1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart2, sizeof(pPart2) + 1), pPart2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart3, sizeof(pPart3) + 1), pPart3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// All done. Get the number of rows processed (should be one).  
nRowsProcessed = bcp_done(hdbc);  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
