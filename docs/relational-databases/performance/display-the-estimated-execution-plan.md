---
title: "Affichage du plan d&#39;ex&#233;cution estim&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "zoom [SQL Server]"
  - "plan d'exécution estimé [SQL Server]"
  - "affichage des plans d'exécution"
  - "visualisation des plans d'exécution"
  - "plans d’exécution [SQL Server], affichage"
  - "personnalisation de l'affichage du plan d'exécution [SQL Server]"
  - "modification de l'affichage du plan d'exécution"
  - "zoom personnalisé [SQL Server]"
ms.assetid: e94aa576-4c0c-4c54-ad05-6c3432cc615b
caps.latest.revision: 26
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 26
---
# Affichage du plan d&#39;ex&#233;cution estim&#233;
  Cette rubrique décrit la génération d'un plan d'exécution estimé au format graphique à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Lors de la génération de ces plans, les traitements ou requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] ne sont pas exécutés, mais le plan d'exécution des requêtes que [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] utiliserait probablement si celles-ci étaient exécutées s'affiche.  
  
 Pour utiliser cette fonctionnalité, les utilisateurs doivent disposer des autorisations adéquates pour exécuter la requête [!INCLUDE[tsql](../../includes/tsql-md.md)] correspondant au plan d'exécution graphique à générer, et ils doivent posséder l'autorisation SHOWPLAN pour toutes les bases de données référencées par la requête.  
  
### Pour afficher le plan d'exécution estimé pour une requête  
  
1.  Dans la barre d’outils, cliquez sur **Requête de moteur de base de données**. Vous pouvez également ouvrir une requête existante et afficher le plan d’exécution estimé en cliquant sur le bouton **Ouvrir un fichier** dans la barre d’outils puis en choisissant la requête existante.  
  
2.  Entrez la requête pour laquelle afficher le plan d'exécution estimé.  
  
3.  Dans le menu **Requête**, cliquez sur **Afficher le plan d’exécution estimé** ou cliquez sur le bouton **Afficher le plan d’exécution estimé** dans la barre d’outils. Le plan d’exécution estimé s’affiche sous l’onglet **Plan d’exécution** du volet de résultats. Pour afficher des informations supplémentaires, placez le curseur sur les icônes des opérateurs logiques et physiques, et consultez la description et les propriétés de l'opérateur indiquées dans l'infobulle. Il est également possible d'afficher les propriétés des opérateurs dans la fenêtre Propriétés. Si les propriétés ne sont pas visibles, cliquez avec le bouton droit sur un opérateur, puis cliquez sur **Propriétés**. Sélectionnez l'opérateur de votre choix.  
  
4.  Pour modifier l’affichage du plan d’exécution, cliquez avec le bouton droit sur le plan d’exécution, puis sélectionnez **Zoom avant**, **Zoom arrière**, **Zoom personnalisé** ou **Zoom pour ajuster**. **Zoom avant** et **Zoom arrière** permettent respectivement d’agrandir et de réduire l’affichage du plan d’exécution suivant des pourcentages fixes. **Zoom personnalisé** vous permet de définir votre propre facteur de zoom, par exemple 80 %. Enfin, l’option **Zoom pour ajuster** agrandit le plan de sorte que sa taille soit ajustée en fonction de celle du volet de résultats.  
  
  