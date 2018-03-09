---
title: "SQLSetScrollOptions (pilotes d’ordinateur de bureau) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ddac617904825a5ad324ad991a0721b505f704a5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (pilotes bureau de base de données)
Les curseurs avant et statiques sont prises en charge pour la valeur SQL_CONCUR_READ_ONLY.  
  
 Uniquement les curseurs pilotés par jeu de clés sont pris en charge pour un *fConcurrency* argument de SQL_CONCUR_LOCK.  
  
 Un *fConcurrency* argument de SQL_CONCUR_ROWVER n’est pas pris en charge.  
  
 Les curseurs dynamiques et les curseurs mixtes ne sont pas pris en charge.
