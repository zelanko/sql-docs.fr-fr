---
title: SQLSetStmtAttr (bibliothèque de curseurs) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d4e5bd6ec27891e80933dfcc42beec9056d2d3a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62735207"
---
# <a name="sqlsetstmtattr-cursor-library"></a>SQLSetStmtAttr (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLSetStmtAttr** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLSetStmtAttr**, consultez [SQLSetStmtAttr, fonction](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
 La bibliothèque de curseurs prend en charge les attributs d’instruction suivantes avec **SQLSetStmtAttr**:  
  
|||  
|-|-|  
|SQL_ATTR_CONCURRENCY|SQL_ATTR_ROW_BIND_OFFSET_PTR|  
|SQL_ATTR_CURSOR_TYPE|SQL_ATTR_ROW_BIND_TYPE|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|SQL_ATTR_ROWSET_ARRAY_SIZE|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|SQL_ATTR_SIMULATE_CURSOR|  
|SQL_ATTR_PARAM_BIND_TYPE|SQL_ATTR_USE_BOOKMARKS|  
  
 La bibliothèque de curseurs prend en charge uniquement les valeurs SQL_CURSOR_FORWARD_ONLY et SQL_CURSOR_STATIC de l’attribut d’instruction SQL_ATTR_CURSOR_TYPE.  
  
 Pour les curseurs avant uniquement, la bibliothèque de curseurs prend en charge la valeur SQL_CONCUR_READ_ONLY de l’attribut d’instruction SQL_ATTR_CONCURRENCY. Pour les curseurs statiques, la bibliothèque de curseurs prend en charge les valeurs SQL_CONCUR_READ_ONLY et SQL_CONCUR_VALUES de l’attribut d’instruction SQL_ATTR_CONCURRENCY.  
  
 La bibliothèque de curseurs prend en charge uniquement la valeur SQL_SC_NON_UNIQUE de l’attribut d’instruction SQL_ATTR_SIMULATE_CURSOR.  
  
 Bien que la spécification ODBC prend en charge les appels à **SQLSetStmtAttr** avec les attributs SQL_ATTR_PARAM_BIND_TYPE ou SQL_ATTR_ROW_BIND_TYPE après **SQLFetch** ou **SQLFetchScroll**  a été appelée, le curseur n’est pas le cas de bibliothèque. Avant d’avoir modifié le type de liaison dans la bibliothèque de curseurs, l’application doit fermer le curseur. La bibliothèque de curseurs prend en charge la modification des SQL_ATTR_ROW_BIND_OFFSET_PTR, SQL_ATTR_PARAM_BIND_OFFSET_PTR, SQL_ATTR_ROWS_FETCHED_PTR, et les attributs d’instruction SQL_ATTR_PARAMS_PROCESSED_PTR lorsqu’un curseur est ouvert.  
  
 Une application peut appeler **SQLSetStmtAttr** avec un **attribut** de SQL_ATTR_ROW_ARRAY_SIZE pour modifier la taille de l’ensemble de lignes lorsqu’un curseur est ouvert. La nouvelle taille d’ensemble de lignes prendront effet au prochain **SQLFetchScroll** ou **SQLFetch** est appelée.  
  
 La bibliothèque de curseurs prend en charge la définition de l’attribut d’instruction SQL_ATTR_PARAM_BIND_OFFSET_PTR ou SQL_ATTR_ROW_BIND_OFFSET_PTR pour activer les décalages des liaisons. Le décalage de la liaison ne sera pas utilisé pour les appels à **SQLFetch** lorsque la bibliothèque de curseurs est utilisée avec un ODBC 2. *x* pilote.  
  
 La bibliothèque de curseurs prend en charge la définition de l’attribut d’instruction SQL_ATTR_USE_BOOKMARKS sur SQL_UB_VARIABLE.
