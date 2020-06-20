---
title: Se connecter à un autre ordinateur (Gestionnaire de configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], other computers
ms.assetid: c4c1e94f-4f5f-431e-8b5b-d5ff97baf723
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95de509e0c78c807c3c9de25b317eb2b540db93a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935033"
---
# <a name="connect-to-another-computer-sql-server-configuration-manager"></a>Se connecter à un autre ordinateur (Gestionnaire de configuration SQL Server)
  Cette rubrique explique comment se connecter à un autre ordinateur dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Suivez la première procédure pour ouvrir la Console de gestion [!INCLUDE[msCoName](../../includes/msconame-md.md)] (mmc) de Gestion de l'ordinateur Windows, connectez-vous à l'ordinateur et développez l'arborescence Services et Applications. Suivez la deuxième procédure pour créer un fichier avec un lien vers le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur distant.  
  
> [!NOTE]  
>  Certaines actions ne peuvent pas être effectuées par le Gestionnaire de configuration lors de la connexion à distance.  
  
 Pour démarrer, arrêter, interrompre ou reprendre les services sur un autre ordinateur, vous pouvez également vous connecter au serveur à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquer avec le bouton droit sur le serveur ou l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , puis cliquer sur l'action souhaitée.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-connect-to-another-computer-with-windows-computer-management"></a>Pour se connecter à un autre ordinateur avec la Gestion de l'ordinateur Windows  
  
1.  Dans le menu **Démarrer** , cliquez avec le bouton droit sur **Poste de travail**, puis cliquez sur **Gérer**.  
  
2.  Dans **Gestion de l’ordinateur**, cliquez avec le bouton droit sur **Gestion de l’ordinateur (local)**, puis cliquez sur **Se connecter à un autre ordinateur**.  
  
3.  Dans la boîte de dialogue **Sélectionner un ordinateur** , dans la zone de texte **Un autre ordinateur** , tapez le nom de l'ordinateur que vous voulez gérer et cliquez sur **OK**.  
  
     La Gestion de l'ordinateur affiche les services exécutés sur l'ordinateur distant. Le nœud de niveau supérieur se transforme en gestion de l' **ordinateur** \<*remotecomputer*> .  
  
4.  Dans l'arborescence de la console, développez **Services et applications**, puis **Gestionnaire de configuration SQL Server** pour gérer les services de l'ordinateur distant.  
  
#### <a name="to-save-a-link-to-sql-server-configuration-manager-for-another-computer"></a>Pour enregistrer un lien vers le Gestionnaire de configuration SQL Server pour un autre ordinateur  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans la zone **ouvrir** , tapez `mmc -a` pour ouvrir la [!INCLUDE[msCoName](../../includes/msconame-md.md)] console de gestion en mode auteur.  
  
3.  Dans le menu **Fichier** , cliquez sur **Ajouter/Supprimer un composant logiciel enfichable**.  
  
4.  Dans la fenêtre **Ajouter/Supprimer un composant logiciel enfichable** , cliquez sur **Ajouter**.  
  
5.  Dans la fenêtre **Ajout d’un composant logiciel enfichable autonome** , cliquez sur **Gestion de l’ordinateur** , puis sur **Ajouter**.  
  
6.  Dans la fenêtre **Gestion de l'ordinateur** , cliquez sur **Un autre ordinateur**, tapez le nom de l'ordinateur distant que vous souhaitez gérer, puis cliquez sur **Terminer**.  
  
7.  Dans la fenêtre **Ajout d’un composant logiciel enfichable autonome** , cliquez sur **Fermer**.  
  
8.  Dans la fenêtre **Ajouter/Supprimer un composant logiciel enfichable** , cliquez sur **OK**.  
  
9. Développez Gestion de l' **ordinateur ( ***\<computer name>*** )**, puis **services et applications**.  
  
10. Cliquez avec le bouton droit sur **Gestionnaire de configuration SQL Server**, puis cliquez sur **Nouvelle fenêtre à partir d’ici**.  
  
11. Dans le menu **Fenêtre**, cliquez sur **Racine de la console** pour revenir à la première fenêtre et supprimez-la.  
  
12. Dans le menu **fichier** , cliquez sur **Enregistrer sous**, puis enregistrez le fichier dans le dossier de votre choix, avec un nom approprié avec l' `.msc` extension de fichier. Fermez [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.  
  
13. Pour ouvrir le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur l'ordinateur cible, double-cliquez sur le fichier. Si vous le souhaitez, enregistrez un lien vers le fichier sur le bureau ou dans le menu **Démarrer** .  
  
> [!CAUTION]  
>  Si vous utilisez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur distant, le nom de l'ordinateur ne va pas de soi et il est possible d'arrêter ou de configurer accidentellement un ordinateur. Sous l'onglet **Service** , activez la case à cocher **Nom de l'hôte** pour confirmer le nom de l'ordinateur avant de modifier un service.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer WMI pour afficher l'état du serveur dans les outils SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
