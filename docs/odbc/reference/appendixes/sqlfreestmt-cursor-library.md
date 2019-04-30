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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07d56e9b77c7e7e34b0de98ef5704b26aa2b86dd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199465"
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique explique comment utiliser le **SQLFreeStmt** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLFreeStmt**, consultez [SQLFreeStmt, fonction](../../../odbc/reference/syntax/sqlfreestmt-function.md).  
  
 Si une application appelle **SQLFreeStmt** avec l’option SQL_UNBIND après l’appel **SQLExtendedFetch**, **SQLFetch**, ou **SQLFetchScroll**, la bibliothèque de curseurs retourne une erreur. Avant qu’il peut séparer les colonnes de jeu de résultats, une application doit appeler **SQLCloseCursor** ou **SQLFreeStmt** avec l’option SQL_CLOSE.
