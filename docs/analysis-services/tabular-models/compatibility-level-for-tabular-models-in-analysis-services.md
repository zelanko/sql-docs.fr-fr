---
title: "Niveau de compatibilit&#233; pour les mod&#232;les tabulaires dans Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.versioncompat.f1"
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
caps.latest.revision: 27
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 27
---
# Niveau de compatibilit&#233; pour les mod&#232;les tabulaires dans Analysis Services
  Le *niveau de compatibilité* d’un modèle ou d’une base de données fait référence à un ensemble de comportements spécifiques à chaque version dans le moteur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Vous pouvez créer des modèles à n’importe quel niveau de compatibilité pris en charge afin d’obtenir les comportements d'une version particulière. Par exemple, les métadonnées d'objets DirectQuery et tabulaires ont des implémentations différentes en fonction du niveau de compatibilité attribué.  
  
 **SQL Server 2016 RTM (1200)**, ou niveau de compatibilité 1200 pour faire court, est une nouveauté de SQL Server 2016 qui ne s’applique qu’aux modèles tabulaires.  Les modèles tabulaires au niveau de compatibilité 1200 s’exécuteront uniquement sur une instance tabulaire [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] .  
  
 Pour créer ou mettre à niveau un modèle tabulaire, utilisez SQL Server Data Tools (SSDT) et définissez la propriété **Niveau de compatibilité** pendant la création du projet ou dans le fichier **model.bim** une fois le projet créé.  
  
> [!NOTE]  
>  Les modèles multidimensionnels suivent un chemin d'accès de version indépendante en termes de niveaux de compatibilité. Lorsque les numéros sont identiques, comme c'est le cas avec 1103, il s’agit d’une coïncidence. Pour plus d’informations, consultez [Niveau de compatibilité d’une base de données multidimensionnelle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md).  
  
## Niveaux de compatibilité pris en charge pour les bases de données d’un modèle tabulaire  
 Analysis Services prend en charge les niveaux de compatibilité suivants, applicables à la fois aux modèles et aux bases de données.  La version de l'outil permettant de créer un modèle détermine si des niveaux de compatibilité plus élevés sont disponibles.  
  
||||  
|-|-|-|  
|niveau de compatibilité|Version du serveur|Version de l’outil de modélisation|  
|1200|S'exécute uniquement sur les instances SQL Server 2016|[SQL Server Data Tools pour Visual Studio 2015 uniquement](http://go.microsoft.com/fwlink/?LinkID=690931) <sup>1</sup><br /><br /> [What's New in Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md) décrit les fonctionnalités disponibles à ce niveau.|  
|1103|SQL Server 2016<br /><br /> SQL Server 2014<br /><br /> SQL Server 2012 SP1|[SQL Server Data Tools pour Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkID=690931) <sup>2</sup><br /><br /> [SQL Server Data Tools for Business Intelligence (Visual Studio 2013)](https://www.microsoft.com/en-us/download/details.aspx?id=42313)<br /><br /> [SQL Server Data Tools for Business Intelligence (Visual Studio 2012)](http://www.microsoft.com/en-us/download/details.aspx?id=36843)|  
|1100|SQL Server 2016<br /><br /> SQL Server 2014<br /><br /> SQL Server 2012 SP1<br /><br /> SQL Server 2012|[SQL Server Data Tools pour Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkID=690931) <sup>1</sup><br /><br /> [SQL Server Data Tools for Business Intelligence (Visual Studio 2013)](https://www.microsoft.com/en-us/download/details.aspx?id=42313)<br /><br /> [SQL Server Data Tools for Business Intelligence (Visual Studio 2012)](http://www.microsoft.com/en-us/download/details.aspx?id=36843)<br /><br /> Business Intelligence Development Studio (s'exécute dans le shell Visual Studio 2010 et s’installe via le programme d'installation SQL Server)|  
  
 <sup>1</sup> Vous pouvez utiliser SQL Server Data Tools pour Visual Studio 2015 afin de déployer un modèle tabulaire 1100 ou 1103 sur des versions antérieures d'Analysis Services.  
  
 <sup>2</sup> Les niveaux de compatibilité 1100, 1103 et 1200 sont tous valides pour les projets de modèles tabulaires dans SQL Server Data Tools pour Visual Studio 2015, mais vous pouvez uniquement déployer et exécuter un modèle 1200 sur une instance SQL Server 2016 d'Analysis Services.  
  
## Définir le niveau de compatibilité lors de la création ou de la mise à niveau d'un projet de modèle tabulaire dans SSDT  
 Quand vous créez un projet de modèle tabulaire dans SQL Server Data Tools (SSDT), dans la boîte de dialogue **Options de nouveau projet tabulaire**, spécifiez le niveau de compatibilité.  
  
 ![ssas_tabularproject_compat1200](../../analysis-services/tabular-models/media/ssas-tabularproject-compat1200.jpg "ssas_tabularproject_compat1200")  
  
 Vous pouvez également spécifier un niveau de compatibilité par défaut en sélectionnant l'option **Ne plus afficher ce message** . Tous les projets suivants utiliseront le niveau de compatibilité que vous avez spécifié. Vous pouvez modifier le niveau de compatibilité par défaut dans SSDT sous **Outils** > **Options**.  
  
 Pour mettre à niveau un projet de modèle tabulaire, définissez la propriété **Niveau de compatibilité** dans la fenêtre **Propriétés** du modèle sur **SQL Server 2016 RTM (1200)**.  Consultez la rubrique [Upgrade Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md) (éventuellement en anglais) pour plus d'informations.  
  
> [!NOTE]  
>  Vous pouvez créer un modèle tabulaire en vous basant sur un classeur Power Pivot importé. Par défaut, Power BI Desktop crée automatiquement des modèles tabulaires au niveau de compatibilité 1200. Cependant, les versions antérieures de classeurs Power Pivot peuvent être au niveau 1100. Lorsque vous utilisez un classeur plus ancien, n'oubliez pas de modifier la propriété **Niveau de compatibilité** pour la mettre à niveau.  
  
## Vérifier le niveau de compatibilité d'une base de données dans SSMS  
 Dans SSMS, cliquez avec le bouton droit sur le nom de la base de données, puis choisissez **Propriétés** > **Niveau de compatibilité**.  
  
## Vérifier le niveau de compatibilité pris en charge pour un serveur dans SSMS  
 Dans SSMS, cliquez avec le bouton droit sur le nom du serveur, puis choisissez **Propriétés** > **Niveau de compatibilité pris en charge**.  
  
 Cette propriété spécifie le plus haut niveau de compatibilité de la base de données qui s'exécutera sur le serveur.  Le niveau de compatibilité pris en charge est en lecture seule et ne peut pas être modifié.  
  
## Voir aussi  
 [Niveau de compatibilité d’une base de données multidimensionnelle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Nouveautés d’Analysis Services](../../analysis-services/what-s-new-in-analysis-services.md)   
 [Importer à partir de Power Pivot &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)   
 [Créer un projet de modèle tabulaire &#40;Analysis Services&#41;](../../analysis-services/tabular-models/create-a-new-tabular-model-project-analysis-services.md)  
  
  