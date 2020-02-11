---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e530d0b16811cdf25a5bc1d99f5386efdb55ccd4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905326"
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (pilotes pour les bases de données de poste de travail)
Un index unique est retourné (le cas échéant) pour l’indicateur SQL_BEST_ROWID dans *fColType*. Aucun jeu de résultats n’est retourné pour l’indicateur SQL_ROWVER.  
  
 Tous les ID de ligne ont une étendue de SQL_SCOPE_CURROW.  
  
 Les critères spéciaux ne sont pas pris en charge pour l’argument *szTableQualifier* ou *szTableName* .
