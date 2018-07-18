---
title: Bases de données de modèle multidimensionnel (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 08a5d383d9c46b01c52e1fc888c8d692470fd619
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241679"
---
# <a name="multidimensional-model-databases-ssas"></a>Bases de données de modèle multidimensionnel (SSAS)
  Une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est une collection de sources de données, de vues de source de données, de cubes, de dimensions et de rôles. Éventuellement, une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peut inclure des structures pour l'exploration de données et des assemblys personnalisés qui permettent d'ajouter des fonctions définies par l'utilisateur à la base de données.  
  
 Les cubes sont les objets de requête fondamentaux dans Analysis Services. Lorsque vous vous connectez à une base de données Analysis Services via une application cliente, vous vous connectez à un cube dans cette base de données. Une base de données peut contenir plusieurs cubes si vous réutilisez les dimensions, les assemblys, les rôles ou les structures d'exploration de données dans plusieurs contextes.  
  
 Vous pouvez créer et modifier une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] par programmation ou à l'aide de l'une des méthodes interactives suivantes :  
  
-   Déployer un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à partir de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] dans une instance désignée d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Ce processus crée une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , s'il n'existe aucune base de données de ce nom dans cette instance, et instancie les objets désignés dans la base de données nouvellement créée. Si vous utilisez une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], les modifications apportées aux objets dans le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prennent effet uniquement lorsque le projet est déployé dans une instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
-   Créez une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vide dans une instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], puis connectez-vous directement à cette base de données à l’aide de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et créez des objets dans cette dernière (plutôt que dans un projet). Si vous utilisez une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de cette façon, les modifications apportées aux objets prennent effet dans la base de données à laquelle vous vous connectez lorsque vous enregistrez l'objet modifié.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilise l'intégration avec le logiciel de contrôle de code source pour prendre en charge plusieurs développeurs qui utilisent différents objets simultanément dans un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Un développeur peut également interagir directement avec une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , plutôt que dans un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Cependant, les objets d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peuvent devenir désynchronisés avec le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui a été utilisé pour son déploiement. Une fois le déploiement effectué, vous pouvez administrer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous pouvez également apporter certaines modifications à une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], notamment aux partitions et aux rôles. Cela peut également entraîner la désynchronisation des objets d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] avec le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui a été utilisé pour son déploiement.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Attacher et détacher des bases de données Analysis Services](attach-and-detach-analysis-services-databases.md)  
  
 [Sauvegarde et restauration de bases de données Analysis Services](backup-and-restore-of-analysis-services-databases.md)  
  
 [Documenter et générer des scripts pour une base de données Analysis Services](document-and-script-an-analysis-services-database.md)  
  
 [Modifier ou supprimer une base de données Analysis Services](modify-or-delete-an-analysis-services-database.md)  
  
 [Déplacer une base de données Analysis Services](move-an-analysis-services-database.md)  
  
 [Renommer une base de données multidimensionnelle &#40;Analysis Services&#41;](rename-a-multidimensional-database-analysis-services.md)  
  
 [Définir la compatibilité de niveau d’une base de données multidimensionnelle &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md)  
  
 [Définir les propriétés de la base de données multidimensionnelle &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md)  
  
 [Synchroniser des bases de données Analysis Services](synchronize-analysis-services-databases.md)  
  
 [Basculer une base de données Analysis Services entre les modes ReadOnly et ReadWrite](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter en Mode en ligne à une base de données Analysis Services](connect-in-online-mode-to-an-analysis-services-database.md)   
 [Créer un projet Analysis Services &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md)   
 [Interrogation de données multidimensionnelles avec MDX](mdx/querying-multidimensional-data-with-mdx.md)  
  
  
