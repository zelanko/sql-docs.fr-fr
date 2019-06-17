---
title: Nombre de lignes extraites et état | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- row status array [ODBC]
- number of rows fetched [ODBC]
- result sets [ODBC], row status array
ms.assetid: a069b979-5108-4905-932f-8ae8e7905ff2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab4830ddd56335959dd7049a1dabdcc3a0354213
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149332"
---
# <a name="number-of-rows-fetched-and-status"></a>Nombre de lignes extraites et état
Si l’attribut d’instruction SQL_ATTR_ROWS_FETCHED_PTR a été définie, elle spécifie une mémoire tampon qui retourne le nombre de lignes extraites par l’appel à **SQLFetch** ou **SQLFetchScroll**et les lignes d’erreur. (Ce nombre est un nombre de toutes les lignes qui n’ont pas l’état SQL_ROW_NO_ROWS.) Après un appel à **SQLBulkOperations** ou **SQLSetPos**, la mémoire tampon contient le nombre de lignes affectées par une opération en bloc effectuée par la fonction. Si l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR a été défini, **SQLFetch** ou **SQLFetchScroll** retourne le *tableau d’état de ligne,* qui fournit l’état de chaque ligne retournée. À la fois des mémoires tampons vers lequel pointés ces champs sont allouées par l’application et remplies par le pilote. Une application doit s’assurer que ces pointeurs restent valides jusqu'à ce que le curseur est fermé.  
  
 Entrées dans l’état de tableau de statut de la ligne si chaque ligne a été récupérée avec succès, si elle a été mise à jour, ajouté ou supprimé depuis sa dernière extraction et si une erreur s’est produite lors de l’extraction de la ligne. Si **SQLFetch** ou **SQLFetchScroll** rencontre une erreur lors de la récupération d’une ligne d’un ensemble de lignes multiligne, ou si **SQLBulkOperations** avec un *opération*  argument de SQL_FETCH_BY_BOOKMARK rencontre une erreur lors de l’exécution d’une extraction en bloc, il définit la valeur correspondante dans le tableau d’état de ligne à SQL_ROW_ERROR, continue l’extraction de lignes et retourne SQL_SUCCESS_WITH_INFO. Pour plus d’informations sur la gestion des erreurs et le tableau d’état de ligne, consultez le [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md) et [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) des descriptions de fonction.
