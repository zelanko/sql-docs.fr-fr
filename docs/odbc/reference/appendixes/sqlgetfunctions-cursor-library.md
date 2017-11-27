---
title: "SQLGetFunctions (bibliothèque de curseurs) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLGetFunctions function [ODBC], Cursor Library
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b27a2ca5c99d65b269eb388da4ab6c30d8c8121f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (bibliothèque de curseurs)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Cette rubrique décrit l’utilisation de la **SQLGetFunctions** fonction dans la bibliothèque de curseurs. Pour des informations générales sur **SQLGetFunctions**, consultez [fonction SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md).  
  
 Lorsque vous appelez **SQLGetFunctions**, la bibliothèque de curseurs retourne la prise en charge **SQLExtendedFetch**, **SQLFetchScroll**, **SQLSetPos**, et **SQLSetScrollOptions**, outre les fonctions prises en charge par le pilote.
