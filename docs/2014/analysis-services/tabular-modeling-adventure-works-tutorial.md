---
title: Tabulaire (didacticiel Adventure Works) de modélisation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 140d0b43-9455-4907-9827-16564a904268
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af4d5dfa6d59338fb9640143b387b78421375e05
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66067797"
---
# <a name="tabular-modeling-adventure-works-tutorial"></a>Modélisation tabulaire (didacticiel Adventure Works)
  Ce didacticiel inclut des leçons sur la création d’un modèle tabulaire [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Analysis Services, à l’aide de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Dans ce didacticiel, vous allez apprendre à effectuer les opérations suivantes :  
  
-   Créer un nouveau projet de modèle tabulaire dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
-   Importer des données depuis une base de données relationnelle SQL Server dans un projet de modèle tabulaire.  
  
-   Créer et gérer des relations entre des tables dans le modèle.  
  
-   Créer et gérer des calculs, des mesures et des indicateurs de performance clés qui aideront les utilisateurs à analyser les données du modèle.  
  
-   Créer et gérer des perspectives et des hiérarchies qui aideront les utilisateurs à parcourir plus facilement les données du modèle en fournissant des points de vue spécifiques à l'entreprise et à l'application.  
  
-   Créer des partitions qui divisent les données des tables en plus petites parties logiques pouvant être traitées indépendamment des autres partitions.  
  
-   Sécuriser les objets et les données du modèle en créant des rôles à l'aide des membres utilisateurs.  
  
-   Déployer un modèle tabulaire dans un bac à sable (sandbox) ou une instance de production d'Analysis Services exécutée en mode tabulaire.  
  
## <a name="tutorial-scenario"></a>Scénario du didacticiel  
 Ce didacticiel est basé sur [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], une société fictive. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] est une grande entreprise multinationale spécialisée dans la fabrication et la distribution de métaux et de pièces détachées de vélos pour les marchés d'Amérique du Nord, d'Europe et d'Asie. Le siège de la société [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] est situé dans la ville de Bothell, à Washington, où 500 personnes sont employées. Par ailleurs, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] emploie plusieurs équipes commerciales régionales pour couvrir son marché.  
  
 Pour améliorer la prise en charge des besoins d'analyse des données des équipes de vente et marketing et des seniors du management, vous devez créer un modèle tabulaire pour que les utilisateurs analysent les données des ventes Internet dans la base de données AdventureWorksDW donnée en exemple.  
  
 Pour pouvoir exécuter ce didacticiel et le modèle tabulaire des ventes Internet Adventure Works, vous devez suivre plusieurs leçons. Dans chaque leçon, vous exécuterez une série de tâches ; vous devez effectuer chaque tâche dans l'ordre pour terminer la leçon. Dans une leçon donnée, il peut exister plusieurs tâches qui aboutissent à des résultats similaires ; toutefois, la façon dont vous effectuez chaque tâche est légèrement différente. Cela montre qu'il existe souvent plusieurs façon d'effectuer une tâche particulière, le but étant de vous inciter à utiliser les compétences acquises lors des tâches effectuées précédemment.  
  
 L'objectif des leçons est de vous guider dans la création d'un modèle tabulaire de base en mode In-Memory à l'aide de plusieurs fonctionnalités incluses dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Chaque leçon découle de la leçon précédente, c'est pourquoi vous devez effectuer les leçons dans l'ordre. Lorsque vous avez terminé toutes les leçons, vous aurez créé et déployé un exemple de modèle tabulaire des ventes Internet Adventure Works sur un serveur Analysis Services.  
  
> [!NOTE]  
>  Ce didacticiel n'inclut pas de leçons ni d'informations sur la gestion d'une base de données de modèles tabulaires déployée à l'aide de SQL Server Management Studio, ou sur l'utilisation d'une application cliente de création de rapports pour se connecter à un modèle déployé et parcourir ses données.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour pouvoir exécuter ce didacticiel, les composants suivants doivent être installés :  
  
-   Instance [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Analysis Services exécutée en mode tabulaire.  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] .  
  
-   Exemple de base de données AdventureWorksDW. Cet exemple de base de données comprend les données nécessaires pour effectuer ce didacticiel. Pour télécharger la base de données, consultez [ https://go.microsoft.com/fwlink/?LinkID=335807 ](https://go.microsoft.com/fwlink/?LinkID=335807).  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 2003 ou version ultérieure (pour utiliser la fonctionnalité Analyser dans Excel dans la leçon 11)  
  
## <a name="lessons"></a>Leçons  
 Ce didacticiel inclut les leçons suivantes :  
  
|Leçon|Durée estimée|  
|------------|--------------------------------|  
|[Leçon 1 : Créez un projet de modèle tabulaire](lesson-1-create-a-new-tabular-model-project.md)|10 minutes|  
|[Leçon 2 : Ajouter des données](lesson-2-add-data.md)|20 minutes|  
|[Leçon 3 : Renommer des colonnes](rename-columns.md)|20 minutes|  
|[Leçon 4 : Marquer comme Table de dates](lesson-3-mark-as-date-table.md)|3 minutes|  
|[Leçon 5 : Créer des relations](lesson-4-create-relationships.md)|10 minutes|  
|[Leçon 6 : Créer des colonnes calculées](lesson-5-create-calculated-columns.md)|15 minutes|  
|[Leçon 7 : Créer des mesures](lesson-6-create-measures.md)|30 minutes|  
|[Leçon 8 : Créer des indicateurs de Performance clés](lesson-7-create-key-performance-indicators.md)|15 minutes|  
|[Leçon 9 : Créer des Perspectives](lesson-8-create-perspectives.md)|5 minutes|  
|[Leçon 10 : Créer des hiérarchies](lesson-9-create-hierarchies.md)|20 minutes|  
|[Leçon 11 : Créer des Partitions](lesson-10-create-partitions.md)|15 minutes|  
|[Leçon 12 : Créer des rôles](lesson-11-create-roles.md)|15 minutes|  
|[Leçon 13 : Analyser dans Excel](lesson-12-analyze-in-excel.md)|20 minutes|  
|[Leçon 14 : Déployer](lesson-13-deploy.md)|5 minutes|  
  
## <a name="supplemental-lessons"></a>Leçons supplémentaires  
 Ce didacticiel inclut également des [leçons supplémentaires](../tutorials/supplemental-lessons.md). Les rubriques de cette section ne sont pas requises pour suivre ce didacticiel, mais peuvent être utiles pour mieux comprendre les fonctionnalités de création de modèles tabulaires avancées.  
  
 Ce didacticiel inclut les leçons supplémentaires suivantes :  
  
|Leçon|Durée estimée|  
|------------|--------------------------------|  
|[Implémentation de la sécurité dynamique à l'aide des filtres de lignes](../tutorials/implement-dynamic-security-by-using-row-filters.md)|30 minutes|  
|[Configurer les propriétés de création de rapports pour les rapports Power View](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)configurer les propriétés de création de rapports pour les rapports Power View|30 minutes|  
  
## <a name="next-step"></a>Étape suivante  
 Pour démarrer le didacticiel, passez à la première leçon : [Leçon 1 : Créez un projet de modèle tabulaire](lesson-1-create-a-new-tabular-model-project.md).  
  
  
