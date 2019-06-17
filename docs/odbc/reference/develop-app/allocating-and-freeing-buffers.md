---
title: Allocation et libération de mémoires tampons | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- buffers [ODBC], allocating and freeing
- allocating buffers [ODBC]
- freeing buffers [ODBC]
ms.assetid: 886bc9ed-39d4-43d2-82ff-aebc35b14d39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 388147de8935d36180ba9845c8353bbf3dd6edc0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63288083"
---
# <a name="allocating-and-freeing-buffers"></a>Allocation et libération de mémoires tampons
Toutes les mémoires tampons sont allouées et libérées par l’application. Si une mémoire tampon n’est pas différée, il doit exister uniquement pendant la durée de l’appel à une fonction. Par exemple, **SQLGetInfo** retourne la valeur associée à une option spécifique dans la mémoire tampon vers laquelle pointée le *InfoValuePtr* argument. Cette mémoire tampon peut être libéré immédiatement après l’appel à **SQLGetInfo**, comme illustré dans l’exemple de code suivant :  
  
```  
SQLSMALLINT   InfoValueLen;  
SQLCHAR *     InfoValuePtr = malloc(50);   // Allocate InfoValuePtr.  
  
SQLGetInfo(hdbc, SQL_DBMS_NAME, (SQLPOINTER)InfoValuePtr, 50,  
            &InfoValueLen);  
  
free(InfoValuePtr);                        // OK to free InfoValuePtr.  
```  
  
 Étant donné que les mémoires tampons différées sont spécifiés dans une fonction et utilisés dans un autre, il est une erreur de programmation d’application pour libérer une mémoire tampon différée, tandis que le pilote attend toujours qu’elle existe. Par exemple, l’adresse de la \* *ValuePtr* mémoire tampon est transmise à **SQLBindCol** pour une utilisation ultérieure par **SQLFetch**. Cette mémoire tampon ne peut pas être libéré tant que la colonne est détachée, comme avec un appel à **SQLBindCol** ou **SQLFreeStmt** comme indiqué dans l’exemple de code suivant :  
  
```  
SQLRETURN    rc;  
SQLINTEGER   ValueLenOrInd;  
SQLHSTMT     hstmt;  
  
// Allocate ValuePtr  
SQLCHAR * ValuePtr = malloc(50);  
  
// Bind ValuePtr to column 1. It is an error to free ValuePtr here.  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, 50, &ValueLenOrInd);  
  
// Fetch each row of data and place the value for column 1 in *ValuePtr.  
// Code to check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO   
// not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   // It is an error to free ValuePtr here.  
}  
  
// Unbind ValuePtr from column 1.  It is now OK to free ValuePtr.  
SQLFreeStmt(hstmt, SQL_UNBIND);  
free(ValuePtr);  
```  
  
 Une telle erreur est facilement effectuée en déclarant de la mémoire tampon localement dans une fonction ; la mémoire tampon est libérée lorsque l’application quitte la fonction. Par exemple, le code suivant provoque un comportement non défini et probablement irrécupérable dans le pilote :  
  
```  
SQLRETURN   rc;  
SQLHSTMT    hstmt;  
  
BindAColumn(hstmt);  
  
// Fetch each row of data and try to place the value for column 1 in  
// *ValuePtr. Because ValuePtr has been freed, the behavior is undefined  
// and probably fatal. Code to check if rc equals SQL_ERROR or   
// SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {}  
  
   .  
   .  
   .  
  
void BindAColumn(SQLHSTMT hstmt)  // WARNING! This function won't work!  
{  
   // Declare ValuePtr locally.  
   SQLCHAR      ValuePtr[50];  
   SQLINTEGER   ValueLenOrInd;  
  
   // Bind rgbValue to column.  
   SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr),  
               &ValueLenOrInd);  
  
   // ValuePtr is freed when BindAColumn exits.  
}  
```
