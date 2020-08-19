---
description: SQLSpecialColumns (pilotes pour les bases de données de poste de travail)
title: SQLSpecialColumns (pilotes de base de données de bureau) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Desktop Database Drivers
ms.assetid: 3de66fdf-053b-4354-979d-e76a5a5e975f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3f023c4f82c5a2f9af7af2e34cc697ffdb34206
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421613"
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (pilotes pour les bases de données de poste de travail)
Un index unique est retourné (le cas échéant) pour l’indicateur SQL_BEST_ROWID dans *fColType*. Aucun jeu de résultats n’est retourné pour l’indicateur SQL_ROWVER.  
  
 Tous les ID de ligne ont une étendue de SQL_SCOPE_CURROW.  
  
 Les critères spéciaux ne sont pas pris en charge pour l’argument *szTableQualifier* ou *szTableName* .
