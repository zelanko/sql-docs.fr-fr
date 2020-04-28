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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5f8cd4ed0912f9f1e71d64b32449b5d46f9ef1a3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299389"
---
# <a name="sqlspecialcolumns-desktop-database-drivers"></a>SQLSpecialColumns (pilotes pour les bases de données de poste de travail)
Un index unique est retourné (le cas échéant) pour l’indicateur SQL_BEST_ROWID dans *fColType*. Aucun jeu de résultats n’est retourné pour l’indicateur SQL_ROWVER.  
  
 Tous les ID de ligne ont une étendue de SQL_SCOPE_CURROW.  
  
 Les critères spéciaux ne sont pas pris en charge pour l’argument *szTableQualifier* ou *szTableName* .
