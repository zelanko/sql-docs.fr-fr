---
title: "Mod&#233;lisation tabulaire (didacticiel Adventure Works) | Microsoft Docs"
ms.custom: ""
ms.date: "03/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
keywords: 
  - "Analysis Services"
  - "Modèle tabulaire"
  - "Didacticiel"
  - "SSAS"
ms.assetid: 140d0b43-9455-4907-9827-16564a904268
caps.latest.revision: 40
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 35
---
# Mod&#233;lisation tabulaire (didacticiel Adventure Works)
Ce didacticiel inclut des leçons sur la création d’un modèle tabulaire [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Analysis Services, à l’aide de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
  
## Contenu du didacticiel  
Dans ce didacticiel, vous allez apprendre à effectuer les opérations suivantes :  
  
-   Créer un nouveau projet de modèle tabulaire dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
-   Importer des données depuis une base de données relationnelle SQL Server dans un projet de modèle tabulaire.  
  
-   Créer et gérer des relations entre des tables dans le modèle.  
  
-   Créer et gérer des calculs, des mesures et des indicateurs de performance clés qui aideront les utilisateurs à analyser les données du modèle.  
  
-   Créer et gérer des perspectives et des hiérarchies qui aideront les utilisateurs à parcourir plus facilement les données du modèle en fournissant des points de vue spécifiques à l'entreprise et à l'application.  
  
-   Créer des partitions qui divisent les données des tables en plus petites parties logiques pouvant être traitées indépendamment des autres partitions.  
  
-   Sécuriser les objets et les données du modèle en créant des rôles à l'aide des membres utilisateurs.  
  
-   Déployer un modèle tabulaire dans un bac à sable (sandbox) ou une instance de production d'Analysis Services exécutée en mode tabulaire.  
  
## Scénario  
Ce didacticiel est basé sur [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], une société fictive. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] est une grande entreprise multinationale spécialisée dans la fabrication et la distribution de métaux et de pièces détachées de vélos pour les marchés d'Amérique du Nord, d'Europe et d'Asie. Le siège de la société [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] est situé dans la ville de Bothell, à Washington, où 500 personnes sont employées. Par ailleurs, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] emploie plusieurs équipes commerciales régionales pour couvrir son marché.  
  
Pour améliorer la prise en charge des besoins d'analyse des données des équipes de vente et marketing et des seniors du management, vous devez créer un modèle tabulaire pour que les utilisateurs analysent les données des ventes Internet dans la base de données AdventureWorksDW donnée en exemple.  
  
Pour pouvoir exécuter ce didacticiel et le modèle tabulaire des ventes Internet Adventure Works, vous devez suivre plusieurs leçons. Dans chaque leçon, vous exécuterez une série de tâches ; vous devez effectuer chaque tâche dans l'ordre pour terminer la leçon. Dans une leçon donnée, il peut exister plusieurs tâches qui aboutissent à des résultats similaires ; toutefois, la façon dont vous effectuez chaque tâche est légèrement différente. Cela montre qu'il existe souvent plusieurs façon d'effectuer une tâche particulière, le but étant de vous inciter à utiliser les compétences acquises lors des tâches effectuées précédemment.  
  
L'objectif des leçons est de vous guider dans la création d'un modèle tabulaire de base en mode In-Memory à l'aide de plusieurs fonctionnalités incluses dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Chaque leçon découle de la leçon précédente, c'est pourquoi vous devez effectuer les leçons dans l'ordre. Lorsque vous avez terminé toutes les leçons, vous aurez créé et déployé un exemple de modèle tabulaire des ventes Internet Adventure Works sur un serveur Analysis Services.  
  
Ce didacticiel n'inclut pas de leçons ni d'informations sur la gestion d'une base de données de modèles tabulaires déployée à l'aide de SQL Server Management Studio, ou sur l'utilisation d'une application cliente de création de rapports pour se connecter à un modèle déployé et parcourir ses données.  
  
## Conditions préalables  
Pour pouvoir exécuter ce didacticiel, les composants suivants doivent être installés :  
  
-   [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Instance Analysis Services exécutée en mode tabulaire.  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. [Obtenir la dernière version.](https://msdn.microsoft.com/library/mt204009.aspx)  
  
-   Exemple de base de données Adventure Works DW 2014. Cet exemple de base de données comprend les données nécessaires pour effectuer ce didacticiel. Pour télécharger l’exemple de base de données, accédez à la page [http://go.microsoft.com/fwlink/?LinkID=335807](http://go.microsoft.com/fwlink/?LinkID=335807).  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 2003 ou version ultérieure (pour utiliser la fonctionnalité Analyser dans Excel dans la leçon 11)  
  
## Leçons  
Ce didacticiel inclut les leçons suivantes :  
  
|Leçon|Durée estimée|  
|----------|------------------------------|  
|[Leçon 1 : Créer un projet de modèle tabulaire](../analysis-services/lesson-1-create-a-new-tabular-model-project.md)|10 minutes|  
|[Leçon 2 : Ajouter des données](../analysis-services/lesson-2-add-data.md)|20 minutes|  
|[Leçon 3 : Renommer des colonnes](../analysis-services/lesson-3-rename-columns.md)|20 minutes|  
|[Leçon 4 : Marquer en tant que table de dates](../analysis-services/lesson-4-mark-as-date-table.md)|3 minutes|  
|[Leçon 5 : Créer des relations](../analysis-services/lesson-5-create-relationships.md)|10 minutes|  
|[Leçon 6 : Créer des colonnes calculées](../analysis-services/lesson-6-create-calculated-columns.md)|15 minutes|  
|[Leçon 7 : Créer des mesures](../analysis-services/lesson-7-create-measures.md)|30 minutes|  
|[Leçon 8 : Créer les indicateurs de performance clés](../analysis-services/lesson-8-create-key-performance-indicators.md)|15 minutes|  
|[Leçon 9 : Créer des perspectives](../Topic/Lesson%209:%20Create%20Perspectives.md)|5 minutes|  
|[Leçon 10 : Créer des hiérarchies](../analysis-services/lesson-10-create-hierarchies.md)|20 minutes|  
|[Leçon 11 : Créer des partitions](../analysis-services/lesson-11-create-partitions.md)|15 minutes|  
|[Leçon 12 : Créer des rôles](../analysis-services/lesson-12-create-roles.md)|15 minutes|  
|[Leçon 13 : Analyser dans Excel](../analysis-services/lesson-13-analyze-in-excel.md)|20 minutes|  
|[Leçon 14 : Déploiement](../analysis-services/lesson-14-deploy.md)|5 minutes|  
  
## Leçons supplémentaires  
Ce didacticiel inclut également des [leçons supplémentaires](../Topic/Supplemental%20Lessons.md). Les rubriques de cette section ne sont pas requises pour suivre ce didacticiel, mais peuvent être utiles pour mieux comprendre les fonctionnalités de création de modèles tabulaires avancées.  
  
|Leçon|Durée estimée|  
|----------|------------------------------|  
|[Implémentation de la sécurité dynamique à l'aide des filtres de lignes](../analysis-services/implement-dynamic-security-by-using-row-filters.md)|30 minutes|  
|[Configurer les propriétés de création de rapports pour les rapports Power View](../analysis-services/configure-reporting-properties-for-power-view-reports.md)|30 minutes|  
  
## Étape suivante  
Pour démarrer le didacticiel, passez à la première leçon : [Leçon 1 : Créer un projet de modèle tabulaire](../analysis-services/lesson-1-create-a-new-tabular-model-project.md).  
  
  
  
