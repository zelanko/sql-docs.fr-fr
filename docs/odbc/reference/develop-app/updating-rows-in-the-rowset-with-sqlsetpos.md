---
title: Mise à jour des lignes dans le Rowset avec SQLSetPos (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298969"
---
# <a name="updating-rows-in-the-rowset-with-sqlsetpos"></a>Mise à jour de lignes dans l’ensemble de lignes avec SQLSetPos
L’opération de mise à jour de **SQLSetPos** rend la source de données mettre à jour une ou plusieurs lignes sélectionnées d’un tableau, en utilisant les données dans les tampons d’application pour chaque colonne liée (à moins que la valeur dans le tampon longueur/indicateur ne soit SQL_COLUMN_IGNORE). Les colonnes qui ne sont pas liées ne seront pas mises à jour.  
  
 Pour mettre à jour les lignes avec **SQLSetPos**, l’application fait ce qui suit :  
  
1.  Place les nouvelles valeurs de données dans les tampons rowset. Pour plus d’informations sur la façon d’envoyer de longues données avec **SQLSetPos**, voir [Long Data et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Définit la valeur dans le tampon longueur/indicateur de chaque colonne au besoin. Il s’agit de la longueur d’entrée des données ou SQL_NTS pour les colonnes liées aux tampons de chaîne, la longueur d’or des données pour les colonnes liées aux tampons binaires, et SQL_NULL_DATA pour toutes les colonnes à définir à NULL.  
  
3.  Définit la valeur dans le tampon longueur/indicateur des colonnes qui ne doivent pas être mises à jour pour SQL_COLUMN_IGNORE. Bien que l’application puisse sauter cette étape et renvoyer les données existantes, elle est inefficace et risque d’envoyer des valeurs à la source de données qui ont été tronquées lors de leur lecture.  
  
4.  Appels **SQLSetPos** avec *Opération* réglée à SQL_UPDATE et *RowNumber* réglé au nombre de la rangée à mettre à jour. Si *RowNumber* est 0, toutes les rangées dans le ram ensemble sont mises à jour.  
  
 Après le retour **de SQLSetPos,** la ligne actuelle est réglée sur la ligne mise à jour.  
  
 Lors de la mise à jour de toutes les lignes de l’acart *(RowNumber* est égal à 0), une application peut désactiver la mise à jour de certaines lignes en définissant les éléments correspondants du tableau d’opération de la ligne (indiqué par l’attribut de l’SQL_ATTR_ROW_OPERATION_PTR déclaration) à SQL_ROW_IGNORE. Le tableau d’opération de la ligne correspond en taille et en nombre d’éléments au tableau d’état de la ligne (indiqué par l’attribut de l’SQL_ATTR_ROW_STATUS_PTR). Pour mettre à jour uniquement les lignes dans l’ensemble de résultat qui ont été récupérés avec succès et n’ont pas été supprimés de la rangée, l’application utilise le tableau d’état de la ligne de la fonction qui a récupéré le rowset que le tableau d’opération de ligne à **SQLSetPos**.  
  
 Pour chaque ligne qui est envoyée à la source de données comme une mise à jour, les tampons d’application doivent avoir des données de ligne valides. Si les tampons d’application ont été remplis par aller chercher et si un tableau d’état de ligne a été maintenu, ses valeurs à chacune de ces positions de rangée ne devraient pas être SQL_ROW_DELETED, SQL_ROW_ERROR, ou SQL_ROW_NOROW.  
  
 Par exemple, le code suivant permet à un utilisateur de faire défiler la table des clients et de mettre à jour, supprimer ou ajouter de nouvelles lignes. Il place les nouvelles données dans les tampons rowset avant d’appeler **SQLSetPos** pour mettre à jour ou ajouter de nouvelles lignes. Une rangée supplémentaire est allouée à la fin des tampons en rangée pour contenir de nouvelles rangées; cela empêche les données existantes d’être écrasées lorsque les données d’une nouvelle rangée sont placées dans les tampons.  
  
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
