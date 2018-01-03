---
title: "Résumé des résultats d’une requête (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- summarizing query results
- queries [SQL Server], results
- aggregate queries [SQL Server]
ms.assetid: c9e15350-ed57-4d95-814d-815fbebfd86b
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 23be6f5ada4c862e4f55d71d3023a8e0c56fdb7a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="summarize-query-results-visual-database-tools"></a>Résumé des résultats d'une requête (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Certains principes logiques s’appliquent à la création de requêtes d’agrégation. Par exemple, il est impossible d'afficher le contenu de lignes individuelles dans une requête de synthèse. Le Concepteur de requêtes et de vues vous aide à respecter ces principes dans le comportement du [volet Schéma](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) et du [volet Critères](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md) .  
  
Une bonne compréhension des principes des requêtes d'agrégation et du comportement du Concepteur de requêtes et de vues permet de créer des requêtes correctes du point de vue logique. Le principe déterminant est que les requêtes d'agrégation ne peuvent donner que des informations de synthèse. C'est pourquoi la plupart des principes présentés plus loin décrivent les différentes méthodes permettant de référencer des colonnes de données individuelles dans une requête d'agrégation.  
  
## <a name="in-this-section"></a>Dans cette section  
[Utiliser des colonnes dans des requêtes d'agrégation &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-columns-in-aggregate-queries-visual-database-tools.md)  
Décrit les concepts relatifs au regroupement et à la synthèse de colonnes à l'aide des clauses GROUP BY, WHERE et HAVING.  
  
[Compter les lignes d'une table &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/count-rows-in-a-table-visual-database-tools.md)  
Fournit la procédure de comptage du nombre de lignes dans une table ou du nombre de lignes dans une table qui répondent à un jeu de critères.  
  
[Synthétiser ou regrouper des valeurs de toutes les lignes d'une table &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)  
Fournit la procédure de synthèse de toutes les lignes plutôt que d'un jeu de lignes groupées.  
  
[Synthétiser ou regrouper des valeurs à l'aide d'expressions personnalisées &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-or-aggregate-values-using-custom-expressions-visual-database-tools.md)  
Fournit la procédure d'utilisation d'expressions pour synthétiser ou regrouper plutôt que d'utiliser des clauses prédéfinies.  
  
## <a name="related-sections"></a>Sections connexes  
[Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
Fournit des liens vers des rubriques qui décrivent l'utilisation du Concepteur de requêtes et de vues.  
  
