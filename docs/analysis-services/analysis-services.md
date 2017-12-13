---
title: Analysis Services | Documents Microsoft
ms.date: 05/11/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.custom: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- Analysis Services, about Analysis Services - Multidimensional Data
- SSAS
- Analysis Services
- SQL Server Analysis Services, about Analysis Services - Multidimensional Data
- SQL Server Analysis Services
- multidimensional data [Analysis Services]
- SSAS, about Analysis Services - Multidimensional Data
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
caps.latest.revision: "60"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: d31d430fdaf5276b52a3f90efacf4a9a56576a35
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="what-is-analysis-services"></a>Nouveautés d’Analysis Services ?
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]Analysis Services est un moteur de données analytiques utilisé de la prise de décision et analytique d’entreprise, en fournissant les données analytiques pour les rapports d’entreprise et les applications clientes, telles que Power BI, Excel, des rapports Reporting Services et d’autres outils de visualisation de données.  
  
 Un flux de travail typique comprend la création d’un modèle de données multidimensionnelle ou tabulaire, le déploiement du modèle en tant qu’une base de données à une instance de serveur local SQL Server Analysis Services ou Azure Analysis Services, configurer le traitement des données périodique et affectation d’autorisations d’accès aux données par les utilisateurs finaux. Lorsqu’il est prêt, votre modèle de données sémantique accessibles par toute application cliente prenant en charge d’Analysis Services comme source de données.  
 
## <a name="analysis-services-on-premises-and-in-the-cloud"></a>Analysis Services en local et dans le cloud
Analysis Services est désormais disponible dans le cloud comme un service Azure. Azure Analysis Services prend en charge les modèles tabulaires aux niveaux de compatibilité 1200 et supérieurs. DirectQuery, les partitions, la sécurité de niveau ligne, les relations bidirectionnelles et les traductions sont toutes prises en charge. Pour en savoir plus et effectuer un essai gratuit, consultez [Azure Analysis Services](https://azure.microsoft.com/en-us/services/analysis-services/). 
  
## <a name="server-mode"></a>Mode serveur  
 Lorsque vous installez Analysis Services à l’aide du programme d’installation de SQL Server, lors de la configuration, vous spécifiez un mode de serveur pour cette instance.  Chaque mode inclut différentes fonctionnalités propres à une solution Analysis Services particulière.   
  
-   **En Mode tabulaire** - les données relationnelles en mémoire implémentent constructions (modèle, tables, colonnes, mesures, hiérarchies) de modélisation.  

-   **Mode multidimensionnel et d’exploration de données** : implémente les constructions de modélisation OLAP (cubes, dimensions, mesures). 

-   **Power Pivot Mode** -modèles de données implémentent PowerPivot et Excel dans SharePoint (PowerPivot pour SharePoint est un moteur de données de couche intermédiaire qui charge, interroge et actualise les modèles de données hébergés dans SharePoint).  
  
 Une instance unique peut être configurée avec un seul mode et ne peut pas être modifiée par la suite.  Vous pouvez installer plusieurs instances avec des modes différents sur le même serveur, mais vous devrez exécuter le programme d’installation et spécifier les paramètres de configuration pour chaque instance. Pour plus d’informations et une comparaison des différentes fonctionnalités offertes par chacun des modes, consultez [comparaison sous forme de tableau et les Solutions multidimensionnelles](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md).
  
## <a name="authoring-and-managing-solutions"></a>Création et gestion des solutions  
 Pour créer un modèle et déployez-le sur un serveur, vous utilisez SQL Server Data Tools, en choisissant le modèle de projet soit un tabulaire ou multidimensionnel et d’exploration de données. Le modèle de projet contient les dossiers de tous les objets nécessaires dans un modèle. Les concepteurs et les Assistants vous aident à que créer de nombreux éléments de base telles que la connexion à des rôles, des relations, des mesures et des sources de données. Une fois votre base de données model est déployé sur un serveur, vous utilisez SQL Server Management Studio (SSMS) pour configurer le traitement des données, de surveiller et de gérer votre serveur et les bases de données. Pour plus d’informations, consultez [outils et applications utilisés dans Analysis Services](../analysis-services/tools-and-applications-used-in-analysis-services.md). 
  
## <a name="documentation-by-area"></a>Documentation par domaine  
En général, la documentation Azure Analysis Services est incluse dans la documentation sur Azure. Et documentation pour SQL Server Analysis Services est incluse dans la documentation de SQL. Toutefois, au moins pour les modèles tabulaires, comment créer et déployer vos projets est similaire, quelle que soit la plate-forme vous utilisez.  
   
*  [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/)
*  [Nouveautés de SQL Server Analysis Services](../analysis-services/what-s-new-in-analysis-services.md)   
*  [Comparaison des Solutions multidimensionnelles et tabulaires](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
*  [Modèles tabulaires](../analysis-services/tabular-models/tabular-models-ssas.md)  
*  [Modèles multidimensionnels](../analysis-services/multidimensional-models/multidimensional-models-ssas.md)  
*  [Exploration de données](../analysis-services/data-mining/data-mining-ssas.md)  
*  [PowerPivot pour SharePoint](../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
*  [Gestion d’instances](../analysis-services/instances/analysis-services-instance-management.md)    
*  [Didacticiels](../analysis-services/analysis-services-tutorials-ssas.md)   
*  [Documentation pour développeurs](https://msdn.microsoft.com/library/bb500153(SQL.130).aspx)  
*  [Informations techniques de référence (SSAS)](../analysis-services/powershell/technical-reference-ssas.md)
