---
title: "Tabulaire (didacticiel Adventure Works) de modélisation | Documents Microsoft"
ms.custom: 
ms.date: 04/19/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
keywords:
- Analysis Services
- "Modèle tabulaire"
- Didacticiel
- SSAS
ms.assetid: 140d0b43-9455-4907-9827-16564a904268
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 811b5df37a88fa7a03eec2b9bc05acb87ec67bcc
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---
# <a name="tabular-modeling-adventure-works-tutorial"></a>Modélisation tabulaire (didacticiel Adventure Works)
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

Ce didacticiel inclut des leçons sur la création d’un modèle tabulaire d’Analysis Services à le [niveau de compatibilité 1200](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md) à l’aide de [SQL Server Data Tools (SSDT)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)et déployer votre modèle à un serveur Analysis Services en local ou dans Azure.  
 
Si vous utilisez SQL Server 2017 ou Azure Analysis Services, et que vous souhaitez créer votre modèle à la compatibilité 1400 niveau, utilisez le [Azure Analysis Services - didacticiel Adventure Works](https://review.docs.microsoft.com/azure/analysis-services/tutorials/aas-adventure-works-tutorial?branch=master). Cette version de mise à jour utilise la fonctionnalité obtenir des données de nouveau, moderne pour vous connecter et importer les données sources et utilise le langage de M pour configurer des partitions.
 
  
## <a name="what-youll-learn"></a>Contenu du didacticiel   
  
-   Comment créer un nouveau projet de modèle tabulaire dans SSDT.
  
-   Importer des données depuis une base de données relationnelle SQL Server dans un projet de modèle tabulaire.  
  
-   Créer et gérer des relations entre des tables dans le modèle.  
  
-   Créer et gérer des calculs, des mesures et des indicateurs de performance clés qui aideront les utilisateurs à analyser les données du modèle.  
  
-   Créer et gérer des perspectives et des hiérarchies qui aideront les utilisateurs à parcourir plus facilement les données du modèle en fournissant des points de vue spécifiques à l'entreprise et à l'application.  
  
-   Créer des partitions qui divisent les données des tables en plus petites parties logiques pouvant être traitées indépendamment des autres partitions.  
  
-   Sécuriser les objets et les données du modèle en créant des rôles à l'aide des membres utilisateurs.  
  
-   Comment déployer un modèle tabulaire à un serveur Analysis Services en local ou dans Azure.  
  
## <a name="scenario"></a>Scénario  
Ce didacticiel est basé sur Adventure Works Cycles, une société fictive. Adventure Works est une société de fabrication multinationale volumineux qui produit et distribue des bicyclettes métalliques et pour les marchés d’Amérique du Nord, Europe et Asie. Avec son siège social à Bothell, Washington, la société emploie 500 employés. En outre, Adventure Works emploie plusieurs équipes commerciales régionales pour couvrir son marché.  
  
Pour améliorer la prise en charge des besoins d'analyse des données des équipes de vente et marketing et des seniors du management, vous devez créer un modèle tabulaire pour que les utilisateurs analysent les données des ventes Internet dans la base de données AdventureWorksDW donnée en exemple.  
  
Pour pouvoir exécuter ce didacticiel et le modèle tabulaire des ventes Internet Adventure Works, vous devez suivre plusieurs leçons. Dans chaque leçon, vous exécuterez une série de tâches ; vous devez effectuer chaque tâche dans l'ordre pour terminer la leçon. Dans une leçon donnée il peut y avoir plusieurs tâches qui accomplissent des résultats similaires, mais comment vous effectuez chaque tâche est légèrement différente. Cela est de montrer qu’il existe souvent plusieurs façons pour effectuer une tâche particulière et à utiliser les compétences que vous avez appris dans les tâches précédentes.  
  
L’objectif des leçons est pour vous guider dans la création d’un modèle tabulaire de base en cours d’exécution en mode In-Memory à l’aide de nombreuses fonctionnalités incluses dans SSDT. Chaque leçon découle de la leçon précédente, c'est pourquoi vous devez effectuer les leçons dans l'ordre. Une fois que vous avez terminé toutes les leçons, vous avez créé et déployé le modèle tabulaire d’exemple Adventure Works Internet Sales sur un serveur Analysis Services.  
  
Ce didacticiel n'inclut pas de leçons ni d'informations sur la gestion d'une base de données de modèles tabulaires déployée à l'aide de SQL Server Management Studio, ou sur l'utilisation d'une application cliente de création de rapports pour se connecter à un modèle déployé et parcourir ses données.  
  
## <a name="prerequisites"></a>Conditions préalables  
Pour effectuer ce didacticiel, vous devez les conditions préalables suivantes :  
  
-   La version la plus récente de [ ! INCLURE[ssBIDevStudioFull](../ssdt/download-sql-server-data-tools-ssdt.md).

-   La dernière version de SQL Server Management Studio. [Obtenir la dernière version](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). 
  
-   Une application cliente telle que [Power BI Desktop](https://powerbi.microsoft.com/desktop/) ou [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel.    
  
-   Une instance de SQL Server avec la base de données exemple Adventure Works DW 2014. Cet exemple de base de données comprend les données nécessaires pour effectuer ce didacticiel. [Obtenir la dernière version](http://go.microsoft.com/fwlink/?LinkID=335807).  
  

-   Un Azure Analysis Services ou SQL Server 2016 instance ou version ultérieure Analysis Services pour déployer votre modèle. [S’inscrire à une évaluation gratuite de Azure Analysis Services](https://azure.microsoft.com/services/analysis-services/).
  
## <a name="lessons"></a>Leçons  
Ce didacticiel inclut les leçons suivantes :  
  
|Leçon|Durée estimée|  
|----------|------------------------------|  
|[Leçon 1 : Créer un projet de modèle tabulaire](../analysis-services/lesson-1-create-a-new-tabular-model-project.md)|10 minutes|  
|[Leçon 2 : Ajouter des données](../analysis-services/lesson-2-add-data.md)|20 minutes|  
|[Leçon 3 : Marquer en tant que table de dates](../analysis-services/lesson-3-mark-as-date-table.md)|3 minutes|  
|[Leçon 4 : Créer des relations](../analysis-services/lesson-4-create-relationships.md)|10 minutes|  
|[Leçon 5 : Créer des colonnes calculées](../analysis-services/lesson-5-create-calculated-columns.md)|15 minutes|
|[Leçon 6 : Créer des mesures](../analysis-services/lesson-6-create-measures.md)|30 minutes|  
|[Leçon 7 : Créer des indicateurs de performance clés](../analysis-services/lesson-7-create-key-performance-indicators.md)|15 minutes|  
|[Leçon 8 : Créer des Perspectives](../analysis-services/lesson-8-create-perspectives.md)|5 minutes|  
|[Leçon 9 : Créer des hiérarchies](../analysis-services/lesson-9-create-hierarchies.md)|20 minutes|  
|[Leçon 10 : Créer des Partitions](../analysis-services/lesson-10-create-partitions.md)|15 minutes|  
|[Leçon 11 : Créer des rôles](../analysis-services/lesson-11-create-roles.md)|15 minutes|  
|[Leçon 12 : Analyser dans Excel](../analysis-services/lesson-12-analyze-in-excel.md)|20 minutes| 
|[Leçon 13 : Déployer](../analysis-services/lesson-13-deploy.md)|5 minutes|  
  
## <a name="supplemental-lessons"></a>Leçons supplémentaires  
Ce didacticiel inclut également des [leçons supplémentaires](http://msdn.microsoft.com/library/2018456f-b4a6-496c-89fb-043c62d8b82e). Les rubriques de cette section ne sont pas requises pour suivre ce didacticiel, mais peuvent être utiles pour mieux comprendre les fonctionnalités de création de modèles tabulaires avancées.  
  
|Leçon|Durée estimée|  
|----------|------------------------------|  
|[Implémentation de la sécurité dynamique à l'aide des filtres de lignes](../analysis-services/supplemental-lesson-implement-dynamic-security-by-using-row-filters.md)|30 minutes|  

  
## <a name="next-step"></a>Étape suivante  
Pour démarrer le didacticiel, passez à la première leçon : [Leçon 1 : Créer un projet de modèle tabulaire](../analysis-services/lesson-1-create-a-new-tabular-model-project.md).  
  
  
  


