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
ms.openlocfilehash: b783c2fc6766f0e2d2685724169894160c15ffc9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68077189"
---
# <a name="allocating-and-freeing-buffers"></a>Allocation et libération de mémoires tampons
Toutes les mémoires tampons sont allouées et libérées par l’application. Si une mémoire tampon n’est pas différée, elle n’a besoin d’exister que pendant la durée de l’appel à une fonction. Par exemple, **SQLGetInfo** retourne la valeur associée à une option particulière dans la mémoire tampon vers laquelle pointe l’argument *InfoValuePtr* . Cette mémoire tampon peut être libérée immédiatement après l’appel à **SQLGetInfo**, comme illustré dans l’exemple de code suivant :  
  
```  
SQLSMALLINT   InfoValueLen;  
SQLCHAR *     InfoValuePtr = malloc(50);   // Allocate InfoValuePtr.  
  
SQLGetInfo(hdbc, SQL_DBMS_NAME, (SQLPOINTER)InfoValuePtr, 50,  
            &InfoValueLen);  
  
free(InfoValuePtr);                        // OK to free InfoValuePtr.  
```  
  
 Étant donné que les tampons différés sont spécifiés dans une fonction et utilisés dans une autre, il s’agit d’une erreur de programmation d’application pour libérer une mémoire tampon différée alors que le pilote s’attend à ce qu’elle existe encore. Par exemple, l’adresse de la \*mémoire tampon *ValuePtr* est passée à **SQLBindCol** pour une utilisation ultérieure par **SQLFetch**. Cette mémoire tampon ne peut pas être libérée tant que la colonne n’est pas détachée, par exemple avec un appel à **SQLBindCol** ou **SQLFreeStmt** comme indiqué dans l’exemple de code suivant :  
  
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
  
 Une telle erreur est facilement rendue en déclarant la mémoire tampon localement dans une fonction. la mémoire tampon est libérée lorsque l’application quitte la fonction. Par exemple, le code suivant provoque un comportement non défini et probablement fatal dans le pilote :  
  
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
