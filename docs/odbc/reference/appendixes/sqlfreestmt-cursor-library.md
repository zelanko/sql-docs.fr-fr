---
title: SQLFreeStmt (bibliothèque de curseurs) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d78075593926c15dbaeb1904603b08e990f64983
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302020"
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 Cette rubrique traite de l’utilisation de la fonction **SQLFreeStmt** dans la bibliothèque de curseurs. Pour obtenir des informations générales sur **SQLFreeStmt**, consultez [fonction SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md).  
  
 Si une application appelle **SQLFreeStmt** avec l’option SQL_UNBIND après avoir appelé **SQLExtendedFetch**, **SQLFetch**ou **SQLFetchScroll**, la bibliothèque de curseurs retourne une erreur. Avant de pouvoir détacher des colonnes de jeu de résultats, une application doit appeler **SQLCloseCursor** ou **SQLFreeStmt** avec l’option SQL_CLOSE.
