---
title: Création d’une analyse de projet (didacticiel d’exploration de données de base) Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 784c0401-0358-4117-9c85-4e8220ce71d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ee6c1a8b765843304d25f1e2ad485ede2badcba4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018900"
---
# <a name="creating-an-analysis-services-project-basic-data-mining-tutorial"></a>Création d'un projet Analysis Services (Didacticiel sur l'exploration de données de base)
  Chaque projet [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] définit les objets présents dans une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unique. Une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] contient plusieurs types d'objets.  
  
-   Modèles multidimensionnels (cubes)  
  
-   Structures et modèles d'exploration de données  
  
-   Objets de prise en charge, tels que des sources de données, des vues de source de données et des assemblys personnalisés  
  
 Notez que vous **n'avez pas** besoin d'un cube pour effectuer l'exploration de données. Si vous devez effectuer l'exploration de données sur un cube existant, vous devez ajouter les modèles d'exploration de données au projet utilisé pour générer le cube. Cependant, dans la plupart des cas, vous créez vos modèles sur des sources de données relationnelles, par exemple un entrepôt de données, et vous obtenez de meilleures performances si un cube n'est pas impliqué.  
  
 Dans ce didacticiel vous allez utiliser un entrepôt de données relationnelles, [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], comme source de données. Vous allez déployer tous vos objets d'exploration de données sur une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nommée `BasicDataMining`, utilisée uniquement pour l'exploration de données.  
  
 Par défaut, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise l'instance **localhost** pour les nouveaux projets. Si vous utilisez une instance nommée ou un serveur différent, vous devez d'abord créer et ouvrir le projet, puis modifier le nom de l'instance.  
  
 Pour plus d'informations sur les projets [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , consultez [Creating an Analysis Services Project](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md).  
  
### <a name="to-create-an-analysis-services-project"></a>Pour créer un projet Analysis Services  
  
1.  Ouvrez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis sélectionnez **Projet**.  
  
3.  Vérifiez que l'option **Projets Business Intelligence** est sélectionnée dans le volet **Types de projets** .  
  
4.  Dans le volet **Modèles** , sélectionnez **Projet multidimensionnel et d'exploration de données Analysis Services**.  
  
5.  Dans le **nom** boîte, nommez le nouveau projet `BasicDataMining`.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored"></a>Pour modifier les instances de stockage des objets d'exploration de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans le menu **Projet** , sélectionnez **Propriétés**.  
  
2.  Dans la partie gauche du volet **Pages de propriétés** , sous **Propriétés de configuration**, cliquez sur **Déploiement**.  
  
3.  Dans la partie droite du volet **Pages de propriétés** , sous **Cible**, vérifiez que le nom du **Serveur** est **localhost**. Si vous utilisez une instance différente, tapez le nom de l'instance. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création d’une Source de données &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Générer des projets Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)   
 [Créer un projet Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  
