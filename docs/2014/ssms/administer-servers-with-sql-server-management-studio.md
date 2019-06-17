---
title: Administrer des serveurs à l’aide de SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9d57657d47f28dc0502b83375f563fa9df737831
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63206820"
---
# <a name="administer-servers-with-sql-server-management-studio"></a>Administrer des serveurs à l'aide de SQL Server Management Studio
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] est un client d’administration intégré complet, conçu pour répondre à la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] exigences de gestion de l’administrateur serveur. Dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], les tâches d'administration sont effectuées à l'aide de l'Explorateur d'objets qui vous permet de vous connecter à n'importe quel serveur de la famille des produits [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et de parcourir son contenu sous forme graphique. Un serveur peut être une instance du [!INCLUDE[ssDE](../includes/ssde-md.md)], d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ou d'[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 Les composants outil de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] comprennent les serveurs inscrits, l'Explorateur d'objets, l'Explorateur de solutions, l'Explorateur de modèles, la page Détails de l'Explorateur d'objets et la fenêtre de document. Pour afficher un outil, dans le menu **Affichage** , cliquez sur le nom de l’outil. Pour afficher l’outil Éditeur de requête, cliquez sur le bouton **Nouvelle requête** de la barre d’outils.  
  
> [!IMPORTANT]  
>  Par défaut, le trafic réseau entre [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] n'est pas chiffré. N'utilisez pas de données sensibles (notamment des mots de passe) dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] , à moins que vous n'ayez établi une connexion chiffrée. Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 Utilisez [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] pour effectuer les tâches suivantes :  
  
-   Inscrire des serveurs  
  
-   vous connecter à une instance du [!INCLUDE[ssDE](../includes/ssde-md.md)], de [!INCLUDE[ssAS](../includes/ssas-md.md)], de [!INCLUDE[ssRS](../includes/ssrs.md)] ou de [!INCLUDE[ssIS](../includes/ssis-md.md)] ;  
  
-   Configurer les propriétés du serveur  
  
-   Gérer la base de données et les objets [!INCLUDE[ssAS](../includes/ssas-md.md)] tels que les cubes, les dimensions et les assemblys  
  
-   Créer des objets tels que des bases de données, des tables, des cubes, des utilisateurs de base de données et des connexions  
  
-   Gérer les fichiers et les groupes de fichiers  
  
-   Attacher ou détacher les bases de données  
  
-   Lancer des outils de script  
  
-   Gérer la sécurité  
  
-   Afficher les journaux système  
  
-   Surveiller l'activité actuelle  
  
-   Configurer la réplication  
  
-   Gérer les index de texte intégral  
  
 Pour démarrer et arrêter [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou l'Agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , utilisez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)   
 [Afficher ou modifier des propriétés de serveur &#40;SQL Server&#41;](../database-engine/configure-windows/view-or-change-server-properties-sql-server.md)  
  
  
