---
title: Ce que fait le conducteur Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: 75dcdea6-ff6b-4ac8-aa11-a1f9edbeb8e6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c0438478f5aa625ffdd4d3bcd1c0a6f0f80d3367
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301390"
---
# <a name="what-the-driver-does"></a>Ce que fait le pilote
Le tableau suivant résume les fonctions et les énoncés qui attribuent un pilote ODBC *3.x* à mettre en œuvre pour les curseurs de blocs et de curseurs défilants.  
  
|Fonction ou<br /><br /> attribut d'instruction|Commentaires|  
|-----------------------------------------|--------------|  
|SQL_ATTR_ROW_STATUS_PTR|Définit l’adresse du tableau d’état de la rangée rempli par **SQLFetch** et **SQLFetchScroll**. Ce tableau est également rempli par **SQLSetPos** si **SQLSetPos** est appelé dans l’état de déclaration S6. Si **SQLSetPos** est appelé dans l’état S7, ce tableau n’est pas rempli, mais le tableau souligné par *l’argument RowStatusArray* de **SQLExtendedFetch** est rempli. Pour plus d’informations, voir [Transitions d’énoncés](../../../odbc/reference/appendixes/statement-transitions.md) à l’annexe B : Tableaux de transition d’État ODBC.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Définit l’adresse du tampon dans lequel **SQLFetch** et **SQLFetchScroll** retournent le nombre de rangées récupérées. Si **SQLExtendedFetch** est appelé, ce tampon n’est pas rempli, mais *l’argument RowCountPtr* indique le nombre de rangées récupérées.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Définit la taille de l’aviron utilisée par **SQLFetch** et **SQLFetchScroll**.|  
|SQL_ROWSET_SIZE|Définit la taille de l’aviron utilisée par **SQLExtendedFetch**. Les conducteurs ODBC *3.x* implémentent ceci s’ils veulent travailler avec des applications ODBC *2.x* qui appellent **SQLExtendedFetch** ou **SQLSetPos**.|  
|**SQLBulkOperations (SQLBulkOperations)**|Si un conducteur ODBC *3.x* doit travailler avec des applications ODBC *2.x* qui utilisent **SQLSetPos** avec une *opération* de SQL_ADD, le conducteur doit prendre en charge **SQLSetPos** avec une *opération* de SQL_ADD en plus de **SQLBulkOperations** avec une *opération* de SQL_ADD.|  
|**SQLExtendedFetch**|Retourne le jeu de ligne spécifié. Les conducteurs ODBC *3.x* implémentent ceci s’ils veulent travailler avec des applications ODBC *2.x* qui appellent **SQLExtendedFetch** ou **SQLSetPos**. Voici les détails de la mise en œuvre :<br /><br /> - Le conducteur récupère la taille de l’aviron à partir de la valeur de l’attribut SQL_ROWSET_SIZE déclaration.<br />- Le conducteur récupère l’adresse du tableau d’état de la ligne de l’argument *RowStatusArray,* et non l’attribut de déclaration SQL_ATTR_ROW_STATUS_PTR. *L’argument de RowStatusArray* dans un appel à **SQLExtendedFetch** ne doit pas être un pointeur nul. (Notez que dans ODBC *3.x*, l’attribut de déclaration SQL_ATTR_ROW_STATUS_PTR peut être un pointeur nul.)<br />- Le conducteur récupère l’adresse du tampon récupéré des rangées de l’argument *RowCountPtr,* et non l’attribut de déclaration SQL_ATTR_ROWS_FETCHED_PTR.<br />- Le conducteur retourne SQLSTATE 01S01 (Erreur de suite) pour indiquer qu’une erreur s’est produite alors que des rangées ont été récupérées par un appel à **SQLExtendedFetch**. Un conducteur ODBC *3.x* devrait retourner SQLSTATE 01S01 (Erreur de ligne) seulement lorsque **SQLExtendedFetch** est appelé, pas lorsque **SQLFetch** ou **SQLFetchScroll** est appelé. Pour préserver la compatibilité vers l’arrière, lorsque SQLSTATE 01S01 (Erreur de ligne) est retourné par **SQLExtendedFetch**, le gestionnaire de conducteur ne commande pas d’enregistrements d’état dans la file d’attente d’erreur selon les règles énoncées dans la section « Séquence des dossiers d’état » de [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).|  
|**SQLFetch**|Retourne le jeu de ligne suivant. Voici les détails de la mise en œuvre :<br /><br /> - Le conducteur récupère la taille de l’aviron à partir de la valeur de l’attribut SQL_ATTR_ROW_ARRAY_SIZE déclaration.<br />- Le conducteur récupère l’adresse du tableau d’état de la ligne à partir de l’attribut SQL_ATTR_ROW_STATUS_PTR déclaration.<br />- Le conducteur récupère l’adresse du tampon récupéré par les rangées à partir de l’attribut SQL_ATTR_ROWS_FETCHED_PTR déclaration.<br />- L’application peut mélanger les appels entre **SQLFetchScroll** et **SQLFetch**.<br />-   **SQLFetch** renvoie des signets si la colonne 0 est liée.<br />-   **SQLFetch** peut être appelé à retourner plus d’une rangée.<br />- Le conducteur ne retourne pas SQLSTATE 01S01 (Erreur de ligne) pour indiquer qu’une erreur s’est produite alors que des rangées ont été récupérées par un appel à **SQLFetch**.|  
|**SQLFetchScroll**|Retourne le jeu de ligne spécifié. Voici les détails de la mise en œuvre :<br /><br /> - Le conducteur récupère la taille de l’aviron à partir de l’attribut SQL_ATTR_ROW_ARRAY_SIZE déclaration.<br />- Le conducteur récupère l’adresse du tableau d’état de la ligne à partir de l’attribut SQL_ATTR_ROW_STATUS_PTR déclaration.<br />- Le conducteur récupère l’adresse du tampon récupéré par les rangées à partir de l’attribut SQL_ATTR_ROWS_FETCHED_PTR déclaration.<br />- L’application peut mélanger les appels entre **SQLFetchScroll** et **SQLFetch**.<br />- Le conducteur ne retourne pas SQLSTATE 01S01 (Erreur de ligne) pour indiquer qu’une erreur s’est produite alors que des rangées ont été récupérées par un appel à **SQLFetchScroll**.|  
|**SQLSetPos**|Effectue diverses opérations positionnées. Voici les détails de la mise en œuvre :<br /><br /> - Cela peut être appelé dans les états de déclaration S6 ou S7. Pour plus de détails, voir [Transitions de déclaration](../../../odbc/reference/appendixes/statement-transitions.md) à l’annexe B : ODBC State Transition Tables.<br />- Si cela est appelé dans l’état de déclaration S5 ou S6, le conducteur récupère la taille de la ligne de l’attribut de SQL_ATTR_ROWS_FETCHED_PTR déclaration et l’adresse du tableau d’état de la ligne de l’attribut de déclaration SQL_ATTR_ROW_STATUS_PTR.<br />- Si cela est appelé dans l’état de déclaration S7, le conducteur récupère la taille rowset de l’attribut de déclaration SQL_ROWSET_SIZE et l’adresse du tableau de statut de la ligne de l’argument *RowStatusArray* de **SQLExtendedFetch**.<br />- Le conducteur retourne SQLSTATE 01S01 (Erreur de suite) seulement pour indiquer qu’une erreur s’est produite alors que des rangées ont été récupérées par un appel à **SQLSetPos** pour effectuer une opération en vrac lorsque la fonction est appelée dans l’état S7. Pour préserver la compatibilité rétrograde, si SQLSTATE 01S01 (Erreur de ligne) est retourné par **SQLSetPos**, le gestionnaire de conducteur ne commande pas d’enregistrements d’état dans la file d’attente d’erreur selon les règles énoncées dans la section « Séquence des dossiers d’état » de [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).<br />- Si le conducteur doit travailler avec des applications ODBC *2.x* qui appellent **SQLSetPos** avec un argument *d’opération* de SQL_ADD, le conducteur doit soutenir **SQLSetPos** avec un argument *d’opération* de SQL_ADD.|
