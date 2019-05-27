---
title: Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
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
ms.openlocfilehash: 241bb57ffd0ce05f1daa289cc7ae78c365a27cc9
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66062338"
---
# <a name="analysis-services"></a>Analysis Services
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] est un moteur de données analytiques en ligne utilisé dans des solutions de décisionnel (BI) et d'aide à la décision. Il fournit des données analytiques utilisées dans des rapports et des applications clientes tels qu'Excel, les rapports Reporting Services et d'autres outils BI tiers. Dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], un flux de travail typique comprend la création d'un modèle de données OLAP ou tabulaires, le déploiement de ce modèle en tant que base de données vers une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], le traitement de la base de données en vue de son chargement et des données qu'elle contient, puis l'attribution d'autorisations d'accès aux données. Quand il est prêt, le modèle de données polyvalent est accessible depuis n'importe quelle application cliente prenant en charge [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en tant que source données.  
  
 Pour créer un modèle, utilisez SQL Server Data Tools (consultez [outils et applications utilisés dans Analysis Services](tools-and-applications-used-in-analysis-services.md)), en choisissant un modèle de projet tabulaire ou multidimensionnel et exploration de données. Le modèle de projet contient les dossiers de tous les objets nécessaires dans un modèle. Vous pouvez utiliser des Assistants pour créer tous les éléments de base, tels que des sources de données, des vues de source de données, des dimensions, des cubes et des rôles.  
  
 Les modèles sont remplis avec des données provenant de systèmes de données externes, généralement des entrepôts de données hébergés sur un moteur de base de données relationnelle SQL Server ou Oracle (les modèles tabulaires prennent en charge d'autres types de source de données). Les modèles spécifient les objets de requête, tels que les cubes, mais aussi les dimensions qui peuvent être utilisées dans plusieurs cubes, les calculs et les indicateurs de performance clés qui encapsulent la logique métier, ainsi que les interactions telles que les comportements de navigation et d'extraction.  
  
 Pour utiliser un modèle, celui-ci doit être déployé sur une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui exécute des bases de données dans un mode serveur particulier, ce qui permet de mettre les données à la disposition des utilisateurs autorisés qui se connectent via Excel ou d'autres applications.  
  
 Vous pouvez installer une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans l'un des trois modes serveur :  
  
-   En tant qu'instance tabulaire, avec exécution de modèles tabulaires.  
  
-   En tant qu'instance multidimensionnelle et d'exploration de données, avec exécution de cubes OLAP et de modèles d'exploration de données (il s'agit de la valeur par défaut).  
  
-   En tant que PowerPivot pour SharePoint, avec exécution de modèles de données PowerPivot et Excel dans SharePoint (PowerPivot pour SharePoint est un moteur de données de couche intermédiaire qui charge, interroge, puis actualise les modèles de données hébergés dans SharePoint).  
  
 Même moteur de données ; trois manières de l'utiliser. Notez que les modes serveur sont définis lors de l'installation et ne peuvent pas être modifiés ultérieurement. Vous devez installer une nouvelle instance si vous avez besoin d'un mode différent.  
  
 La documentation fondamentale pour Analysis Services s'articule autour de sections qui correspondent au type de projet que vous créez. Choisissez parmi les liens suivants pour en savoir plus sur chaque mode ou fonctionnalité.  
  
 **Parcourir le contenu par domaine**  
 ![Icône de dossier petit fichier](../../2014/integration-services/media/filefolder-small.gif "icône dossier de petits fichiers") [comparaison des Solutions tabulaires et multidimensionnelles &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![Icône de dossier petit fichier](../../2014/integration-services/media/filefolder-small.gif "icône dossier de petits fichiers") [gestion d’Instance Analysis Services](instances/analysis-services-instance-management.md)  
  
 ![Icône de dossier petit fichier](../../2014/integration-services/media/filefolder-small.gif "icône dossier de petits fichiers") [modélisation tabulaire &#40;SSAS tabulaire&#41;](tabular-models/tabular-models-ssas.md)  
  
 ![Icône de dossier petit fichier](../../2014/integration-services/media/filefolder-small.gif "icône dossier de petits fichiers") [modélisation multidimensionnelle &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)  
  
 ![Icône de dossier petit fichier](../../2014/integration-services/media/filefolder-small.gif "icône dossier de petits fichiers") [exploration de données &#40;SSAS&#41;](data-mining/data-mining-ssas.md)  
  
 ![Icône de dossier petit fichier](../../2014/integration-services/media/filefolder-small.gif "icône dossier de petits fichiers") [PowerPivot pour SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
> [!NOTE]  
>  Les fonctionnalités [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] varient en fonction de l’édition. Les modèles d'exploration de données et multidimensionnels sont disponibles dans l'édition standard, mais avec moins de fonctionnalités que les éditions supérieures. Les modèles tabulaires et PowerPivot pour SharePoint sont des fonctionnalités Premium et ne sont pas disponibles avec une licence d'édition standard. Pour plus d'informations, consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels sur Analysis Services &#40;SSAS&#41;](analysis-services-tutorials-ssas.md)   
 [Installation de SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Guide du développeur &#40;Analysis Services&#41;](analysis-services-developer-documentation.md)   
 [Centre de ressources SQL Server](https://go.microsoft.com/fwlink/?linkID=219676)   
 [SQLCat.com](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
