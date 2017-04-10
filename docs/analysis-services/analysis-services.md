---
title: "Analysis Services | Microsoft Docs"
ms.date: "03/28/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "Analysis Services, à propos d’Analysis Services - données multidimensionnelles"
  - "SSAS"
  - "Analysis Services"
  - "SQL Server Analysis Services, à propos d’Analysis Services - données multidimensionnelles"
  - "SQL Server Analysis Services"
  - "données multidimensionnelles [Analysis Services]"
  - "SSAS, à propos d’Analysis Services - données multidimensionnelles"
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
caps.latest.revision: 60
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 60
---
# Analysis Services
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] est un moteur de données analytiques en ligne utilisé pour l’analyse marketing et l’aide à la décision. Il fournit des données analytiques employées dans des rapports et des applications clientes comme Power BI, Excel, les rapports Reporting Services et d’autres outils de visualisation des données.  
  
 Dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , un flux de travail typique comprend la création d’un modèle de données multidimensionnel ou tabulaire, le déploiement de ce modèle en tant que base de données vers une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , le traitement de la base de données en vue de son chargement avec les données ou métadonnées qu’elle contient, la configuration de l’actualisation des données, puis l’attribution d’autorisations pour permettre aux utilisateurs finaux d’accéder aux données. Quand il est prêt, ce modèle de données sémantiques polyvalent est accessible depuis n’importe quelle application cliente prenant en charge [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en tant que source de données.  
  
 Les modèles sont remplis avec des données provenant de systèmes de données externes, généralement des entrepôts de données hébergés sur un moteur de base de données relationnelle SQL Server ou Oracle (les modèles tabulaires prennent en charge d'autres types de source de données). Les modèles spécifient les objets de requête, tels que les cubes, mais aussi les dimensions qui peuvent être utilisées dans plusieurs cubes, les calculs et les indicateurs de performance clés qui encapsulent la logique métier, ainsi que les interactions telles que les comportements de navigation et d'extraction.  
 
## <a name="analysis-services-on-premises-and-in-the-cloud"></a>Analysis Services en local et dans le cloud
Analysis Services est désormais disponible dans le cloud comme un service Azure. Actuellement en préversion, Azure Analysis Services prend en charge les modèles tabulaires au niveau de compatibilité 1200. DirectQuery, les partitions, la sécurité de niveau ligne, les relations bidirectionnelles et les traductions sont toutes prises en charge. Pour en savoir plus et effectuer un essai gratuit, consultez [Azure Analysis Services](https://azure.microsoft.com/en-us/services/analysis-services/). 
  
## <a name="server-mode"></a>Mode serveur  
 Lors de l’installation d’Analysis Services à l’aide du programme d’installation de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] , vous spécifiez un mode serveur pour cette instance lors de la configuration.  Chaque mode inclut différentes fonctionnalités propres à une solution Analysis Services particulière.  
  
-   **Mode multidimensionnel et d’exploration de données** : implémente les constructions de modélisation OLAP (cubes, dimensions, mesures).  
  
-   **Mode tabulaire** : implémente les constructions de modélisation de données relationnelles en mémoire (modèle, tables, colonnes).  
  
     Les modèles tabulaires peuvent être créés au niveau de compatibilité par défaut 1200, avec les dernières fonctionnalités, ou au niveau de compatibilité 1103 plus ancien. Il existe des différences significatives entre les niveaux de compatibilité. Pour plus d’informations sur la comparaison des niveaux, consultez [Niveau de compatibilité pour les modèles tabulaires dans Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).  
  
-   **Mode Power Pivot** : implémente les modèles de données [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] et Excel dans SharePoint ([!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour SharePoint est un moteur de données de couche intermédiaire qui charge, interroge, puis actualise les modèles de données hébergés dans SharePoint).  
  
 Une instance unique peut être configurée avec un seul mode et ne peut pas être modifiée par la suite.  Vous pouvez installer plusieurs instances avec des modes différents sur le même serveur, mais vous devrez exécuter le programme d’installation et spécifier les paramètres de configuration pour chaque instance.  
  
 Les fonctionnalités [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] varient en fonction de l’édition. Pour plus d’informations, consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../sql-server/fonctionnalités-prises-en-charge-par-les-éditions-de-sql-server-2016.md) 
  
## <a name="authoring-solutions"></a>Solutions de création  
 Pour créer un modèle, vous utilisez SQL Server Data Tools (consultez [Outils et applications utilisés dans Analysis Services](../analysis-services/tools-and-applications-used-in-analysis-services.md)), en choisissant un modèle de projet d’exploration de données et un modèle tabulaire ou multidimensionnel. Le modèle de projet contient les dossiers de tous les objets nécessaires dans un modèle. Les Assistants aident à créer un grand nombre des éléments de base, tels que des sources de données, des vues de sources de données, des dimensions, des cubes et des rôles.  
  
## <a name="documentation-by-area"></a>Documentation par domaine  
La documentation pour Analysis Services s’articule autour de sections qui correspondent au type de projet que vous créez. Choisissez parmi les liens suivants pour en savoir plus sur chaque mode ou fonctionnalité.  
   
 ![Petite icône de dossier de fichiers](../analysis-services/media/filefolder-small.png "Petite icône de dossier de fichiers") [Nouveautés](../analysis-services/what-s-new-in-analysis-services.md)  
  
 ![Petite icône de dossier de fichiers](../analysis-services/media/filefolder-small.png "Petite icône de dossier de fichiers") [Comparaison des solutions tabulaires et multidimensionnelles](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![Petite icône de dossier de fichiers](../analysis-services/media/filefolder-small.png "Petite icône de dossier de fichiers") [Modèles tabulaires](../analysis-services/tabular-models/tabular-models-ssas.md)  
  
 ![Petite icône de dossier de fichiers](../analysis-services/media/filefolder-small.png "Petite icône de dossier de fichiers") [Modèles multidimensionnels](../analysis-services/multidimensional-models/multidimensional-models-ssas.md)  
  
 ![Petite icône de dossier de fichiers](../analysis-services/media/filefolder-small.png "Petite icône de dossier de fichiers") [Exploration de données](../analysis-services/data-mining/data-mining-ssas.md)  
  
 ![Petite icône de dossier de fichiers](../analysis-services/media/filefolder-small.png "Petite icône de dossier de fichiers") [PowerPivot pour SharePoint](../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
 ![Petite icône de dossier de fichiers](../analysis-services/media/filefolder-small.png "Petite icône de dossier de fichiers") [Gestion d’instances Analysis Services](../analysis-services/instances/analysis-services-instance-management.md)  
   
 ![Petite icône de dossier de fichiers](../analysis-services/media/filefolder-small.png "Petite icône de dossier de fichiers") [Didacticiels sur Analysis Services](../analysis-services/analysis-services-tutorials-ssas.md)  
  
![Petite icône de dossier de fichiers](../analysis-services/media/filefolder-small.png "Petite icône de dossier de fichiers") [Documentation du développeur Analysis Services](https://msdn.microsoft.com/library/bb500153(SQL.130).aspx)  
 
![Petite icône de dossier de fichiers](../analysis-services/media/filefolder-small.png "Petite icône de dossier de fichiers") [Références techniques (SSAS)](../analysis-services/powershell/technical-reference-ssas.md)