---
title: "(Didacticiel Adventure Works) de modélisation multidimensionnelle | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
helpviewer_keywords:
- tutorials [Analysis Services]
- Analysis Services, tutorials
ms.assetid: db55e226-601a-4026-8651-573195555a59
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: a288cb2c30cc1e5146291c62e4a3aca4dc5af5ce
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="multidimensional-modeling-adventure-works-tutorial"></a>Modélisation multidimensionnelles (didacticiel Adventure Works)
Didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Ce didacticiel explique comment utiliser [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] pour développer et déployer un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et tous les exemples sont basés sur la société fictive [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] .  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
Dans ce didacticiel, vous apprendrez les éléments suivants:  
  
-   Définir des sources de données, des vues de source de données, des dimensions, des attributs, des relations d'attributs, des hiérarchies et des cubes dans un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] au sein de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
-   Afficher les données de dimension et de cube en déployant le projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] vers une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]et en traitant les objets déployés pour les remplir avec des données issues de la source de données sous-jacente.  
  
-   Apprendre à modifier les mesures, les dimensions, les hiérarchies, les attributs et les groupes de mesures dans le projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et ensuite à déployer les modifications incrémentielles dans le cube déployé sur le serveur de développement.  
  
-   Définir des calculs, des indicateurs de performance clés (KPI), des actions, des perspectives, des traductions et des rôles de sécurité à l'intérieur d'un cube.  
  
Une description du scénario accompagne ce didacticiel afin que vous puissiez mieux comprendre le contexte de ces leçons. Pour plus d'informations, consultez [Analysis Services Tutorial Scenario](../analysis-services/analysis-services-tutorial-scenario.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
Vous aurez besoin d'exemples de données, de fichiers d'exemple de projet et d'un logiciel pour effectuer toutes les leçons du didacticiel. Pour obtenir des instructions sur la façon de vous procurer et d'installer les éléments requis pour ce didacticiel, consultez l' [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](../analysis-services/install-sample-data-and-projects.md).  
  
En outre, les autorisations suivantes doivent être en place pour achever correctement ce didacticiel :  
  
-   Vous devez être membre du groupe local Administrateur sur l'ordinateur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ou être membre du rôle d'administration de serveur dans l'instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   Vous devez disposer d'autorisations de lecture dans l'exemple de base de données **AdventureWorksDW2012** . Cet exemple de base de données est valable pour la version de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] .  
  
## <a name="lessons"></a>Leçons  
Ce didacticiel inclut les leçons suivantes.  
  
|Leçon|Durée estimée|  
|----------|------------------------------|  
|[Leçon 1 : Définition d'une vue de source de données dans un projet Analysis Services](../analysis-services/lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)|15 minutes|  
|[Leçon 2 : Définition et déploiement d'un cube](../analysis-services/lesson-2-defining-and-deploying-a-cube.md)|30 minutes|  
|[Leçon 3 : Modification des mesures, des attributs et des hiérarchies](../analysis-services/lesson-3-modifying-measures-attributes-and-hierarchies.md)|45 minutes|  
|[Leçon 4 : Définition des attributs avancés et des propriétés de dimension](../analysis-services/lesson-4-defining-advanced-attribute-and-dimension-properties.md)|120 minutes|  
|[Leçon 5 : Définition des relations entre les dimensions et les groupes de mesures](../analysis-services/lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)|45 minutes|  
|[Leçon 6 : Définition de calculs](../analysis-services/lesson-6-defining-calculations.md)|45 minutes|  
|[Leçon 7 : Définition d’indicateurs de performance clés &#40;KPIs&#41;](../analysis-services/lesson-7-defining-key-performance-indicators-kpis.md)|30 minutes|  
|[Leçon 8 : Définition des actions](../analysis-services/lesson-8-defining-actions.md)|30 minutes|  
|[Leçon 9 : Définition de perspectives et de traductions](../analysis-services/lesson-9-defining-perspectives-and-translations.md)|30 minutes|  
|[Leçon 10 : Définition de rôles administratifs](../analysis-services/lesson-10-defining-administrative-roles.md)|15 minutes|  
  
> [!NOTE]  
> La base de données de cube que vous allez créer dans ce didacticiel est une version simplifiée du projet de modèle multidimensionnel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui fait partie des exemples de bases de données Adventure Works disponibles en téléchargement sur le site Codeplex. La version du didacticiel de la base de données multidimensionnelle Adventure Works est simplifiée afin de se consacrer davantage aux compétences spécifiques que vous souhaitez maîtriser au plus vite. Après avoir terminé le didacticiel, explorez le projet de modèle multidimensionnel par vous même afin d'approfondir votre compréhension de la modélisation multidimensionnelle [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="next-step"></a>Étape suivante  
Pour démarrer le didacticiel, passez à la première leçon : [Lesson 1: Defining a Data Source View within an Analysis Services Project](../analysis-services/lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md).  
  
  
  
