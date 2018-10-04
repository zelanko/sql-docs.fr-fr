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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47840007"
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (pilotes pour les bases de données de poste de travail)
Un index unique est renvoyé (le cas échéant) pour l’indicateur SQL_BEST_ROWID dans *fColType*. Aucun jeu de résultats n’est retourné pour l’indicateur SQL_ROWVER.  
  
 Tous les ID de ligne ont une étendue de SQL_SCOPE_CURROW.  
  
 Critères spéciaux n’est pas pris en charge pour une le *szTableQualifier* ou *szTableName* argument.
