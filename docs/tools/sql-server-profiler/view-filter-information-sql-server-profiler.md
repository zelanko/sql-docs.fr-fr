---
title: "Afficher des informations de filtre (SQL Server Profiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "affichage d'informations de filtre"
  - "filtres [SQL Server], affichage"
  - "filtres [SQL Server], traces"
  - "traces [SQL Server], filtres"
  - "visualisation d'informations de filtre"
ms.assetid: 8d002dea-376a-452c-b3ca-3e93656ed75f
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# Afficher des informations de filtre (SQL Server Profiler)
  Cette rubrique indique comment afficher des filtres sur des colonnes de données pour des classes d'événements en utilisant [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### Pour afficher les informations de filtrage  
  
1.  Ouvrez un fichier de trace, une table de trace ou un script SQL, et dans le menu **Fichier**, cliquez sur **Propriétés**. Si vous modifiez un modèle de trace ou créez une nouvelle trace, ignorez cette étape.  
  
2.  Sous l’onglet **Sélection des événements**, cliquez avec le bouton droit sur le nom de la colonne de données du filtre à afficher, puis cliquez sur **Modifier le filtre des colonnes**.  
  
3.  Dans la boîte de dialogue **Modifier le filtre**, développez les opérateurs de comparaison de filtre pour afficher la valeur affectée pour le critère spécifié. Recommencez les étapes 2 et 3 pour toutes les colonnes pour lesquelles vous souhaitez afficher des informations de filtre.  
  
> [!NOTE]  
>  Les opérateurs de comparaison avec des valeurs affectées apparaissent en caractères gras.  
  
## Voir aussi  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  