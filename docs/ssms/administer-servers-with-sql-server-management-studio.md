---
title: Administrer des serveurs à l’aide de SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 08f62dedebd5cc8567e57163ef4d0e14c9935b42
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266427"
---
# <a name="administer-servers-with-sql-server-management-studio"></a>Administrer des serveurs à l'aide de SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] est un client d’administration intégré performant qui a été conçu pour répondre aux besoins en matière de gestion des serveurs des administrateurs de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et Azure SQL Database. Dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], les tâches d'administration sont effectuées à l'aide de l'Explorateur d'objets qui vous permet de vous connecter à n'importe quel serveur de la famille des produits [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et de parcourir son contenu sous forme graphique. Un serveur peut être une instance de [!INCLUDE[ssDE](../includes/ssde_md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ou d’Azure SQL Database.  
  
Les composants outil de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] comprennent les serveurs inscrits, l'Explorateur d'objets, l'Explorateur de solutions, l'Explorateur de modèles, la page Détails de l'Explorateur d'objets et la fenêtre de document. Pour afficher un outil, dans le menu **Affichage** , cliquez sur le nom de l’outil. Pour afficher l’outil Éditeur de requête, cliquez sur le bouton **Nouvelle requête** de la barre d’outils.  
  
> [!IMPORTANT]  
> Par défaut, le trafic réseau entre [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] n'est pas chiffré. N'utilisez pas de données sensibles (notamment des mots de passe) dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] , à moins que vous n'ayez établi une connexion chiffrée. Pour plus d’informations, consultez [Procédure : Activer les connexions chiffrées dans le moteur de base de données (Gestionnaire de configuration SQL Server)](https://msdn.microsoft.com/e1e55519-97ec-4404-81ef-881da3b42006).  
  
Utilisez [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] pour effectuer les tâches suivantes :  
  
-   Inscrire des serveurs  
  
-   Se connecter à une instance [!INCLUDE[ssDE](../includes/ssde_md.md)], SSAS [!INCLUDE[ssRS](../includes/ssrs.md)], [!INCLUDE[ssIS](../includes/ssis_md.md)] ou Azure SQL Database  
  
-   Configurer les propriétés du serveur  
  
-   Gérer la base de données et les objets SSAS tels que les cubes, les dimensions et les assemblys  
  
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
[Utiliser SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Procédure : afficher des propriétés du serveur (SQL Server Management Studio)](https://msdn.microsoft.com/55f3ac04-5626-4ad2-96bd-a1f1b079659d)  
  
