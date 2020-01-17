---
title: Se connecter à un autre ordinateur (Gestionnaire de configuration SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 11/19/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], other computers
ms.assetid: c4c1e94f-4f5f-431e-8b5b-d5ff97baf723
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 03f409e11e037fcc406940d5a97e9934a77b96b4
ms.sourcegitcommit: c98c6e33d04d4a1888db7dbe89cb0b1bb3a66418
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74249759"
---
# <a name="scm-services---connect-to-another-computer"></a>Services SCM - Se connecter à un autre ordinateur

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article explique comment se connecter à un autre ordinateur dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Suivez la première procédure pour ouvrir la Console de gestion [!INCLUDE[msCoName](../../includes/msconame-md.md)] (mmc) de Gestion de l'ordinateur Windows, connectez-vous à l'ordinateur et développez l'arborescence Services et Applications. Suivez la deuxième procédure pour créer un fichier avec un lien vers le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur distant.

> [!NOTE]
> Certaines actions ne peuvent pas être effectuées par le Gestionnaire de configuration lors de la connexion à distance.

Pour démarrer, arrêter, interrompre ou reprendre les services sur un autre ordinateur, vous pouvez également vous connecter au serveur à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquer avec le bouton droit sur le serveur ou l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , puis cliquer sur l'action souhaitée.

## <a name="SSMSProcedure"></a>

### <a name="to-connect-to-another-computer-with-windows-computer-management"></a>Pour se connecter à un autre ordinateur avec la Gestion de l'ordinateur Windows

1. Cliquez avec le bouton droit sur le menu **Démarrer**, puis cliquez sur **Gestion de l’ordinateur (local)** .
2. Dans le menu **Action**, cliquez sur **Se connecter à un autre ordinateur**.
3. Dans la boîte de dialogue **Sélectionner un ordinateur** , dans la zone de texte **Un autre ordinateur** , tapez le nom de l'ordinateur que vous voulez gérer et cliquez sur **OK**.

   La Gestion de l'ordinateur affiche les services exécutés sur l'ordinateur distant. Le nœud de niveau supérieur devient alors **Gestion de l’ordinateur** \<*ordinateur_distant*>.

4. Dans l'arborescence de la console, développez **Services et applications**, puis **Gestionnaire de configuration SQL Server** pour gérer les services de l'ordinateur distant.

### <a name="to-save-a-link-to-sql-server-configuration-manager-for-another-computer"></a>Pour enregistrer un lien vers le Gestionnaire de configuration SQL Server pour un autre ordinateur

1. Dans le menu **Démarrer** , cliquez sur **Exécuter**.

2. Dans la zone **Ouvrir**, tapez **mmc -a** (tapez **mmc /32 -a** sur un ordinateur 64 bits) pour ouvrir [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console en mode auteur.
3. Dans le menu **Fichier** , cliquez sur **Ajouter/Supprimer un composant logiciel enfichable**.
4. Dans la fenêtre **Ajouter/Supprimer un composant logiciel enfichable** , cliquez sur **Ajouter**.
5. Dans la fenêtre **Ajout d’un composant logiciel enfichable autonome** , cliquez sur **Gestion de l’ordinateur** , puis sur **Ajouter**.
6. Dans la fenêtre **Gestion de l'ordinateur** , cliquez sur **Un autre ordinateur**, tapez le nom de l'ordinateur distant que vous souhaitez gérer, puis cliquez sur **Terminer**.
7. Dans la fenêtre **Ajout d’un composant logiciel enfichable autonome** , cliquez sur **Fermer**.
8. Dans la fenêtre **Ajouter/Supprimer un composant logiciel enfichable** , cliquez sur **OK**.
9. Développez **Gestion de l’ordinateur (** _\<nom_ordinateur>_ **)** , puis **Services et applications**.
10. Cliquez avec le bouton droit sur **Gestionnaire de configuration SQL Server**, puis cliquez sur **Nouvelle fenêtre à partir d’ici**.
11. Dans le menu **Fenêtre**, cliquez sur **Racine de la console** pour revenir à la première fenêtre et supprimez-la.
12. Dans le menu **Fichier** , cliquez sur **Enregistrer sous**, et enregistrez le fichier dans le dossier souhaité en lui donnant un nom approprié et l’extension de fichier **.msc** . Fermez [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.
13. Pour ouvrir le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur l'ordinateur cible, double-cliquez sur le fichier. Si vous le souhaitez, enregistrez un lien vers le fichier sur le bureau ou dans le menu **Démarrer** .

> [!CAUTION]
> Si vous utilisez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur distant, le nom de l'ordinateur ne va pas de soi et il est possible d'arrêter ou de configurer accidentellement un ordinateur. Sous l'onglet **Service** , activez la case à cocher **Nom de l'hôte** pour confirmer le nom de l'ordinateur avant de modifier un service.

## <a name="see-also"></a>Voir aussi

- [Configurer WMI pour afficher l'état du serveur dans les outils SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)
