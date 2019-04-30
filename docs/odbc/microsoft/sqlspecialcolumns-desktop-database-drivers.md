---
title: SQLSpecialColumns (pilotes pour les postes de travail de base de données) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f319e6a28a1eba5f803e9cf7f7087f45f227fd87
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200510"
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (pilotes pour les bases de données de poste de travail)
Un index unique est renvoyé (le cas échéant) pour l’indicateur SQL_BEST_ROWID dans *fColType*. Aucun jeu de résultats n’est retourné pour l’indicateur SQL_ROWVER.  
  
 Tous les ID de ligne ont une étendue de SQL_SCOPE_CURROW.  
  
 Critères spéciaux n’est pas pris en charge pour une le *szTableQualifier* ou *szTableName* argument.
