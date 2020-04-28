---
title: Utilisation des valeurs de longueur et d’indicateur | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306760"
---
# <a name="using-length-and-indicator-values"></a>Utilisation des valeurs de longueur et d’indicateur
La mémoire tampon de longueur/d’indicateur est utilisée pour transmettre la longueur d’octet des données dans la mémoire tampon de données ou un indicateur spécial, tel que SQL_NULL_DATA, qui indique que les données sont NULL. Selon la fonction dans laquelle elle est utilisée, une mémoire tampon de longueur/d’indicateur est définie pour être un SQLINTEGER destinée ou un SQLSMALLINT. Par conséquent, un seul argument est nécessaire pour le décrire. Si la mémoire tampon de données est une mémoire tampon d’entrée non différée, cet argument contient la longueur en octets des données elles-mêmes ou une valeur d’indicateur. Il est souvent nommé *StrLen_Or_Ind* ou un nom similaire. Par exemple, le code suivant appelle **SQLPutData** pour passer une mémoire tampon remplie de données ; la longueur d’octet (*ValueLen*) est passée directement, car la mémoire tampon de données (*ValuePtr*) est une mémoire tampon d’entrée.  
  
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
  
 Si la mémoire tampon de données est une mémoire tampon d’entrée différée, une mémoire tampon de sortie non différée ou une mémoire tampon de sortie, l’argument contient l’adresse de la mémoire tampon de longueur/d’indicateur. Il est souvent nommé *StrLen_or_IndPtr* ou un nom similaire. Par exemple, le code suivant appelle **SQLGetData** pour récupérer une mémoire tampon remplie de données ; la longueur d’octet est retournée à l’application dans le tampon de longueur/d’indicateur (*ValueLenOrInd*), dont l’adresse est passée à **SQLGetData** , car la mémoire tampon de données correspondante (*ValuePtr*) est une mémoire tampon de sortie non différée.  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLGetData(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 À moins qu’il ne soit spécifiquement interdit, un argument de mémoire tampon de longueur/indicateur peut avoir la valeur 0 (en entrée non différée) ou un pointeur null (en cas de sortie ou d’entrée différée). Pour les mémoires tampons d’entrée, le pilote ignore la longueur d’octet des données. Cela retourne une erreur lors du passage de données de longueur variable, mais est courant lors du passage de données non null, de longueur fixe, car aucune valeur de longueur ou d’indicateur n’est nécessaire. Pour les mémoires tampons de sortie, le pilote ne retourne pas la longueur en octets des données ou une valeur d’indicateur. Il s’agit d’une erreur si les données retournées par le pilote ont la valeur NULL, mais est courante lors de la récupération de données de longueur fixe non Nullable, car aucune valeur de longueur ou d’indicateur n’est nécessaire.  
  
 Comme lorsque l’adresse d’un tampon de données différé est passée au pilote, l’adresse d’une mémoire tampon de longueur/d’indicateur différée doit rester valide jusqu’à ce que la mémoire tampon soit détachée.  
  
 Les longueurs suivantes sont valides en tant que valeurs de longueur/indicateur :  
  
-   *n*, où *n* > 0.  
  
-   0.  
  
-   SQL_NTS. Une chaîne envoyée au pilote dans le tampon de données correspondant est terminée par un caractère null ; C’est un moyen pratique pour les programmeurs C de passer des chaînes sans avoir à calculer leur longueur d’octet. Cette valeur est légale uniquement lorsque l’application envoie des données au pilote. Lorsque le pilote retourne des données à l’application, il retourne toujours la longueur d’octet réelle des données.  
  
 Les valeurs suivantes sont valides en tant que valeurs de longueur/indicateur. SQL_NULL_DATA est stocké dans le champ de descripteur de SQL_DESC_INDICATOR_PTR ; toutes les autres valeurs sont stockées dans le champ descripteur SQL_DESC_OCTET_LENGTH_PTR.  
  
-   SQL_NULL_DATA. Les données sont une valeur de données NULL, et la valeur dans le tampon de données correspondant est ignorée. Cette valeur est légale uniquement pour les données SQL envoyées ou récupérées à partir du pilote.  
  
-   SQL_DATA_AT_EXEC. La mémoire tampon de données ne contient aucune donnée. Au lieu de cela, les données sont envoyées avec **SQLPutData** lors de l’exécution de l’instruction ou lors de l’appel de **SQLBulkOperations** ou **SQLSetPos** . Cette valeur est légale uniquement pour les données SQL envoyées au pilote. Pour plus d’informations, consultez [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)et [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
-   Résultat de la macro SQL_LEN_DATA_AT_EXEC (*longueur*). Cette valeur est similaire à SQL_DATA_AT_EXEC. Pour plus d’informations, consultez [envoi de données de type long](../../../odbc/reference/develop-app/sending-long-data.md).  
  
-   SQL_NO_TOTAL. Le pilote ne peut pas déterminer le nombre d’octets de données longues encore disponibles pour le retour dans une mémoire tampon de sortie. Cette valeur est légale uniquement pour les données SQL récupérées à partir du pilote.  
  
-   SQL_DEFAULT_PARAM. Une procédure consiste à utiliser la valeur par défaut d’un paramètre d’entrée dans une procédure au lieu de la valeur dans la mémoire tampon de données correspondante.  
  
-   SQL_COLUMN_IGNORE. **SQLBulkOperations** ou **SQLSetPos** est d’ignorer la valeur dans la mémoire tampon de données. Lors de la mise à jour d’une ligne de données par un appel à **SQLBulkOperations** ou **SQLSetPos,** la valeur de la colonne n’est pas modifiée. Lors de l’insertion d’une nouvelle ligne de données par un appel à **SQLBulkOperations**, la valeur de la colonne est définie sur sa valeur par défaut ou, si la colonne n’a pas de valeur par défaut, la valeur null.
