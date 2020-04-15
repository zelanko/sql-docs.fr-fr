---
title: Utilisation des valeurs de longueur et d’indicateurs Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- length/indicator buffers [ODBC]
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 849792f1-cb1e-4bc2-b568-c0aff0b66199
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a0c878c9038b26aa996ed206c6b8adfe8d6c21e5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306760"
---
# <a name="using-length-and-indicator-values"></a>Utilisation des valeurs de longueur et d’indicateur
Le tampon longueur/indicateur est utilisé pour passer la longueur des données dans le tampon de données ou un indicateur spécial tel que SQL_NULL_DATA, ce qui indique que les données sont NULL. Selon la fonction dans laquelle il est utilisé, un tampon de longueur/indicateur est défini comme étant un SQLINTEGER ou un SQLSMALLINT. Par conséquent, un seul argument est nécessaire pour le décrire. Si le tampon de données est un tampon d’entrée non dédiécé, cet argument contient la longueur d’entrée des données elle-même ou une valeur indicateur. Il est souvent nommé *StrLen_or_Ind* ou un nom similaire. Par exemple, le code suivant appelle **SQLPutData** à passer un tampon rempli de données; la longueur des fourre-tout (*ValueLen*) est passée directement parce que le tampon de données (*ValuePtr*) est un tampon d’entrée.  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLen;  
  
// Call local function to place data in ValuePtr. In ValueLen, return the  
// number of bytes of data placed in ValuePtr. If there is not enough  
// data, this will be less than 50.  
FillBuffer(ValuePtr, sizeof(ValuePtr), &ValueLen);  
  
// Call SQLPutData to send the data to the driver.  
SQLPutData(hstmt, ValuePtr, ValueLen);  
```  
  
 Si le tampon de données est un tampon d’entrée différé, un tampon de sortie non différé ou un tampon de sortie, l’argument contient l’adresse du tampon longueur/indicateur. Il est souvent nommé *StrLen_or_IndPtr* ou un nom similaire. Par exemple, le code suivant appelle **SQLGetData** pour récupérer un tampon rempli de données; la longueur des fourre-tout est retournée à l’application dans le tampon longueur/indicateur (*ValueLenOrInd*), dont l’adresse est transmise à **SQLGetData** parce que le tampon de données correspondant (*ValuePtr*) est un tampon de sortie non différé.  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLGetData(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 À moins qu’il ne soit expressément interdit, un argument de mémoire tampon de longueur ou d’indicateur peut être 0 (si l’entrée non différée) ou un pointeur nul (si la sortie ou l’entrée différée). Pour les tampons d’entrée, cela amène le conducteur à ignorer la longueur des données. Cela renvoie une erreur lors de la transmission de données à durée variable, mais il est courant lors de l’adoption de données non nulles à durée déterminée, car ni une longueur ni une valeur d’indicateur ne sont nécessaires. Pour les tampons de sortie, cela amène le conducteur à ne pas retourner la longueur d’entrée des données ou une valeur indicateur. Il s’agit d’une erreur si les données retournées par le conducteur sont NULL, mais est fréquente lors de la récupération de données fixes et non annulables, car ni une longueur ni une valeur d’indicateur n’est nécessaire.  
  
 Comme lorsque l’adresse d’un tampon de données différée est transmise au conducteur, l’adresse d’un tampon de longueur différée/indicateur doit rester valide jusqu’à ce que le tampon ne soit pas lié.  
  
 Les longueurs suivantes sont valides en tant que valeurs de longueur/indicateur :  
  
-   *n*, où *n* > 0.  
  
-   0.  
  
-   SQL_NTS. Une chaîne envoyée au conducteur dans le tampon de données correspondant est annulée; c’est un moyen pratique pour les programmeurs C de passer les ficelles sans avoir à calculer leur longueur d’au revoir. Cette valeur n’est légale que lorsque l’application envoie des données au conducteur. Lorsque le conducteur retourne les données à l’application, il renvoie toujours la durée réelle des données.  
  
 Les valeurs suivantes sont valables sous forme de valeurs de longueur/indicateur. SQL_NULL_DATA est stockée dans le champ descripteur SQL_DESC_INDICATOR_PTR; toutes les autres valeurs sont stockées dans le champ descripteur SQL_DESC_OCTET_LENGTH_PTR.  
  
-   SQL_NULL_DATA. Les données sont une valeur de données NULL, et la valeur du tampon de données correspondant est ignorée. Cette valeur n’est légale que pour les données SQL envoyées ou récupérées au conducteur.  
  
-   SQL_DATA_AT_EXEC. Le tampon de données ne contient aucune donnée. Au lieu de cela, les données seront envoyées avec **SQLPutData** lorsque la déclaration est exécutée ou lorsque **SQLBulkOperations** ou **SQLSetPos** est appelé. Cette valeur n’est légale que pour les données SQL envoyées au conducteur. Pour plus d’informations, voir [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), et [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
-   Résultat de la SQL_LEN_DATA_AT_EXEC(*longueur)* macro. Cette valeur est similaire à SQL_DATA_AT_EXEC. Pour plus d’informations, voir [Envoyer des données longues](../../../odbc/reference/develop-app/sending-long-data.md).  
  
-   SQL_NO_TOTAL. Le conducteur ne peut pas déterminer le nombre d’octets de données longues encore disponibles pour revenir dans un tampon de sortie. Cette valeur n’est légale que pour les données SQL récupérées auprès du conducteur.  
  
-   SQL_DEFAULT_PARAM. Une procédure consiste à utiliser la valeur par défaut d’un paramètre d’entrée dans une procédure au lieu de la valeur du tampon de données correspondant.  
  
-   SQL_COLUMN_IGNORE. **SQLBulkOperations** ou **SQLSetPos** doit ignorer la valeur du tampon de données. Lors de la mise à jour d’une série de données par un appel à **SQLBulkOperations** ou **SQLSetPos,** la valeur de la colonne n’est pas modifiée. Lors de l’insertion d’une nouvelle ligne de données par un appel à **SQLBulkOperations**, la valeur de la colonne est réglée à sa valeur par défaut ou, si la colonne n’a pas de défaut, à NULL.
