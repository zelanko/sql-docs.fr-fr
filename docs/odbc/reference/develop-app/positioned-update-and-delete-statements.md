---
title: Mises à jour et suppressions d’instructions positionnées . Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- data updates [ODBC], positioned update or delete
- positioned updates [ODBC]
- updating data [ODBC], positioned update or delete
ms.assetid: 0eafba50-02c7-46ca-a439-ef3307b935dc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6e5316bee7057b30eace326b3ca82b30b75741fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282360"
---
# <a name="positioned-update-and-delete-statements"></a>Instructions de mise à jour et de suppression positionnées
Les applications peuvent mettre à jour ou supprimer la ligne actuelle dans un ensemble de résultats avec une mise à jour positionnée ou supprimer l’instruction. Les instructions de mise à jour et de suppression positionnées sont prises en charge par certaines sources de données, mais pas toutes. Pour déterminer si une source de données prend en charge la mise à jour et la suppression des relevés positionnés, une application appelle **SQLGetInfo** avec le SQL_DYNAMIC_CURSOR_ATTRIBUTES1, la SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, la SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 *InfoType* (selon le type de curseur). Notez que la bibliothèque de curseurs ODBC simule la mise à jour positionnée et supprime les instructions.  
  
 Pour utiliser une mise à jour ou une déclaration de suppression positionnée, l’application doit créer un ensemble de résultats avec une déclaration **SELECT FOR UPDATE.** La syntaxe de cette déclaration est la suivante:  
  
 **SELECT** [**ALL** &#124; **DISTINCT**] *select-list*  
  
 **DE** *table-référence-liste*  
  
 [**Où** *la recherche-condition*]  
  
 **POUR UPDATE OF** [*nom de colonne* **[,** *nom de colonne*]...]  
  
 L’application positionne ensuite le curseur sur la ligne pour être mis à jour ou supprimé. Il peut le faire en appelant **SQLFetchScroll** pour récupérer un aviron contenant la rangée requise et en appelant **SQLSetPos** pour positionner le curseur encastré sur cette rangée. L’application exécute ensuite la mise à jour positionnée ou supprime l’instruction sur une déclaration différente de celle utilisée par l’ensemble de résultats. La syntaxe de ces énoncés est la suivante :  
  
 **NOM** *de table* UPDATE  
  
 **SET** *colonne-identificateur* **=** -*expression* &#124; **NULL**'  
  
 [,**,** *colonne-identifiant* **=** -*expression* &#124; **NULL]...**  
  
 **Où CURRENT OF** *cursor-name*  
  
 **DELETE FROM** *table-name* **WHERE CURRENT OF** *cursor-name*  
  
 Notez que ces déclarations nécessitent un nom de curseur. L’application peut spécifier un nom de curseur avec **SQLSetCursorName** avant d’exécuter l’instruction qui crée l’ensemble de résultats ou peut laisser la source de données générer automatiquement un nom de curseur lorsque le curseur est créé. Dans ce dernier cas, l’application récupère ce nom de curseur pour une utilisation dans la mise à jour positionnée et supprime les déclarations en appelant **SQLGetCursorName**.  
  
 Par exemple, le code suivant permet à un utilisateur de faire défiler la table des clients et de supprimer les enregistrements des clients ou de mettre à jour leurs adresses et numéros de téléphone. Il appelle **SQLSetCursorName** pour spécifier un nom curseur avant de créer l’ensemble de résultats des clients et utilise trois poignées de déclaration: *hstmtCust* pour l’ensemble de résultat, *hstmtUpdate* pour une instruction de mise à jour *positionnée, et hstmtDelete* pour une déclaration de suppression positionnée. Bien que le code puisse lier des variables distinctes aux paramètres de l’énoncé de mise à jour positionné, il met à jour les tampons encastrés et lie les éléments de ces tampons. Cela permet de garder les tampons encastrés synchronisés avec les données mises à jour.  
  
```  
#define POSITIONED_UPDATE 100  
#define POSITIONED_DELETE 101  
  
SQLUINTEGER    CustIDArray[10];  
SQLCHAR        NameArray[10][51], AddressArray[10][51],   
               PhoneArray[10][11];  
SQLINTEGER     CustIDIndArray[10], NameLenOrIndArray[10],   
               AddressLenOrIndArray[10],  
               PhoneLenOrIndArray[10];  
SQLUSMALLINT   RowStatusArray[10], Action, RowNum;  
SQLHSTMT       hstmtCust, hstmtUpdate, hstmtDelete;  
  
// Set the SQL_ATTR_BIND_TYPE statement attribute to use column-wise   
// binding. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE   
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement   
// attribute to point to the row status array.  
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);  
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_ARRAY_SIZE, 10, 0);  
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
  
// Bind arrays to the CustID, Name, Address, and Phone columns.  
SQLBindCol(hstmtCust, 1, SQL_C_ULONG, CustIDArray, 0, CustIDIndArray);  
SQLBindCol(hstmtCust, 2, SQL_C_CHAR, NameArray, sizeof(NameArray[0]),  
            NameLenOrIndArray);  
SQLBindCol(hstmtCust, 3, SQL_C_CHAR, AddressArray, sizeof(AddressArray[0]),  
         AddressLenOrIndArray);  
SQLBindCol(hstmtCust, 4, SQL_C_CHAR, PhoneArray, sizeof(PhoneArray[0]),  
            PhoneLenOrIndArray);  
  
// Set the cursor name to Cust.  
SQLSetCursorName(hstmtCust, "Cust", SQL_NTS);  
  
// Prepare positioned update and delete statements.  
SQLPrepare(hstmtUpdate,  
   "UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust",  
   SQL_NTS);  
SQLPrepare(hstmtDelete, "DELETE FROM Customers WHERE CURRENT OF Cust", SQL_NTS);  
  
// Execute a statement to retrieve rows from the Customers table.  
SQLExecDirect(hstmtCust,  
   "SELECT CustID, Name, Address, Phone FROM Customers FOR UPDATE OF Address, Phone",  
   SQL_NTS);  
  
// Fetch and display the first 10 rows.  
SQLFetchScroll(hstmtCust, SQL_FETCH_NEXT, 0);  
DisplayData(CustIDArray, CustIDIndArray, NameArray, NameLenOrIndArray, AddressArray,  
            AddressLenOrIndArray, PhoneArray, PhoneLenOrIndArray, RowStatusArray);  
  
// Call GetAction to get an action and a row number from the user.  
while (GetAction(&Action, &RowNum)) {  
   switch (Action) {  
  
      case SQL_FETCH_NEXT:  
      case SQL_FETCH_PRIOR:  
      case SQL_FETCH_FIRST:  
      case SQL_FETCH_LAST:  
      case SQL_FETCH_ABSOLUTE:  
      case SQL_FETCH_RELATIVE:  
         // Fetch and display the requested data.  
         SQLFetchScroll(hstmtCust, Action, RowNum);  
         DisplayData(CustIDArray, CustIDIndArray, NameArray, NameLenOrIndArray,  
                     AddressArray, AddressLenOrIndArray, PhoneArray,  
                     PhoneLenOrIndArray, RowStatusArray);  
         break;  
  
      case POSITIONED_UPDATE:  
         // Get the new data and place it in the rowset buffers.  
         GetNewData(AddressArray[RowNum - 1], &AddressLenOrIndArray[RowNum - 1],  
                     PhoneArray[RowNum - 1], &PhoneLenOrIndArray[RowNum - 1]);  
  
         // Bind the elements of the arrays at position RowNum-1 to the   
         // parameters of the positioned update statement.  
         SQLBindParameter(hstmtUpdate, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                           50, 0, AddressArray[RowNum - 1], sizeof(AddressArray[0]),  
                           &AddressLenOrIndArray[RowNum - 1]);  
         SQLBindParameter(hstmtUpdate, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                           10, 0, PhoneArray[RowNum - 1], sizeof(PhoneArray[0]),  
                           &PhoneLenOrIndArray[RowNum - 1]);  
  
         // Position the rowset cursor. The rowset is 1-based.  
         SQLSetPos(hstmtCust, RowNum, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
  
         // Execute the positioned update statement to update the row.  
         SQLExecute(hstmtUpdate);  
         break;  
  
      case POSITIONED_DELETE:  
         // Position the rowset cursor. The rowset is 1-based.  
         SQLSetPos(hstmtCust, RowNum, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
  
         // Execute the positioned delete statement to delete the row.  
         SQLExecute(hstmtDelete);  
         break;  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmtCust);  
```
