---
title: SQLSetScrollOptions (pilotes de base de données de bureau) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Desktop Database Drivers
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5c47255b455354c49133d61c3546be63ab2380a1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299432"
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (pilotes pour les bases de données de poste de travail)
Les curseurs de transfert et statiques sont pris en charge pour les SQL_CONCUR_READ_ONLY.  
  
 Seuls les curseurs de jeu de clés sont pris en charge pour un argument *fConcurrency* de SQL_CONCUR_LOCK.  
  
 Un argument *fConcurrency* de SQL_CONCUR_ROWVER n’est pas pris en charge.  
  
 Les curseurs dynamiques et les curseurs mixtes ne sont pas pris en charge.
