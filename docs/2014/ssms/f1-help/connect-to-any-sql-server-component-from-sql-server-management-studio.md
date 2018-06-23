---
title: Se connecter à n’importe quel composant de SQL Server à partir de SQL Server Management Studio | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connections [SQL Server], SQL Server Management Studio
- saving connections
- components [SQL Server], connections
- SQL Server Management Studio [SQL Server], connections
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5c6a144c8c3807a00bfca2cff61faf95771463c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143150"
---
# <a name="connect-to-any-sql-server-component-from-sql-server-management-studio"></a>Se connecter à n'importe quel composant de SQL Server à partir de SQL Server Management Studio
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] fournit des fonctionnalités pour la gestion de tous les composants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour vous connecter à :  
  
-   Une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Bien que [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] vous permette d'utiliser des requêtes sans que vous deviez établir une connexion à une source de données, la plupart des autres tâches requièrent une connexion. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] contient la boîte de dialogue **Se connecter au serveur** qui vous permet de configurer les propriétés de connexion aux composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Quand [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] démarre, il ouvre la boîte de dialogue **Se connecter au serveur** et vous invite à vous connecter à un serveur. Cette boîte de dialogue conserve les paramètres de connexion depuis leur dernière utilisation.  
  
> [!NOTE]  
>  Cette fonctionnalité peut être désactivée pour qu'aucune connexion ne soit automatiquement établie. Pour plus d’informations, consultez [Options de démarrage du service moteur de base de données](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
## <a name="saving-connections"></a>enregistrement des connexions  
 Vous pouvez enregistrer des connexions à des serveurs spécifiques dans les serveurs inscrits ou des connexions dans des projets à l'aide de l'Explorateur de solutions.  
  
### <a name="saving-connections-in-registered-servers"></a>Enregistrement des connexions dans les serveurs inscrits  
 Lorsque vous inscrivez un serveur, [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] enregistre les informations de connexion dans les serveurs inscrits. Pour vous connecter à un serveur inscrit, double-cliquez sur le nom du serveur dans les serveurs inscrits. L'Explorateur d'objets ouvre alors une connexion au serveur.  
  
### <a name="saving-connections-in-solution-explorer"></a>Enregistrement des connexions dans l'Explorateur de solutions  
 L'Explorateur de solutions vous permet de stocker les requêtes, les scripts, les connexions et d'autres informations associées dans un projet. Chaque projet de script contient un nœud appelé **Connexions**où vous pouvez enregistrer une ou plusieurs connexions. Pour ajouter une connexion, cliquez avec le bouton droit sur **Connexions**, puis cliquez sur **Nouvelle connexion**. Pour accéder à une connexion enregistrée, développez **Connexions** et double-cliquez sur la connexion. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ouvre une fenêtre de requête associée à cette connexion. Une fois enregistrés, les scripts conservent leur association à une connexion spécifique.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser SQL Server Management Studio](../sql-server-management-studio-ssms.md)   
 [l’Explorateur d’objets](../object/object-explorer.md)  
  
  