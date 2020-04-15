---
title: SQLSetStmtAttr (Cursor Library) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtAttr function [ODBC], Cursor Library
ms.assetid: 6018a733-c2c8-4047-92ec-92cf85031767
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1bdd9b3b559d5cc78a0d44f5280aae347bc8996a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300489"
---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Ce sujet traite de l’utilisation de la fonction **SQLSetStmtAttr** dans la bibliothèque de curseurs. Pour plus d’informations générales sur **SQLSetStmtAttr**, voir [SQLSetStmtAttr Function](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
 La bibliothèque de curseurs prend en charge les attributs de déclaration suivantes avec **SQLSetStmtAttr**:  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 La bibliothèque de curseurs ne prend en charge que les valeurs SQL_CURSOR_FORWARD_ONLY et SQL_CURSOR_STATIC de l’attribut de l’énoncé de SQL_ATTR_CURSOR_TYPE.  
  
 Pour les curseurs avant-seulement, la bibliothèque de curseur prend en charge la valeur SQL_CONCUR_READ_ONLY de l’attribut de l’SQL_ATTR_CONCURRENCY déclaration. Pour les curseurs statiques, la bibliothèque de curseurs prend en charge les valeurs SQL_CONCUR_READ_ONLY et SQL_CONCUR_VALUES de l’attribut de l’énoncé de SQL_ATTR_CONCURRENCY.  
  
 La bibliothèque de curseurs ne prend en charge que la valeur SQL_SC_NON_UNIQUE de l’attribut de l’énoncé de SQL_ATTR_SIMULATE_CURSOR.  
  
 Bien que les spécifications de l’ODBC appuient les appels à **SQLSetStmtAttr** avec les attributs SQL_ATTR_PARAM_BIND_TYPE ou SQL_ATTR_ROW_BIND_TYPE après **SQLFetch** ou **SQLFetchScroll** a été appelé, la bibliothèque curseur n’a pas. Avant qu’il puisse modifier le type de liaison dans la bibliothèque de curseur, l’application doit fermer le curseur. La bibliothèque de curseurs prend en charge la modification de la SQL_ATTR_ROW_BIND_OFFSET_PTR, de la SQL_ATTR_PARAM_BIND_OFFSET_PTR, de la SQL_ATTR_ROWS_FETCHED_PTR et de SQL_ATTR_PARAMS_PROCESSED_PTR attributs lorsqu’un curseur est ouvert.  
  
 Une application peut appeler **SQLSetStmtAttr** avec un **attribut** de SQL_ATTR_ROW_ARRAY_SIZE pour changer la taille de l’aviron pendant qu’un curseur est ouvert. La nouvelle taille de ramset entrera en vigueur la prochaine fois **que SQLFetchScroll** ou **SQLFetch** est appelé.  
  
 La bibliothèque de curseurs prend en charge la fixation de l’attribut SQL_ATTR_PARAM_BIND_OFFSET_PTR ou SQL_ATTR_ROW_BIND_OFFSET_PTR énoncé pour permettre des compensations contraignantes. Le décalage de liaison ne sera pas utilisé pour les appels à **SQLFetch** lorsque la bibliothèque de curseur est utilisée avec un ODBC 2. *x* conducteur.  
  
 La bibliothèque de curseurs prend en charge l’établissement de l’attribut SQL_ATTR_USE_BOOKMARKS énoncé à SQL_UB_VARIABLE.
