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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 20e1632e8da765b0da2785bd846b67d13ebe01ed
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302360"
---
# <a name="number-of-rows-fetched-and-status"></a>Nombre de lignes extraites et état
Si l’attribut d’instruction SQL_ATTR_ROWS_FETCHED_PTR a été défini, il spécifie une mémoire tampon qui retourne le nombre de lignes extraites par l’appel à **SQLFetch** ou **SQLFetchScroll**, ainsi que les lignes d’erreur. (Ce nombre est le nombre de toutes les lignes qui n’ont pas l’État SQL_ROW_NO_ROWS.) Après un appel à **SQLBulkOperations** ou **SQLSetPos**, la mémoire tampon contient le nombre de lignes affectées par une opération en bloc effectuée par la fonction. Si l’attribut d’instruction SQL_ATTR_ROW_STATUS_PTR a été défini, **SQLFetch** ou **SQLFetchScroll** retourne le tableau d' *État de ligne,* qui fournit l’état de chaque ligne retournée. Les deux mémoires tampons pointées par ces champs sont allouées par l’application et remplies par le pilote. Une application doit s’assurer que ces pointeurs restent valides jusqu’à la fermeture du curseur.  
  
 Les entrées dans le tableau d’état des lignes déterminent si chaque ligne a été extraite avec succès, si elle a été mise à jour, ajoutée ou supprimée depuis sa dernière extraction, et si une erreur s’est produite lors de l’extraction de la ligne. Si **SQLFetch** ou **SQLFetchScroll** rencontre une erreur lors de l’extraction d’une ligne d’un ensemble de lignes multiligne, ou si **SQLBulkOperations** avec un argument d' *opération* de SQL_FETCH_BY_BOOKMARK rencontre une erreur lors de l’exécution d’une extraction en bloc, il définit la valeur correspondante dans le tableau d’état des lignes sur SQL_ROW_ERROR, continue l’extraction des lignes et retourne SQL_SUCCESS_WITH_INFO. Pour plus d’informations sur la gestion des erreurs et le tableau d’état des lignes, consultez les descriptions des fonctions [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md) et [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) .
