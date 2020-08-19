---
description: SQLSetScrollOptions (pilotes pour les bases de données de poste de travail)
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
ms.openlocfilehash: 57237aca0a68119f6ab8f967b9641f2a2a52fc8c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421643"
---
# <a name="sqlsetscrolloptions-desktop-database-drivers"></a>SQLSetScrollOptions (pilotes pour les bases de données de poste de travail)
Les curseurs de transfert et statiques sont pris en charge pour les SQL_CONCUR_READ_ONLY.  
  
 Seuls les curseurs de jeu de clés sont pris en charge pour un argument *fConcurrency* de SQL_CONCUR_LOCK.  
  
 Un argument *fConcurrency* de SQL_CONCUR_ROWVER n’est pas pris en charge.  
  
 Les curseurs dynamiques et les curseurs mixtes ne sont pas pris en charge.
