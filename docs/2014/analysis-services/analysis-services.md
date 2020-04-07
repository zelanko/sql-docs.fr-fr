---
title: SqL Server 2014 Services d’analyse (fr) Microsoft Docs
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, about Analysis Services - Multidimensional Data
- SSAS
- Analysis Services
- SQL Server Analysis Services, about Analysis Services - Multidimensional Data
- SQL Server Analysis Services
- multidimensional data [Analysis Services]
- SSAS, about Analysis Services - Multidimensional Data
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 986356e6ebf7697bf0b425553f6803659a0fc5cb
ms.sourcegitcommit: 8f99d15c5b23d9f3c08a77e2b8bea5772f570493
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80760302"
---
# <a name="sql-server-2014-analysis-services"></a>SQL Server 2014 Analysis Services

  SQL Server 2014 Analysis Services est un moteur de données analytiques utilisé dans les solutions de support décisionnel et d’intelligence d’affaires (BI), fournissant les données analytiques pour les rapports d’affaires et les applications des clients tels que Excel, Reporting Services reports, et d’autres outils de TYPE tiers. 

## <a name="about-sql-server-analysis-services-documentation"></a>À propos de sqL Server Analysis Services documentation

La documentation est séparée par version. Vous êtes actuellement dans la documentation SQL Server 2014 Analysis Services.

- Pour en savoir plus sur SQL Server 2012 et plus tôt, voir [SQL Server versions précédentes documentation](https://docs.microsoft.com/previous-versions/sql/).
- Pour en savoir plus sur SQL Server 2014, voir [Books Online pour SQL Server 2014](../2014-toc/index.yml)
- Pour en savoir plus sur SQL Server 2016 et plus tard, consultez [la documentation des Services d’analyse](https://docs.microsoft.com/analysis-services/).
- Pour en savoir plus sur azure Analysis Services, voir [Documentation azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/).

## <a name="analysis-services-workflow"></a>Flux de travail des Services d’analyse

Un flux de travail typique comprend la construction d’un OLAP ou d’un modèle de données tabulaire, le déploiement du modèle comme base de données dans une instance de serveur, le traitement de la base de données pour le charger avec des données, puis assigner des autorisations pour permettre l’accès aux données. Quand il est prêt, le modèle de données polyvalent est accessible depuis n'importe quelle application cliente prenant en charge [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en tant que source données.  
  
 Pour créer un modèle, utilisez SQL Server Data Tools (voir [outils et applications utilisés dans les services d’analyse),](tools-and-applications-used-in-analysis-services.md)en choisissant un modèle de projet Tabular ou Multidimensionnel et Data Mining. Le modèle de projet contient les dossiers de tous les objets nécessaires dans un modèle. Vous pouvez utiliser des Assistants pour créer tous les éléments de base, tels que des sources de données, des vues de source de données, des dimensions, des cubes et des rôles.  
  
 Les modèles sont remplis avec des données provenant de systèmes de données externes, généralement des entrepôts de données hébergés sur un moteur de base de données relationnelle SQL Server ou Oracle (les modèles tabulaires prennent en charge d'autres types de source de données). Les modèles spécifient les objets de requête, tels que les cubes, mais aussi les dimensions qui peuvent être utilisées dans plusieurs cubes, les calculs et les indicateurs de performance clés qui encapsulent la logique métier, ainsi que les interactions telles que les comportements de navigation et d'extraction.  
  
 Pour utiliser un modèle, il est déployé dans une instance serveur qui exécute des bases de données dans un mode serveur particulier, ce qui rend les données disponibles pour les utilisateurs autorisés qui se connectent via Excel ou d’autres applications.  
  
 Vous pouvez installer une instance dans l’un des trois modes serveur :  
  
-   En tant qu'instance tabulaire, avec exécution de modèles tabulaires.  
  
-   En tant qu'instance multidimensionnelle et d'exploration de données, avec exécution de cubes OLAP et de modèles d'exploration de données (il s'agit de la valeur par défaut).  
  
-   En tant que PowerPivot pour SharePoint, avec exécution de modèles de données PowerPivot et Excel dans SharePoint (PowerPivot pour SharePoint est un moteur de données de couche intermédiaire qui charge, interroge, puis actualise les modèles de données hébergés dans SharePoint).  
  
 Même moteur de données ; trois manières de l'utiliser. Notez que les modes serveur sont définis lors de l'installation et ne peuvent pas être modifiés ultérieurement. Vous devez installer une nouvelle instance si vous avez besoin d'un mode différent.  
  
 La documentation fondamentale pour Analysis Services s'articule autour de sections qui correspondent au type de projet que vous créez. Choisissez parmi les liens suivants pour en savoir plus sur chaque mode ou fonctionnalité.  
  
 **Parcourir le contenu par zone**  
 ![Icône de dossier de petit fichier](../../2014/integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") [comparant les solutions tabulaires et multidimensionnelles &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 Gestion des exemples de services ![d’analyse d’icônes de](../../2014/integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") [dossiers](instances/analysis-services-instance-management.md)  
  
 Petite modélisation tabulaire ![d’icône de dossier](../../2014/integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") [de fichier &#40;&#41;tabulaire SSAS](tabular-models/tabular-models-ssas.md)  
  
 Petite modélisation multidimensionnelle ![d’icône de dossier](../../2014/integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") [&#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)  
  
 ![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") [Data Mining &#40;SSAS&#41;](data-mining/data-mining-ssas.md)  
  
 ![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") [PowerPivot pour SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
> [!NOTE]  
>  Les fonctionnalités [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] varient en fonction de l’édition. Les modèles d'exploration de données et multidimensionnels sont disponibles dans l'édition standard, mais avec moins de fonctionnalités que les éditions supérieures. Les modèles tabulaires et PowerPivot pour SharePoint sont des fonctionnalités Premium et ne sont pas disponibles avec une licence d'édition standard. Pour plus d’informations, voir [Caractéristiques Soutenues par les Editions de SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Services d’analyse Tutorials &#40;SSAS&#41;](analysis-services-tutorials-ssas.md)   
 [Installation pour SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Guide des &#40;Services d’analyse des développeurs&#41;](analysis-services-developer-documentation.md)   
 [Centre de ressources pour les serveurs SQL](https://go.microsoft.com/fwlink/?linkID=219676)   
 [SQLCat.com](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
