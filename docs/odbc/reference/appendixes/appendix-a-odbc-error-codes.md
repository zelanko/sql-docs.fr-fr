---
title: 'Annexe A : Codes d’erreur ODBC (fr) Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error codes [ODBC]
- SQLSTATE [ODBC]
- error codes [ODBC], SQLSTATE
ms.assetid: c06902e4-721d-42e2-b818-05f0e18e4ce0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af288cf9f0564f6fe0dbef14f66143667120c656
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307520"
---
# <a name="appendix-a-odbc-error-codes"></a>Annexe A : Codes d’erreur ODBC
Ce sujet traite des valeurs SQLSTATE pour ODBC 3. *x*. Pour plus d’informations sur ODBC 3. *x* Valeurs SQLSTATE, voir [SQLSTATE Mappings](../../../odbc/reference/develop-app/sqlstate-mappings.md).  
  
 **SQLGetDiagRec** ou **SQLGetDiagField** retourne les valeurs SQLSTATE telles que définies par Open Group *Data Management: Structured Query Language (SQL), Version 2* (mars 1995). Les valeurs SQLSTATE sont des chaînes qui contiennent cinq caractères. Le tableau suivant énumère les valeurs SQLSTATE qu’un conducteur peut revenir pour **SQLGetDiagRec**.  
  
 La valeur de la chaîne de caractère retournée pour un SQLSTATE se compose d’une valeur de classe à deux caractères suivie d’une valeur de sous-classe à trois caractères. Une valeur de classe de "01" indique un avertissement et est accompagnée d’un code de retour de SQL_SUCCESS_WITH_INFO. Les valeurs de classe autres que « 01 », à l’exception de la classe « IM », indiquent une erreur et sont accompagnées d’une valeur de retour de SQL_ERROR. La classe "IM" est spécifique aux avertissements et erreurs qui découlent de la mise en œuvre de l’ODBC elle-même. La valeur de sous-classe "000" dans n’importe quelle catégorie indique qu’il n’y a pas de sous-classe pour ce SQLSTATE. L’attribution des valeurs de classe et de sous-classe est définie par SQL-92.  
  
> [!NOTE]  
>  Bien que l’exécution réussie d’une fonction soit normalement indiquée par une valeur de retour de SQL_SUCCESS, le SQLSTATE 00000 indique également le succès.  
  
|SQLSTATE|Error|Peut être retourné de|  
|--------------|-----------|--------------------------|  
|01000|Avertissement général|Toutes les fonctions ODBC sauf :<br /><br /> **Sqlerror**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|01001|Conflit d’opération cursor|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|01002|Erreur de déconnexion|**SQLDisconnect**|  
|01003|Valeur NULL éliminée dans la fonction définie|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01004|Données sur les cordes, à droite tronquées|**SQLBrowseConnect**<br /><br /> **SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLColAttribute**<br /><br /> **SQLDataSources**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLNative (SQLNative)**<br /><br /> **Sql SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetCursorName**|  
|01006|Privilège non révoqué|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01007|Privilège non accordé|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|01S00|Attribut de chaîne de connexion invalide|**SQLBrowseConnect**<br /><br /> **SQLDriverConnec (SQLDriverConnec)**|  
|01S01|Erreur dans la rangée|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLSetPos**|  
|01S02|Valeur de l’option modifiée|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|01S06|Tentative d’aller chercher avant le jeu de résultat retourné le premier rowset|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|01S07|Troncation fractionnaire|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|01S08|Fichier d’enregistrement d’erreur DSN|**SQLDriverConnect**|  
|01S09|Mot-clé invalide|**SQLDriverConnect**|  
|07001|Mauvais nombre de paramètres|**SQLExecDirect**<br /><br /> **SQLExecute**|  
|07002|LE champ COUNT incorrect|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**|  
|07005|Déclaration préparée et non *une spécification curseur*|**SQLColAttribute**<br /><br /> **SQLDescribeCol**|  
|07006|Violation restreinte d’attribut de type de données|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|07009|Indice descripteur invalide|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLColAttribute**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRecSQLSetPos**|  
|07S01|Utilisation invalide du paramètre par défaut|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**|  
|08001|Client incapable d’établir la connexion|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08002|Nom de connexion en cours d’utilisation|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|08003|Connexion non ouverte|**SQLAllocHandle**<br /><br /> **SQLDisconnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLSetConnectAttr**|  
|08004|Server a rejeté la connexion|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|08007|Défaillance de connexion pendant la transaction|**SQLEndTran**|  
|08S01|Défaillance du lien de communication|**SQLBrowseConnect**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLCopyDesc (SQLCopyDesc)**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNativeSql**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|21S01|La liste de valeur d’insertion ne correspond pas à la liste de colonnes|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|21S02|Le degré de tableau dérivé ne correspond pas à la liste des colonnes|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetPos**|  
|22001|Données sur les cordes, à droite tronquées|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetPos**|  
|22002|Variable d’indicateur requise mais non fournie|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**|  
|22003|Valeur numérique hors de portée|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLGetInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22007|Format de date invalide|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22008|Débordement de champ datetime|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExecDirect**<br /><br /> **QLParamData**<br /><br /> **SQLPutData**|  
|22012|Division par zéro|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLPutData**|  
|22015|Débordement de champ d’intervalle|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22018|Valeur de caractère invalide pour la spécification de la distribution|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**<br /><br /> **SQLParamData**<br /><br /> **SQLPutData**<br /><br /> **SQLSetPos**|  
|22019|Caractère d’évasion invalide|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22025|Séquence d’évasion invalide|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|22026|Chaîne de données ou longueur non correspondante|**SQLParamData**|  
|23000|Violation de la contrainte d’intégrité|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|24 000|État de curseur non valide|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|25000|État de transaction non valide|**SQLDisconnect**|  
|25S01|État des transactions|**SQLEndTran**|  
|25S02|La transaction est toujours active|**SQLEndTran**|  
|25S03|La transaction est annulée|**SQLEndTran**|  
|28000|Spécifications d’autorisation invalides|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|34000|Nom de curseur non valide|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetCursorName**|  
|3C000|Nom du curseur en double|**SQLSetCursorName**|  
|3D000|Nom du catalogue invalide|**SQLExecDirect**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetConnectAttr**|  
|3F000|Nom de schéma invalide|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|40001|Échec de la sérialisation|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLParamData**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|40002|Violation de la contrainte d’intégrité|**SQLEndTran**|  
|40003|Achèvement de l’énoncé inconnu|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|42000|Erreur de syntaxe ou violation d’accès|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLSetPos**|  
|42S01|La table de base ou la vue existe déjà|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S02|Table de base ou vue non trouvée|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S11|L’indice existe déjà|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S12|Index non trouvé|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S21|Colonne existe déjà|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|42S22|Colonne non trouvée|**SQLExecDirect**<br /><br /> **SQLPrepare**|  
|44000|Violation de WITH CHECK OPTION|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|HY000|Erreur générale|Toutes les fonctions ODBC sauf :<br /><br /> **Sqlerror**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Toutes les fonctions ODBC sauf :<br /><br /> **Sqlerror**<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY003 (HY003)|Type tampon d’application invalide|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLGetData**|  
|HY004|Type de données SQL invalide|**SQLBindParameter**<br /><br /> **SQLGetTypeInfo**|  
|HY007|Déclaration associée n’est pas préparée|**SQLCopyDesc (SQLCopyDesc)**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**|  
|HY008 HY008|Opération annulée|Toutes les fonctions ODBC qui peuvent être traitées asynchronement:<br /><br /> **SQLBrowseConnect**<br /><br /> **SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDisconnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetData**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY009|Utilisation invalide du pointeur nul|**SQLAllocHandle**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLExecDirect**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLNativeSql**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY010|Erreur de séquence de fonction|**SQLAllocHandle**<br /><br /> **SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLCloseCursor**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLCopyDesc (SQLCopyDesc)**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDescribeParam**<br /><br /> **SQLDisconnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetDescRec**<br /><br /> **SQLGetFunctions**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLMoreResults**<br /><br /> **SQLNumParams**<br /><br /> **SQLNumResultCols**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLRowCount**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY011 HY011|L’attribut ne peut pas être défini maintenant|**SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLParamData**<br /><br /> **QLSetPos**<br /><br /> **SQLSetStmtAttr**|  
|HY012|Code d’opération de transaction invalide|**SQLEndTran**|  
|HY013|Erreur de gestion de la mémoire|Toutes les fonctions ODBC sauf :<br /><br /> **SQLGetDiagField**<br /><br /> **SQLGetDiagRec**|  
|HY014|Limite sur le nombre de poignées dépassées|**SQLAllocHandle**|  
|HY015|Aucun nom de curseur disponible|**SQLGetCursorName**|  
|HY016|Impossible de modifier un descripteur de ligne de mise en œuvre|**SQLCopyDesc (SQLCopyDesc)**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY017|Utilisation invalide d’une poignée descripteur automatiquement allouée|**SQLFreeHandle**<br /><br /> **SQLSetStmtAttr**|  
|HY018 HY018|Serveur a refusé la demande d’annulation|**SQLCancel**|  
|HY019|Données non-caractère et non binaires envoyées en morceaux|**SQLPutData**|  
|HY020|Tentative de concatenate d’une valeur nulle|**SQLPutData**|  
|HY021|Informations descripteur incohérentes|**SQLBindParameter**<br /><br /> **SQLCopyDesc (SQLCopyDesc)**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**|  
|HY024|Valeur d’attribut invalide|**SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBrowseConnect**<br /><br /> **SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDataSources**<br /><br /> **SQLDescribeCol**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLDrivers**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetCursorName**<br /><br /> **SQLGetData**<br /><br /> **SQLGetDescField**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLPutData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetCursorName**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetDescRec**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HY091 HY091|Identifiant de champ descripteur invalide|**SQLColAttribute**<br /><br /> **SQLGetDescField**<br /><br /> **SQLSetDescField**|  
|HY092 HY092|Identification d’attribut/option invalide|**SQLAllocHandle**<br /><br /> **QLBulkOperations**<br /><br /> **SQLCopyDesc (SQLCopyDesc)**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetEnvAttr**<br /><br /> **QLParamData**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetDescField**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**|  
|HY095 HY095|Type de fonction hors de portée|**SQLGetFunctions**|  
|HY096 HY096|Type d’information invalide|**SQLGetInfo**|  
|HY097 HY097|Type de colonne hors de portée|**SQLSpecialColumns**|  
|HY098 HY098|Type de portée hors de portée|**SQLSpecialColumns**|  
|HY099 HY099|Type nul hors de portée|**SQLSpecialColumns**|  
|Hy100|Type d’option d’unicité hors de portée|**SQLStatistics**|  
|Hy101|Type d’option de précision hors de portée|**SQLStatistics**|  
|HY103|Code de récupération invalide|**SQLDataSources**<br /><br /> **SQLDrivers**|  
|Hy104|Précision invalide ou valeur à l’échelle|**SQLBindParameter**|  
|Hy105|Type de paramètre invalide|**SQLBindParameter**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLParamData**<br /><br /> **SQLSetDescField**|  
|HY106|Aller type hors de portée|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|HY107|Valeur de la ligne hors de portée|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLSetPos**|  
|HY109 HY109|Position de curseur invalide|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLGetData**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLNativeSql**<br /><br /> **SQLParamData**<br /><br /> **SQLSetPos**|  
|HY110|Achèvement du conducteur invalide|**SQLDriverConnect**|  
|HY111|Valeur de signet invalide|**SQLExtendedFetch**<br /><br /> **SQLFetchScroll**|  
|HYC00|Fonctionnalité facultative non implémentée|**SQLBindCol**<br /><br /> **SQLBindParameter**<br /><br /> **SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLColAttribute**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLEndTran**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetConnectAttr**<br /><br /> **SQLGetData**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLGetInfo**<br /><br /> **SQLGetStmtAttr**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetConnectAttr**<br /><br /> **SQLSetEnvAttr**<br /><br /> **SQLSetPos**<br /><br /> **SQLSetStmtAttr**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HYT00|Délai expiré|**SQLBrowseConnect**<br /><br /> **SQLBulkOperations (SQLBulkOperations)**<br /><br /> **SQLColumnPrivileges**<br /><br /> **SQLColumns**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLExtendedFetch**<br /><br /> **SQLForeignKeys**<br /><br /> **SQLGetTypeInfo**<br /><br /> **SQLParamData**<br /><br /> **SQLPrepare**<br /><br /> **SQLPrimaryKeys**<br /><br /> **SQLProcedureColumns**<br /><br /> **SQLProcedures**<br /><br /> **SQLSetPos**<br /><br /> **SQLSpecialColumns**<br /><br /> **SQLStatistics**<br /><br /> **SQLTablePrivileges**<br /><br /> **SQLTables**|  
|HYT01 (HYT01)|Délai de connexion expiré|Toutes les fonctions ODBC sauf :<br /><br /> **SQLDrivers**<br /><br /> **SQLDataSources**<br /><br /> **SQLGetEnvAttr**<br /><br /> **SQLSetEnvAttr**|  
|IM001|Le conducteur ne prend pas en charge cette fonction|Toutes les fonctions ODBC sauf :<br /><br /> **SQLAllocHandle**<br /><br /> **SQLDataSources**<br /><br /> **SQLDrivers**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLGetFunctions**|  
|IM002|Nom source de données non trouvé et aucun pilote par défaut spécifié|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM003|Le conducteur spécifié n’a pas pu être chargé|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM004|Le **conducteur SQLAllocHandle** sur SQL_HANDLE_ENV a échoué|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM005|Le **conducteur SQLAllocHandle** sur SQL_HANDLE_DBC a échoué|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM006|Le conducteur **SQLSetConnectAttr** a échoué|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM007|Aucune source de données ou pilote spécifié; dialogue interdit|**SQLDriverConnect**|  
|IM008|Le dialogue a échoué|**SQLDriverConnect**|  
|IM009|Incapable de charger la traduction DLL|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**<br /><br /> **SQLSetConnectAttr**|  
|IM010|Nom source de données trop long|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|IM011|Nom du conducteur trop long|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM012|ERREUR de syntaxe mot-clé DRIVER|**SQLBrowseConnect**<br /><br /> **SQLDriverConnect**|  
|IM013|Erreur de fichier de trace|Toutes les fonctions ODBC.|  
|IM014|Nom invalide du fichier DSN|**SQLDriverConnect**|  
|IM015|Source de données de fichiers corrompues|**SQLDriverConnect**|
