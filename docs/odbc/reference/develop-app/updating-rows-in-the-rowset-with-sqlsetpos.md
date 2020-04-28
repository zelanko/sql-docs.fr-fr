---
title: Mise à jour de lignes dans l’ensemble de lignes avec SQLSetPos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating rows
ms.assetid: d83a8c2a-5aa8-4f19-947c-79a817167ee1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4851d4ba741379fc188b2b88c895a378ef3bb80d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298969"
---
# <a name="updating-rows-in-the-rowset-with-sqlsetpos"></a>Mise à jour de lignes dans l’ensemble de lignes avec SQLSetPos
L’opération de mise à jour de **SQLSetPos** permet à la source de données de mettre à jour une ou plusieurs lignes sélectionnées d’une table, à l’aide des données des mémoires tampons de l’application pour chaque colonne liée (sauf si la valeur de la mémoire tampon de longueur/indicateur est SQL_COLUMN_IGNORE). Les colonnes qui ne sont pas liées ne seront pas mises à jour.  
  
 Pour mettre à jour des lignes avec **SQLSetPos**, l’application effectue les opérations suivantes :  
  
1.  Place les nouvelles valeurs de données dans les mémoires tampons de l’ensemble de lignes. Pour plus d’informations sur l’envoi de données de type long avec **SQLSetPos**, consultez [long Data et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Définit la valeur de la mémoire tampon de longueur/d’indicateur de chaque colonne si nécessaire. Il s’agit de la longueur en octets des données ou SQL_NTS pour les colonnes liées aux mémoires tampons de chaîne, la longueur en octets des données pour les colonnes liées aux mémoires tampons binaires, et SQL_NULL_DATA pour toutes les colonnes dont la valeur est NULL.  
  
3.  Définit la valeur dans la mémoire tampon de longueur/d’indicateur des colonnes qui ne doivent pas être mises à jour pour SQL_COLUMN_IGNORE. Bien que l’application puisse ignorer cette étape et renvoyer les données existantes, cela est inefficace et risque d’envoyer des valeurs à la source de données qui ont été tronquées lors de leur lecture.  
  
4.  Appelle **SQLSetPos** avec l' *opération* définie sur SQL_UPDATE et *RowNumber* défini sur le numéro de la ligne à mettre à jour. Si *RowNumber* a la valeur 0, toutes les lignes de l’ensemble de lignes sont mises à jour.  
  
 Une fois **SQLSetPos** retourné, la ligne actuelle est définie sur la ligne mise à jour.  
  
 Lors de la mise à jour de toutes les lignes de l’ensemble de lignes (*NombLigne* est égal à 0), une application peut désactiver la mise à jour de certaines lignes en définissant les éléments correspondants du tableau d’opérations de ligne (vers lequel pointe l’attribut d’instruction SQL_ATTR_ROW_OPERATION_PTR) pour SQL_ROW_IGNORE. Le tableau d’opérations de ligne correspond à la taille et au nombre d’éléments du tableau d’état de ligne (pointé par l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR). Pour mettre à jour uniquement les lignes du jeu de résultats qui ont été récupérées avec succès et qui n’ont pas été supprimées de l’ensemble de lignes, l’application utilise le tableau d’état de ligne de la fonction qui a extrait l’ensemble de lignes en tant que tableau d’opérations de ligne en **SQLSetPos**.  
  
 Pour chaque ligne envoyée à la source de données sous forme de mise à jour, les mémoires tampons de l’application doivent avoir des données de ligne valides. Si les mémoires tampons de l’application ont été remplies par l’extraction et si un tableau d’état de ligne a été conservé, ses valeurs à chacune de ces positions de ligne ne doivent pas être SQL_ROW_DELETED, SQL_ROW_ERROR ou SQL_ROW_NOROW.  
  
 Par exemple, le code suivant permet à un utilisateur de faire défiler la table Customers et de mettre à jour, supprimer ou ajouter de nouvelles lignes. Il place les nouvelles données dans les mémoires tampons de l’ensemble de lignes avant d’appeler **SQLSetPos** pour mettre à jour ou ajouter de nouvelles lignes. Une ligne supplémentaire est allouée à la fin des mémoires tampons de l’ensemble de lignes pour contenir les nouvelles lignes ; Cela empêche le remplacement des données existantes lorsque les données d’une nouvelle ligne sont placées dans les mémoires tampons.  
  
```  
#define UPDATE_ROW   100  
#define DELETE_ROW   101  
#define ADD_ROW      102  
  
SQLUINTEGER    CustIDArray[11];  
SQLCHAR        NameArray[11][51], AddressArray[11][51],   
               PhoneArray[11][11];  
SQLINTEGER     CustIDIndArray[11], NameLenOrIndArray[11],   
               AddressLenOrIndArray[11],  
               PhoneLenOrIndArray[11];  
SQLUSMALLINT   RowStatusArray[10], Action, RowNum;  
SQLRETURN      rc;  
SQLHSTMT       hstmt;  
  
// Set the SQL_ATTR_ROW_BIND_TYPE statement attribute to use column-wise   
// binding. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE   
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement   
// attribute to point to the row status array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_KEYSET_DRIVEN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 10, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
  
// Bind arrays to the CustID, Name, Address, and Phone columns.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, CustIDArray, 0, CustIDIndArray);  
SQLBindCol(hstmt, 2, SQL_C_CHAR, NameArray, sizeof(NameArray[0]), NameLenOrIndArray);  
SQLBindCol(hstmt, 3, SQL_C_CHAR, AddressArray, sizeof(AddressArray[0]),  
            AddressLenOrIndArray);  
SQLBindCol(hstmt, 4, SQL_C_CHAR, PhoneArray, sizeof(PhoneArray[0]),  
            PhoneLenOrIndArray);  
  
// Execute a statement to retrieve rows from the Customers table.  
SQLExecDirect(hstmt, "SELECT CustID, Name, Address, Phone FROM Customers", SQL_NTS);  
  
// Fetch and display the first 10 rows.  
rc = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
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
         SQLFetchScroll(hstmt, Action, RowNum);  
         DisplayData(CustIDArray, CustIDIndArray,  
                     NameArray, NameLenOrIndArray,  
                     AddressArray, AddressLenOrIndArray,  
                     PhoneArray, PhoneLenOrIndArray, RowStatusArray);  
         break;  
  
      case UPDATE_ROW:  
         // Place the new data in the rowset buffers and update the   
         // specified row.  
         GetNewData(&CustIDArray[RowNum - 1], &CustIDIndArray[RowNum - 1],  
                  NameArray[RowNum - 1], &NameLenOrIndArray[RowNum - 1],  
                  AddressArray[RowNum - 1], &AddressLenOrIndArray[RowNum - 1],  
                  PhoneArray[RowNum - 1], &PhoneLenOrIndArray[RowNum - 1]);  
         SQLSetPos(hstmt, RowNum, SQL_UPDATE, SQL_LOCK_NO_CHANGE);  
         break;  
  
      case DELETE_ROW:  
         // Delete the specified row.  
         SQLSetPos(hstmt, RowNum, SQL_DELETE, SQL_LOCK_NO_CHANGE);  
         break;  
  
      case ADD_ROW:  
         // Place the new data in the rowset buffers at index 10.   
         // This is an extra element for new rows so rowset data is   
         // not overwritten. Insert the new row. Row 11 corresponds   
         // to index 10.  
         GetNewData(&CustIDArray[10], &CustIDIndArray[10],  
                     NameArray[10], &NameLenOrIndArray[10],  
                     AddressArray[10], &AddressLenOrIndArray[10],  
                     PhoneArray[10], &PhoneLenOrIndArray[10]);  
         SQLSetPos(hstmt, 11, SQL_ADD, SQL_LOCK_NO_CHANGE);  
         break;  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
