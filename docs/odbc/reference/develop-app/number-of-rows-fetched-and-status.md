---
title: Nombre de lignes récupérées et statuts (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302360"
---
# <a name="number-of-rows-fetched-and-status"></a>Nombre de lignes extraites et état
Si l’attribut de l’SQL_ATTR_ROWS_FETCHED_PTR déclaration a été défini, il spécifie un tampon qui renvoie le nombre de rangées récupérées par l’appel à **SQLFetch** ou **SQLFetchScroll**, et les lignes d’erreur. (Ce nombre est un décompte de toutes les lignes qui n’ont pas le statut SQL_ROW_NO_ROWS.) Après un appel à **SQLBulkOperations** ou **SQLSetPos**, le tampon contient le nombre de rangées qui ont été touchées par une opération en vrac effectuée par la fonction. Si l’attribut de SQL_ATTR_ROW_STATUS_PTR déclaration a été défini, **SQLFetch** ou **SQLFetchScroll** renvoie le *tableau d’état* de la ligne, qui fournit l’état de chaque rangée retournée. Les deux tampons indiqués par ces champs sont attribués par l’application et peuplés par le conducteur. Une application doit s’assurer que ces pointeurs restent valides jusqu’à ce que le curseur soit fermé.  
  
 Les inscriptions dans le tableau d’état de la rangée indiquent si chaque rangée a été récupérée avec succès, si elle a été mise à jour, ajoutée, ou supprimée depuis qu’elle a été récupérée pour la dernière fois, et si une erreur s’est produite en allant chercher la rangée. Si **SQLFetch** ou **SQLFetchScroll** rencontre une erreur lors de la récupération d’une rangée d’un ensemble de rangées à plusieurs lancers, ou si **SQLBulkOperations** avec un argument *d’opération* de SQL_FETCH_BY_BOOKMARK rencontre une erreur tout en effectuant un aller chercher en vrac, il définit la valeur correspondante dans le tableau d’état de la rangée à SQL_ROW_ERROR, continue à chercher des rangées, et retourne SQL_SUCCESS_WITH_INFO. Pour de plus amples renseignements sur le traitement des erreurs et le tableau d’état de la rangée, consultez les descriptions de la fonction [SQLFetch et](../../../odbc/reference/syntax/sqlfetch-function.md) [SQLFetchScroll.](../../../odbc/reference/syntax/sqlfetchscroll-function.md)
