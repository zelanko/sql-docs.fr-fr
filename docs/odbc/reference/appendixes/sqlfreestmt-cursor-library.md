---
title: SQLFreeStmt (bibliothèque de curseurs) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 04d1ef277a75720f75e15b77d7bb8c5e7b96fafa
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLFreeStmt** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLFreeStmt**, consultez [SQLFreeStmt, fonction](../../../odbc/reference/syntax/sqlfreestmt-function.md).  
  
 Si une application appelle **SQLFreeStmt** avec l’option SQL_UNBIND après avoir appelé **SQLExtendedFetch**, **SQLFetch**, ou **SQLFetchScroll**, la bibliothèque de curseurs retourne une erreur. Avant qu’il peut annuler la liaison des colonnes de jeu de résultats, une application doit appeler **SQLCloseCursor** ou **SQLFreeStmt** avec l’option SQL_CLOSE.
