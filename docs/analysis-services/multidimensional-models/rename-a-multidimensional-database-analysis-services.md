---
title: "Renommer une base de donn&#233;es multidimensionnelle (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "bases de données, affectation d'un nouveau nom"
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
caps.latest.revision: 20
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 20
---
# Renommer une base de donn&#233;es multidimensionnelle (Analysis Services)
  La façon dont vous modifiez le nom d'une base de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diffère selon le mode de connexion à la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Pour modifier le nom d'une base de données existante, vous devez vous connecter à l'aide du mode en ligne. Pour modifier le nom de la base de données dans laquelle des objets d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] seront instanciés, vous devez vous connecter à l'aide du mode projet.  
  
### Pour modifier le nom de la base de données en mode en ligne  
  
1.  Connectez-vous directement à la base de données [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]à l'aide de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur la base de données, puis cliquez sur **Modifier la base de données**.  
  
3.  Dans la zone de texte **Nom de la base de données** , modifiez le nom de la base de données.  
  
4.  Dans la barre d'outils, cliquez sur **Enregistrer** ou sur **Enregistrer tout** , ou, dans le menu **Fichier** , cliquez sur **Enregistrer les éléments sélectionnés** ou sur **Enregistrer tout** , ou, fermez le **Concepteur de bases de données** , puis cliquez sur **Enregistrer** à l'invite.  
  
     Le nom de la base de données est mis à jour dans l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et l'objet base de données est actualisé dans l'Explorateur de solutions.  
  
### Pour modifier le nom de la base de données en mode projet  
  
1.  Ouvrez le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Pages de propriétés** sous **Propriétés de configuration** , sélectionnez **Déploiement** .  
  
4.  Affectez à la propriété **Database** le nom de la nouvelle base de données.  
  
     La prochaine fois que le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sera déployé, le déploiement s'effectuera dans cette nouvelle base de données. Si cette base de données existe déjà, elle sera remplacée.  
  
### Pour modifier le nom de la base de données à l'aide de SQL Server Management Studio  
  
-   Cliquez avec le bouton droit sur la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], puis modifiez la propriété Name.  
  
## Voir aussi  
 [propriétés du serveur dans Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Définir les propriétés de base de données multidimensionnelle &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/set-multidimensional-database-properties-analysis-services.md)   
 [Configurer les propriétés d’un projet Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)   
 [Déployer des projets Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
  