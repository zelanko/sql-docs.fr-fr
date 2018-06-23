---
title: Création d’une analyse de Services de projet (didacticiel d’exploration de données de base de données) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 784c0401-0358-4117-9c85-4e8220ce71d9
caps.latest.revision: 50
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d650feead984a358d169851fba246215a58b6d34
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312527"
---
# <a name="creating-an-analysis-services-project-basic-data-mining-tutorial"></a>Création d'un projet Analysis Services (Didacticiel sur l'exploration de données de base)
  Chaque [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projet définit les objets dans un seul [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données. Une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] contient plusieurs types d'objets.  
  
-   Modèles multidimensionnels (cubes)  
  
-   Structures et modèles d'exploration de données  
  
-   Objets de prise en charge, tels que des sources de données, des vues de source de données et des assemblys personnalisés  
  
 Notez que vous **n'avez pas** besoin d'un cube pour effectuer l'exploration de données. Si vous devez effectuer l'exploration de données sur un cube existant, vous devez ajouter les modèles d'exploration de données au projet utilisé pour générer le cube. Cependant, dans la plupart des cas, vous créez vos modèles sur des sources de données relationnelles, par exemple un entrepôt de données, et vous obtenez de meilleures performances si un cube n'est pas impliqué.  
  
 Dans ce didacticiel, vous allez utiliser un entrepôt de données relationnelles, [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], comme la source de données. Vous allez déployer tous vos objets d’exploration de données sur un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] base de données nommée `BasicDataMining`, utilisée uniquement pour l’exploration de données.  
  
 Par défaut, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilise le **localhost** instance pour les nouveaux projets. Si vous utilisez une instance nommée ou un serveur différent, vous devez d'abord créer et ouvrir le projet, puis modifier le nom de l'instance.  
  
 Pour plus d’informations sur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projets, consultez [création d’un projet Analysis Services](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md).  
  
### <a name="to-create-an-analysis-services-project"></a>Pour créer un projet Analysis Services  
  
1.  Ouvrir [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis sélectionnez **Projet**.  
  
3.  Vérifiez que l'option **Projets Business Intelligence** est sélectionnée dans le volet **Types de projets** .  
  
4.  Dans le volet **Modèles** , sélectionnez **Projet multidimensionnel et d'exploration de données Analysis Services**.  
  
5.  Dans le **nom** zone, nommez le nouveau projet `BasicDataMining`.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored"></a>Pour modifier les instances de stockage des objets d'exploration de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans le **projet** menu, sélectionnez **propriétés**.  
  
2.  Dans la partie gauche du volet **Pages de propriétés** , sous **Propriétés de configuration**, cliquez sur **Déploiement**.  
  
3.  Dans la partie droite du volet **Pages de propriétés** , sous **Cible**, vérifiez que le nom du **Serveur** est **localhost**. Si vous utilisez une instance différente, tapez le nom de l'instance. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création d’une Source de données &#40;didacticiel d’exploration de données de base de données&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Générer des projets Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)   
 [Créer un projet Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  