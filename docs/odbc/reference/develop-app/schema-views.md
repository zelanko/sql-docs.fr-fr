---
description: Vues de schéma
title: Vues de schéma | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 34e1b52b5e96b5fedb964e53f14a7b554d12aa05
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429071"
---
# <a name="schema-views"></a>Vues de schéma
Une application peut récupérer des informations de métadonnées à partir du SGBD en appelant des fonctions de catalogue ODBC ou à l’aide de INFORMATION_SCHEMA vues. Les vues sont définies par la norme ANSI SQL-92.  
  
 S’ils sont pris en charge par le SGBD et le pilote, les vues de INFORMATION_SCHEMA offrent un moyen plus puissant et plus complet de récupérer les métadonnées que les fonctions de catalogue ODBC. Une application peut exécuter sa propre instruction **Select** personnalisée sur l’un de ces affichages, joindre des vues ou exécuter une Union sur les vues. Tout en offrant un meilleur utilitaire et un plus grand nombre de métadonnées, les vues INFORMATION_SCHEMA ne sont pas souvent prises en charge par le SGBD. Cela peut changer à mesure que d’autres SGBD et pilotes sont conformes à SQL-92.  
  
 Pour déterminer les vues prises en charge, une application appelle **SQLGetInfo** avec l’option SQL_INFO_SCHEMA_VIEWS. Pour récupérer les métadonnées d’une vue prise en charge, l’application exécute une instruction **Select** qui spécifie les informations de schéma requises.
