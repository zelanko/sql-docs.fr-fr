---
title: Allouer et libérer les tampons (en anglais seulement) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6aab888d24fcbc987b3db921436f14812618519
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288399"
---
# <a name="allocating-and-freeing-buffers"></a>Allocation et libération de mémoires tampons
Tous les tampons sont attribués et libérés par l’application. Si un tampon n’est pas reporté, il n’a besoin d’exister que pour la durée de l’appel à une fonction. Par exemple, **SQLGetInfo** retourne la valeur associée à une option particulière dans le tampon pointé par l’argument *InfoValuePtr.* Ce tampon peut être libéré immédiatement après l’appel à **SQLGetInfo**, comme indiqué dans l’exemple de code suivant :  
  
```  
SQLSMALLINT   InfoValueLen;  
SQLCHAR *     InfoValuePtr = malloc(50);   // Allocate InfoValuePtr.  
  
SQLGetInfo(hdbc, SQL_DBMS_NAME, (SQLPOINTER)InfoValuePtr, 50,  
            &InfoValueLen);  
  
free(InfoValuePtr);                        // OK to free InfoValuePtr.  
```  
  
 Étant donné que les tampons différés sont spécifiés dans une fonction et utilisés dans une autre, il s’agit d’une erreur de programmation d’application pour libérer un tampon différé pendant que le conducteur s’attend toujours à ce qu’il existe. Par \*exemple, l’adresse du tampon *ValuePtr* est transmise à **SQLBindCol** pour une utilisation ultérieure par **SQLFetch**. Ce tampon ne peut pas être libéré tant que la colonne n’est pas liée, par exemple avec un appel à **SQLBindCol** ou **SQLFreeStmt** comme indiqué dans l’exemple de code suivant :  
  
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
  
 Une telle erreur est facilement faite en déclarant le tampon localement dans une fonction; le tampon est libéré lorsque l’application quitte la fonction. Par exemple, le code suivant provoque un comportement indéfini et probablement mortel chez le conducteur :  
  
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
