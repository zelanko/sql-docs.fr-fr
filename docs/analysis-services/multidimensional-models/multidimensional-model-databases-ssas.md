---
title: "Bases de données de modèle multidimensionnel (SSAS) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [Analysis Services], databases
- SQL Server Analysis Services, databases
- SSAS, databases
- Analysis Services, databases
- databases [Analysis Services], designing
- Business Intelligence Development Studio, databases [Analysis Services]
- databases [Analysis Services]
ms.assetid: 78b2f22a-b7bd-4a2b-b6fc-0bff4d2b3168
caps.latest.revision: 55
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2b9b4fa79c4ef7a37158c1fbeea32a80c56effa2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="multidimensional-model-databases-ssas"></a>Bases de données de modèle multidimensionnel (SSAS)
  Une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est une collection de sources de données, de vues de source de données, de cubes, de dimensions et de rôles. Éventuellement, une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peut inclure des structures pour l'exploration de données et des assemblys personnalisés qui permettent d'ajouter des fonctions définies par l'utilisateur à la base de données.  
  
 Les cubes sont les objets de requête fondamentaux dans Analysis Services. Lorsque vous vous connectez à une base de données Analysis Services via une application cliente, vous vous connectez à un cube dans cette base de données. Une base de données peut contenir plusieurs cubes si vous réutilisez les dimensions, les assemblys, les rôles ou les structures d'exploration de données dans plusieurs contextes.  
  
 Vous pouvez créer et modifier une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] par programmation ou à l'aide de l'une des méthodes interactives suivantes :  
  
-   Déployer un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à partir de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] dans une instance désignée d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Ce processus crée une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , s'il n'existe aucune base de données de ce nom dans cette instance, et instancie les objets désignés dans la base de données nouvellement créée. Si vous utilisez une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], les modifications apportées aux objets dans le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prennent effet uniquement lorsque le projet est déployé dans une instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
-   Créez une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vide dans une instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], puis connectez-vous directement à cette base de données à l’aide de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et créez des objets dans cette dernière (plutôt que dans un projet). Si vous utilisez une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de cette façon, les modifications apportées aux objets prennent effet dans la base de données à laquelle vous vous connectez lorsque vous enregistrez l'objet modifié.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilise l'intégration avec le logiciel de contrôle de code source pour prendre en charge plusieurs développeurs qui utilisent différents objets simultanément dans un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Un développeur peut également interagir directement avec une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , plutôt que dans un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Cependant, les objets d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peuvent devenir désynchronisés avec le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui a été utilisé pour son déploiement. Une fois le déploiement effectué, vous pouvez administrer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous pouvez également apporter certaines modifications à une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], notamment aux partitions et aux rôles. Cela peut également entraîner la désynchronisation des objets d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] avec le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui a été utilisé pour son déploiement.  
  
## <a name="related-tasks"></a>Tâches associées  
 [Attacher et détacher des bases de données Analysis Services](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
 [Sauvegarde et restauration de bases de données Analysis Services](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
 [Documenter et générer des scripts pour une base de données Analysis Services](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md)  
  
 [Modifier ou supprimer une base de données Analysis Services](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)  
  
 [Déplacer une base de données Analysis Services](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)  
  
 [Renommer une base de données multidimensionnelle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/rename-a-multidimensional-database-analysis-services.md)  
  
 [Niveau de compatibilité d’une base de données multidimensionnelle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)  
  
 [Définir les propriétés de base de données multidimensionnelle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/set-multidimensional-database-properties-analysis-services.md)  
  
 [Synchroniser des base de données Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)  
  
 [Basculer une base de données Analysis Services entre les modes ReadOnly et ReadWrite](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion en mode en ligne à une base de données Analysis Services](../../analysis-services/multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md)   
 [Créer un projet Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)   
 [Interrogation de données multidimensionnelles avec MDX](../../analysis-services/multidimensional-models/mdx/querying-multidimensional-data-with-mdx.md)  
  
  

