---
title: SQL Server 2014 Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
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
ms.openlocfilehash: bceabba9b490be6bc2c51b4fdcce9b6b131eb0ce
ms.sourcegitcommit: 7183735e38dd94aa3b9bab2b73ccab54c916ff86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683476"
---
# <a name="sql-server-2014-analysis-services"></a>SQL Server 2014 Analysis Services

  SQL Server 2014 Analysis Services est un moteur de données analytiques utilisé dans les solutions d’aide à la décision et d’analyse décisionnelle (BI), fournissant des données analytiques pour les rapports d’entreprise et les applications clientes telles qu’Excel, les rapports d’Reporting Services et d’autres outils DÉCISIONNELs tiers. 

## <a name="about-sql-server-analysis-services-documentation"></a>À propos de la documentation SQL Server Analysis Services

La documentation est séparée par la version. Vous êtes actuellement dans la documentation SQL Server 2014 Analysis Services.

- Pour en savoir plus sur SQL Server 2012 et versions antérieures, consultez [SQL Server la documentation sur les versions précédentes](https://docs.microsoft.com/previous-versions/sql/).
- Pour en savoir plus sur SQL Server 2014, consultez la [documentation en ligne de SQL Server 2014](../2014-toc/index.yml)
- Pour en savoir plus sur SQL Server 2016 et versions ultérieures, consultez [la documentation de Microsoft SQL](https://docs.microsoft.com/sql/).
- Pour en savoir plus sur Azure Analysis Services, consultez [Azure Analysis Services documentation](https://docs.microsoft.com/azure/analysis-services/).

## <a name="analysis-services-workflow"></a>Flux de travail Analysis Services

Un flux de travail classique comprend la génération d’un modèle de données OLAP ou tabulaire, le déploiement du modèle en tant que base de données sur une instance de serveur, le traitement de la base de données pour son chargement avec les données, puis l’attribution d’autorisations pour permettre l’accès aux données. Quand il est prêt, le modèle de données polyvalent est accessible depuis n'importe quelle application cliente prenant en charge [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] en tant que source données.  
  
 Pour créer un modèle, utilisez SQL Server Data Tools (consultez [Outils et applications utilisés dans Analysis Services](tools-and-applications-used-in-analysis-services.md)), en choisissant un modèle de projet tabulaire ou multidimensionnel et d’exploration de données. Le modèle de projet contient les dossiers de tous les objets nécessaires dans un modèle. Vous pouvez utiliser des Assistants pour créer tous les éléments de base, tels que des sources de données, des vues de source de données, des dimensions, des cubes et des rôles.  
  
 Les modèles sont remplis avec des données provenant de systèmes de données externes, généralement des entrepôts de données hébergés sur un moteur de base de données relationnelle SQL Server ou Oracle (les modèles tabulaires prennent en charge d'autres types de source de données). Les modèles spécifient les objets de requête, tels que les cubes, mais aussi les dimensions qui peuvent être utilisées dans plusieurs cubes, les calculs et les indicateurs de performance clés qui encapsulent la logique métier, ainsi que les interactions telles que les comportements de navigation et d'extraction.  
  
 Pour utiliser un modèle, il est déployé sur une instance de serveur qui exécute des bases de données dans un mode serveur particulier, ce qui rend les données accessibles aux utilisateurs autorisés qui se connectent par le biais d’Excel ou d’autres applications.  
  
 Vous pouvez installer une instance dans l’un des trois modes serveur suivants :  
  
-   En tant qu'instance tabulaire, avec exécution de modèles tabulaires.  
  
-   En tant qu'instance multidimensionnelle et d'exploration de données, avec exécution de cubes OLAP et de modèles d'exploration de données (il s'agit de la valeur par défaut).  
  
-   En tant que PowerPivot pour SharePoint, avec exécution de modèles de données PowerPivot et Excel dans SharePoint (PowerPivot pour SharePoint est un moteur de données de couche intermédiaire qui charge, interroge, puis actualise les modèles de données hébergés dans SharePoint).  
  
 Même moteur de données ; trois manières de l'utiliser. Notez que les modes serveur sont définis lors de l'installation et ne peuvent pas être modifiés ultérieurement. Vous devez installer une nouvelle instance si vous avez besoin d'un mode différent.  
  
 La documentation fondamentale pour Analysis Services s'articule autour de sections qui correspondent au type de projet que vous créez. Choisissez parmi les liens suivants pour en savoir plus sur chaque mode ou fonctionnalité.  
  
 **Parcourir le contenu par zone**  
 ![Petite icône de dossier de fichiers](../../2014/integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") [comparaison des solutions tabulaires et multidimensionnelles &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![Petite icône de dossier de fichiers](../../2014/integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") [Analysis Services gestion des instances](instances/analysis-services-instance-management.md)  
  
 ![Petite icône de dossier de fichiers](../../2014/integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") [modélisation tabulaire &#40;SSAS tabulaire&#41;](tabular-models/tabular-models-ssas.md)  
  
 ![Petite icône de dossier de fichiers](../../2014/integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") [&#40;la modélisation multidimensionnelle&#41;SSAS](multidimensional-models/multidimensional-models-ssas.md)  
  
 ![Petite icône de dossier de fichiers](../../2014/integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") [exploration de données &#40;SSAS&#41;](data-mining/data-mining-ssas.md)  
  
 ![Petite icône de dossier de fichiers](../../2014/integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") [PowerPivot pour SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]les fonctionnalités varient en fonction de l’édition. Les modèles d'exploration de données et multidimensionnels sont disponibles dans l'édition standard, mais avec moins de fonctionnalités que les éditions supérieures. Les modèles tabulaires et PowerPivot pour SharePoint sont des fonctionnalités Premium et ne sont pas disponibles avec une licence d'édition standard. Pour plus d'informations, consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels de Analysis Services &#40;SSAS&#41;](analysis-services-tutorials-ssas.md)   
 [Installation pour SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Guide du développeur &#40;Analysis Services&#41;](analysis-services-developer-documentation.md)   
 [Centre de ressources SQL Server](https://go.microsoft.com/fwlink/?linkID=219676)   
 [SQLCat.com](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
