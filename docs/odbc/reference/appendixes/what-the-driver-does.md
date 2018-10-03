---
title: Ce que fait le pilote | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 685f67c9f24593a5c50097de426b76fef068d6e9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628177"
---
# <a name="what-the-driver-does"></a>Ce que fait le pilote
Le tableau suivant récapitule les fonctions d’attributs et d’instruction une ODBC 3 *.x* pilote doit implémenter pour le bloc et de curseurs avec défilement.  
  
|Fonction ou<br /><br /> attribut d'instruction|Commentaires|  
|-----------------------------------------|--------------|  
|SQL_ATTR_ROW_STATUS_PTR|Définit l’adresse du tableau d’état de ligne est remplie par **SQLFetch** et **SQLFetchScroll**. Ce tableau est également rempli par **SQLSetPos** si **SQLSetPos** est appelée dans l’état de l’instruction S6. Si **SQLSetPos** est appelée dans un état S7, ce tableau n’est pas rempli, mais le tableau vers lequel pointe le *RowStatusArray* argument de **SQLExtendedFetch** est remplie. Pour plus d’informations, consultez [Transitions d’instruction](../../../odbc/reference/appendixes/statement-transitions.md) dans les tableaux des transitions d’état annexe b : ODBC.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Définit l’adresse de la mémoire tampon dans laquelle **SQLFetch** et **SQLFetchScroll** retourner le nombre de lignes extraites. Si **SQLExtendedFetch** est appelée, cette mémoire tampon n’est pas remplie, mais le *RowCountPtr* argument pointe vers le nombre de lignes extraites.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Définit la taille de l’ensemble de lignes utilisée par **SQLFetch** et **SQLFetchScroll**.|  
|SQL_ROWSET_SIZE|Définit la taille de l’ensemble de lignes utilisée par **SQLExtendedFetch**. ODBC 3 *.x* pilotes implémentent cela s’ils souhaitent travailler avec ODBC 2. *x* les applications qui appellent **SQLExtendedFetch** ou **SQLSetPos**.|  
|**SQLBulkOperations**|Si un ODBC 3 *.x* pilote doit fonctionner avec ODBC 2. *x* les applications qui utilisent **SQLSetPos** avec un *opération* de SQL_ADD, le pilote doit prendre en charge **SQLSetPos** avec un  *Opération* de SQL_ADD outre **SQLBulkOperations** avec un *opération* de SQL_ADD.|  
|**SQLExtendedFetch**|Retourne l’ensemble de lignes spécifié. ODBC 3 *.x* pilotes implémentent cela s’ils souhaitent travailler avec ODBC 2. *x* les applications qui appellent **SQLExtendedFetch** ou **SQLSetPos**. Détails d’implémentation sont les suivantes :<br /><br /> -Le pilote récupère la taille de l’ensemble de lignes à partir de la valeur de l’attribut d’instruction SQL_ROWSET_SIZE.<br />-Le pilote récupère l’adresse du tableau d’état de ligne à partir de la *RowStatusArray* argument, pas l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR. Le *RowStatusArray* argument dans un appel à **SQLExtendedFetch** ne doit pas être un pointeur null. (Notez que dans ODBC 3 *.x*, l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR peut être un pointeur null.)<br />-Le pilote récupère l’adresse de la mémoire tampon de lignes lues à partir de la *RowCountPtr* argument, pas l’attribut d’instruction SQL_ATTR_ROWS_FETCHED_PTR.<br />-Le pilote retourne 01 s 01 SQLSTATE (erreur de ligne) pour indiquer qu’une erreur s’est produite alors que les lignes ont été extraites par un appel à **SQLExtendedFetch**. Un ODBC 3 *.x* pilote doit retourner 01 s 01 SQLSTATE (erreur de ligne) uniquement lorsque **SQLExtendedFetch** est appelée, pas lorsque **SQLFetch** ou **SQLFetchScroll** est appelée. Pour préserver la compatibilité descendante, lorsque 01 s 01 SQLSTATE (erreur de ligne) est retourné par **SQLExtendedFetch**, le Gestionnaire de pilotes ne trie pas les enregistrements d’état dans la file d’attente de l’erreur selon les règles indiquées dans le « séquence d’état Section des enregistrements de « de [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).|  
|**SQLFetch**|Retourne l’ensemble de lignes suivant. Détails d’implémentation sont les suivantes :<br /><br /> -Le pilote récupère la taille de l’ensemble de lignes à partir de la valeur de l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE.<br />-Le pilote récupère l’adresse du tableau d’état de ligne à partir de l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR.<br />-Le pilote récupère l’adresse des lignes extraites de mémoire tampon à partir de l’attribut d’instruction SQL_ATTR_ROWS_FETCHED_PTR.<br />-L’application peut combiner des appels entre **SQLFetchScroll** et **SQLFetch**.<br />-   **SQLFetch** renvoie des signets, si la colonne 0 est liée.<br />-   **SQLFetch** peut être appelée pour retourner plusieurs lignes.<br />-Le pilote ne retourne pas de 01 s 01 SQLSTATE (erreur de ligne) pour indiquer qu’une erreur s’est produite alors que les lignes ont été extraites par un appel à **SQLFetch**.|  
|**SQLFetchScroll**|Retourne l’ensemble de lignes spécifié. Détails d’implémentation sont les suivantes :<br /><br /> -Le pilote récupère la taille de l’ensemble de lignes à partir de l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE.<br />-Le pilote récupère l’adresse du tableau d’état de ligne à partir de l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR.<br />-Le pilote récupère l’adresse des lignes extraites de mémoire tampon à partir de l’attribut d’instruction SQL_ATTR_ROWS_FETCHED_PTR.<br />-L’application peut combiner des appels entre **SQLFetchScroll** et **SQLFetch**.<br />-Le pilote ne retourne pas de 01 s 01 SQLSTATE (erreur de ligne) pour indiquer qu’une erreur s’est produite alors que les lignes ont été extraites par un appel à **SQLFetchScroll**.|  
|**SQLSetPos**|Effectue des opérations positionnées différents. Détails d’implémentation sont les suivantes :<br /><br /> -Il peut être appelé dans les États d’instruction S6 ou S7. Pour plus d’informations, consultez [Transitions d’instruction](../../../odbc/reference/appendixes/statement-transitions.md) dans les tableaux des transitions d’état annexe b : ODBC.<br />-Si cela est appelée dans un état instruction S5 ou S6, le pilote récupère la taille de l’ensemble de lignes à partir de l’attribut SQL_ATTR_ROWS_FETCHED_PTR d’instruction et l’adresse du tableau d’état de ligne à partir de l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR.<br />-Si cela est appelée dans l’état de l’instruction S7, le pilote récupère la taille de l’ensemble de lignes à partir de l’attribut d’instruction SQL_ROWSET_SIZE et l’adresse du tableau d’état de ligne à partir de la *RowStatusArray* argument de  **SQLExtendedFetch**.<br />-Le pilote retourne 01 s 01 SQLSTATE (erreur de ligne) uniquement pour indiquer qu’une erreur s’est produite alors que les lignes ont été extraites par un appel à **SQLSetPos** pour effectuer une opération en bloc lorsque la fonction est appelée dans un état S7. Pour maintenir la compatibilité descendante, si 01 s 01 SQLSTATE (erreur de ligne) est retourné par **SQLSetPos**, le Gestionnaire de pilotes ne trie pas les enregistrements d’état dans la file d’attente de l’erreur selon les règles indiquées dans les « séquence d’enregistrements d’état » section de [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).<br />-Si le pilote doit fonctionner avec ODBC 2. *x* les applications qui appellent **SQLSetPos** avec un *opération* argument de SQL_ADD, le pilote doit prendre en charge **SQLSetPos** avec un  *Opération* argument de SQL_ADD.|
