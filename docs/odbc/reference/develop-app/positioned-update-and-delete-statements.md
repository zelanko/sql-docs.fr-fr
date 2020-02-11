---
title: Instructions Update et DELETE positionnées | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5b37bdfae5f97a453477768aca39b801c06c0701
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68023292"
---
# <a name="positioned-update-and-delete-statements"></a>Instructions de mise à jour et de suppression positionnées
Les applications peuvent mettre à jour ou supprimer la ligne actuelle dans un jeu de résultats avec une instruction UPDATE ou DELETE positionnée. Les instructions Update et DELETE positionnées sont prises en charge par certaines sources de données, mais pas toutes. Pour déterminer si une source de données prend en charge les instructions Update et DELETE positionnées, une application appelle **SQLGetInfo** avec le SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 ou SQL_STATIC_CURSOR_ATTRIBUTES1 *infotype* (selon le type du curseur). Notez que la bibliothèque de curseurs ODBC simule les instructions Update et DELETE positionnées.  
  
 Pour utiliser une instruction UPDATE ou DELETE positionnée, l’application doit créer un jeu de résultats avec une instruction **Select for Update** . La syntaxe de cette instruction est la suivante :  
  
 **Select** [**All** &#124; **distinct**] *Select-List*  
  
 **À partir de** *table-reference-list*  
  
 [**Where** *recherche-condition*]  
  
 **Pour la mise à jour de** [*nom-* colonne [**,** *colonne-nom*]...]  
  
 L’application positionne ensuite le curseur sur la ligne à mettre à jour ou à supprimer. Pour ce faire, il peut appeler **SQLFetchScroll** pour extraire un ensemble de lignes contenant la ligne requise et appeler **SQLSetPos** pour positionner le curseur de l’ensemble de lignes sur cette ligne. L’application exécute ensuite l’instruction UPDATE ou DELETE positionnée sur une instruction différente de l’instruction utilisée par le jeu de résultats. La syntaxe de ces instructions est la suivante :  
  
 **Mettre à jour** *le nom de la table*  
  
 **Set** *Column-identifier* **=** {*expression* &#124; **null**}  
  
 [**,** *identificateur de colonne* **=** {*expression* &#124; **null**}]...  
  
 **Où Current de** *Cursor-Name*  
  
 **Supprimer de** la *table-nom* **où Current de** *Cursor-Name*  
  
 Notez que ces instructions requièrent un nom de curseur. L’application peut spécifier un nom de curseur avec **SQLSetCursorName** avant d’exécuter l’instruction qui crée le jeu de résultats ou peut permettre à la source de données de générer automatiquement un nom de curseur lors de la création du curseur. Dans ce dernier cas, l’application récupère ce nom de curseur pour une utilisation dans les instructions Update et DELETE positionnées en appelant **SQLGetCursorName**.  
  
 Par exemple, le code suivant permet à un utilisateur de faire défiler la table Customers et de supprimer des enregistrements de clients ou de mettre à jour leurs adresses et numéros de téléphone. Elle appelle **SQLSetCursorName** pour spécifier un nom de curseur avant de créer le jeu de résultats des clients et utilise trois descripteurs d’instruction : *hstmtCust* pour le jeu de résultats, *hstmtUpdate* pour une instruction Update positionnée et *hstmtDelete* pour une instruction DELETE positionnée. Bien que le code puisse lier des variables distinctes aux paramètres dans l’instruction de mise à jour positionnée, il met à jour les mémoires tampons d’ensemble de lignes et lie les éléments de ces mémoires tampons. Cela permet de maintenir la synchronisation des mémoires tampons d’ensemble de lignes avec les données mises à jour.  
  
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
