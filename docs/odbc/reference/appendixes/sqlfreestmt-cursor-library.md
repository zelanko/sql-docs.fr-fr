---
title: "SQLFreeStmt (bibliothèque de curseurs) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b648c069c3930e923db8a929f7203807c67b128e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLFreeStmt** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLFreeStmt**, consultez [SQLFreeStmt, fonction](../../../odbc/reference/syntax/sqlfreestmt-function.md).  
  
 Si une application appelle **SQLFreeStmt** avec l’option SQL_UNBIND après avoir appelé **SQLExtendedFetch**, **SQLFetch**, ou **SQLFetchScroll**, la bibliothèque de curseurs retourne une erreur. Avant qu’il peut annuler la liaison des colonnes de jeu de résultats, une application doit appeler **SQLCloseCursor** ou **SQLFreeStmt** avec l’option SQL_CLOSE.
