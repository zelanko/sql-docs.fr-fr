---
title: Renommer une base de données multidimensionnelle (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- renaming databases
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b6b27b086e84f173e72a61cf01341d5d01ec7ea9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62736747"
---
# <a name="rename-a-multidimensional-database-analysis-services"></a>Renommer une base de données multidimensionnelle (Analysis Services)
  La façon dont vous modifiez le nom d'une base de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diffère selon le mode de connexion à la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Pour modifier le nom d'une base de données existante, vous devez vous connecter à l'aide du mode en ligne. Pour modifier le nom de la base de données dans laquelle des objets d'un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] seront instanciés, vous devez vous connecter à l'aide du mode projet.  
  
### <a name="to-change-the-database-name-in-online-mode"></a>Pour modifier le nom de la base de données en mode en ligne  
  
1.  Connectez-vous directement à la base de données [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]à l'aide de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur la base de données, puis cliquez sur **Modifier la base de données**.  
  
3.  Dans la zone de texte **Nom de la base de données** , modifiez le nom de la base de données.  
  
4.  Dans la barre d'outils, cliquez sur **Enregistrer** ou sur **Enregistrer tout** , ou, dans le menu **Fichier** , cliquez sur **Enregistrer les éléments sélectionnés** ou sur **Enregistrer tout** , ou, fermez le **Concepteur de bases de données** , puis cliquez sur **Enregistrer** à l'invite.  
  
     Le nom de la base de données est mis à jour dans l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et l'objet base de données est actualisé dans l'Explorateur de solutions.  
  
### <a name="to-change-the-database-name-in-project-mode"></a>Pour modifier le nom de la base de données en mode projet  
  
1.  Ouvrez le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Pages de propriétés** sous **Propriétés de configuration** , sélectionnez **Déploiement** .  
  
4.  Affectez à la propriété **Database** le nom de la nouvelle base de données.  
  
     La prochaine fois que le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sera déployé, le déploiement s'effectuera dans cette nouvelle base de données. Si cette base de données existe déjà, elle sera remplacée.  
  
### <a name="to-change-the-database-name-using-sql-server-management-studio"></a>Pour modifier le nom de la base de données à l'aide de SQL Server Management Studio  
  
-   Cliquez avec le bouton droit sur la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , puis modifiez la propriété Name.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés du serveur dans Analysis Services](../server-properties/server-properties-in-analysis-services.md)   
 [Définir les propriétés de base de données multidimensionnelle &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md)   
 [Configurer les propriétés d’un projet Analysis Services &#40;SSDT&#41;](configure-analysis-services-project-properties-ssdt.md)   
 [Déployer des projets Analysis Services &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md)  
  
  
