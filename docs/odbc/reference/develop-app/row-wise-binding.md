---
title: Liaison Row-Wise (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: 4f622cf4-0603-47a1-a48b-944c4ef46364
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3a63565590bbafc6f3a8740dd7cf7d4acbfd4f80
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304270"
---
# <a name="row-wise-binding"></a>Liaison selon les lignes
Lors de l’utilisation de la liaison en ligne, une application définit une structure contenant une ou deux, ou dans certains cas trois, des éléments pour chaque colonne pour laquelle les données doivent être retournées. Le premier élément détient la valeur des données, et le deuxième élément détient le tampon longueur/indicateur. Les indicateurs et les valeurs de longueur peuvent être stockés dans des tampons distincts en fixant les champs SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR descripteur à des valeurs différentes; si cela est fait, la structure contient un troisième élément. L’application alloue ensuite un tableau de ces structures, qui contient autant d’éléments qu’il y a de lignes dans le ramset.  
  
 L’application déclare la taille de la structure au conducteur avec l’attribut SQL_ATTR_ROW_BIND_TYPE déclaration et lie l’adresse de chaque membre dans le premier élément du tableau. Ainsi, le conducteur peut calculer l’adresse des données pour une ligne et une colonne  
  
```  
Address = Bound Address + ((Row Number - 1) * Structure Size)  
```  
  
 où les rangées sont numérotées de 1 à la taille de l’aviron. (On est soustrait du nombre de rangées parce que l’indexation de tableau dans C est basée à zéro.) L’illustration suivante montre comment fonctionne la reliure en ligne. En général, seules les colonnes qui seront liées sont incluses dans la structure. La structure peut contenir des champs qui ne sont pas liés aux colonnes définies de résultat. Les colonnes peuvent être placées dans la structure dans n’importe quel ordre, mais sont montrées dans l’ordre séquentiel pour la clarté.  
  
 ![Affiche la ligne&#45;liaison sage](../../../odbc/reference/develop-app/media/pr22.gif "pr22")  
  
 Par exemple, le code suivant crée une structure avec des éléments dans lesquels retourner les données pour les colonnes OrderID, SalesPerson et Status, ainsi que la longueur/indicateurs pour les colonnes SalesPerson et Status. Il alloue 10 de ces structures et les lie aux colonnes OrderID, SalesPerson et Status.  
  
```  
#define ROW_ARRAY_SIZE 10  
  
// Define the ORDERINFO struct and allocate an array of 10 structs.  
typedef struct {  
   SQLUINTEGER   OrderID;  
   SQLINTEGER    OrderIDInd;  
   SQLCHAR       SalesPerson[11];  
   SQLINTEGER    SalesPersonLenOrInd;  
   SQLCHAR       Status[7];  
   SQLINTEGER    StatusLenOrInd;  
} ORDERINFO;  
ORDERINFO OrderInfoArray[ROW_ARRAY_SIZE];  
  
SQLULEN    NumRowsFetched;  
SQLUSMALLINT   RowStatusArray[ROW_ARRAY_SIZE], i;  
SQLRETURN      rc;  
SQLHSTMT       hstmt;  
  
// Specify the size of the structure with the SQL_ATTR_ROW_BIND_TYPE  
// statement attribute. This also declares that row-wise binding will  
// be used. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE  
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement  
// attribute to point to the row status array. Set the  
// SQL_ATTR_ROWS_FETCHED_PTR statement attribute to point to  
// NumRowsFetched.  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, sizeof(ORDERINFO), 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, ROW_ARRAY_SIZE, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROWS_FETCHED_PTR, &NumRowsFetched, 0);  
  
// Bind elements of the first structure in the array to the OrderID,  
// SalesPerson, and Status columns.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, &OrderInfoArray[0].OrderID, 0, &OrderInfoArray[0].OrderIDInd);  
SQLBindCol(hstmt, 2, SQL_C_CHAR, OrderInfoArray[0].SalesPerson,  
            sizeof(OrderInfoArray[0].SalesPerson),  
            &OrderInfoArray[0].SalesPersonLenOrInd);  
SQLBindCol(hstmt, 3, SQL_C_CHAR, OrderInfoArray[0].Status,  
            sizeof(OrderInfoArray[0].Status), &OrderInfoArray[0].StatusLenOrInd);  
  
// Execute a statement to retrieve rows from the Orders table.  
SQLExecDirect(hstmt, "SELECT OrderID, SalesPerson, Status FROM Orders", SQL_NTS);  
  
// Fetch up to the rowset size number of rows at a time. Print the actual  
// number of rows fetched; this number is returned in NumRowsFetched.  
// Check the row status array to print only those rows successfully  
// fetched. Code to check if rc equals SQL_SUCCESS_WITH_INFO or  
// SQL_ERRORnot shown.  
while ((rc = SQLFetchScroll(hstmt,SQL_FETCH_NEXT,0)) != SQL_NO_DATA) {  
   for (i = 0; i < NumRowsFetched; i++) {  
      if (RowStatusArray[i] == SQL_ROW_SUCCESS|| RowStatusArray[i] ==   
         SQL_ROW_SUCCESS_WITH_INFO) {  
         if (OrderInfoArray[i].OrderIDInd == SQL_NULL_DATA)  
            printf(" NULL      ");  
         else  
            printf("%d\t", OrderInfoArray[i].OrderID);  
         if (OrderInfoArray[i].SalesPersonLenOrInd == SQL_NULL_DATA)  
            printf(" NULL      ");  
         else  
            printf("%s\t", OrderInfoArray[i].SalesPerson);  
         if (OrderInfoArray[i].StatusLenOrInd == SQL_NULL_DATA)  
            printf(" NULL\n");  
         else  
            printf("%s\n", OrderInfoArray[i].Status);  
      }  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
