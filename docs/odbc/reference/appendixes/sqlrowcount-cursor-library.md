---
title: SQLRowCount (bibliothèque de curseurs) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 868f7e45a6f10ce6aa76e84117c5c605c6321d89
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLRowCount** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLRowCount**, consultez [SQLRowCount, fonction](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Lorsqu’une application appelle **SQLRowCount** avec l’instruction associée au curseur, la bibliothèque de curseurs retourne le nombre de lignes de données qu’il a récupéré à partir du pilote.  
  
 Lorsqu’une application appelle **SQLRowCount** avec l’instruction associée à une mise à jour positionnée ou d’une instruction delete, la bibliothèque de curseurs retourne le nombre de lignes affectées par l’instruction.  
  
 Lorsqu’une application appelle **SQLRowCount** après un **sélectionnez** instruction, la bibliothèque de curseurs retourne -1.
