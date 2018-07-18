---
title: Mettre à niveau une instance de cluster de basculement SQL Server (programme d’installation) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], creating clusters
- clusters [SQL Server], creating
- failover clustering [SQL Server], upgrading
ms.assetid: ea8b7d66-e5a1-402f-9928-8f7310e84f5c
caps.latest.revision: 59
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: be393e7f9dd4eef29a26aa4d4e46c77f4ff76d9e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161870"
---
# <a name="upgrade-a-sql-server-failover-cluster-instance-setup"></a>Mettre à niveau une instance de cluster de basculement SQL Server (programme d'installation)
  Vous pouvez mettre à niveau un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers un cluster de basculement [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] à l'aide de l'Assistant Installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou à partir de l'invite de commandes.  
  
 Pendant la mise à niveau du cluster de basculement, le temps mort est limité au temps de basculement et au délai d'exécution des scripts de mise à niveau. Si vous suivez le processus de mise à niveau propagée du cluster de basculement, votre temps mort est minime. Selon que vous disposez ou non de tous les composants requis sur les nœuds de cluster de basculement, le temps mort peut varier en fonction de la durée d'installation des composants requis. Pour plus d’informations sur la manière de minimiser le temps d’arrêt pendant la mise à niveau, consultez le [meilleures pratiques avant la mise à niveau Cluster de basculement](#BestPractices) section de cette page.  
  
 Pour plus d’informations sur la mise à niveau, consultez [Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md) et [mise à niveau vers SQL Server 2014](../../../database-engine/install-windows/upgrade-sql-server.md).  
  
 Pour plus d’informations sur l’exemple de syntaxe pour l’utilisation de l’invite de commandes, consultez [installer SQL Server 2014 à partir de l’invite de commandes](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Avant de commencer, passez en revue les informations importantes suivantes :  
  
-   [Avant l'installation du clustering de basculement](../install/before-installing-failover-clustering.md)  
  
-   [Utilisez le Conseiller de mise à niveau pour préparer des mises à niveau](../../install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
-   [Mettre à niveau le moteur de base de données](../../../database-engine/install-windows/upgrade-database-engine.md)  
  
-   Le programme d'installation installe le .NET Framework 4.0 sur un système d'exploitation en cluster. Pour réduire les temps morts possibles, envisagez d'installer le .NET Framework 4.0 avant d'exécuter le programme d'installation.  
  
-   Pour vous assurer que le composant de Visual Studio peut être installé correctement, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vous oblige à installer une mise à jour. Le programme d'installation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vérifie si cette la présence de cette mise à jour, puis vous demande de télécharger et d'installer la mise à jour avant de vous laisser poursuivre l'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour éviter l’interruption pendant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le programme d’installation, vous pouvez télécharger et installer la mise à jour avant d’exécuter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le programme d’installation comme décrit ci-dessous (ou installer les mises à jour pour .NET 3.5 SP1 disponibles sur Windows Update) :  
  
     Si vous installez [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] sur un ordinateur avec le système d’exploitation Windows Server 2008 SP2, vous pouvez obtenir la mise à jour obligatoire à partir de [ici](http://go.microsoft.com/fwlink/?LinkId=198093)  
  
     Si vous installez [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] sur un ordinateur avec le système d'exploitation [!INCLUDE[win7](../../../includes/win7-md.md)] SP1 ou [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] SP1, cette mise à jour est incluse.  
  
-   Le .NET Framework 3.5 SP1 n'est plus installé par le programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], mais il peut être requis lors de l'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)]. Pour plus d’informations, consultez les [notes de publication](http://go.microsoft.com/fwlink/?LinkId=296445) de [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  
  
-   Dans le cas d'une installation locale, vous devez exécuter le programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en qualité d'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui dispose des autorisations de lecture sur le partage distant.  
  
-   Pour mettre à niveau une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à un [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] cluster de basculement, l’instance en cours de mise à niveau doit être un cluster de basculement.  
  
     Pour déplacer une instance autonome de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers un cluster de basculement [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)], installez un nouveau cluster de basculement [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)], puis migrez les bases de données utilisateur depuis l'instance autonome à l'aide de l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="rolling-upgrades"></a>Mises à niveau propagées  
 Pour mettre à niveau un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de cluster de basculement à [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)], vous devez exécuter le programme d’installation avec l’action de mise à niveau sur chaque nœud de cluster de basculement, un à la fois, en commençant par les nœuds passifs. Lorsque vous mettez à niveau chaque nœud, celui-ci est écarté de la liste des propriétaires possibles du cluster de basculement. En cas de basculement inattendu, les nœuds mis à niveau ne participent pas au basculement tant que la propriété du groupe de ressources de cluster n'est pas transférée vers un nœud mis à niveau par le programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Par défaut, le programme d'installation détermine automatiquement le moment où le basculement doit être effectué vers un nœud mis à niveau. Cela dépend du nombre total de nœuds dans l'instance de cluster de basculement et du nombre de nœuds qui ont déjà été mis à niveau. Lorsque la moitié des nœuds ou plus a déjà été mise à niveau, le programme d'installation provoque un basculement vers un nœud mis à niveau lorsque vous effectuez une mise à niveau du nœud suivant. Lors du basculement vers un nœud mis à niveau, le groupe de clusters est déplacé vers un nœud mis à niveau. Tous les nœuds mis à niveau sont placés dans la liste des propriétaires possibles ; par ailleurs, tous les nœuds qui ne sont pas encore mis à niveau sont retirés de la liste des propriétaires possibles. Lorsque vous mettez à niveau chaque nœud restant, celui-ci est ajouté aux propriétaires possibles du cluster de basculement.  
  
 Ce processus entraîne une limitation de la durée du temps mort au temps de basculement et au délai d'exécution des scripts de mise à niveau de la base de données pendant l'ensemble de la mise à niveau du cluster de basculement.  
  
 Pour contrôler le comportement du basculement des nœuds de cluster pendant le processus de mise à niveau, exécutez l'opération de mise à niveau à l'invite de commandes et utilisez le paramètre /FAILOVERCLUSTERROLLOWNERSHIP. Pour plus d’informations, consultez [Installer SQL Server 2014 à partir de l’invite de commandes](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
 **Remarque** s’il existe un cluster de basculement à un nœud, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le programme d’installation prend le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] groupe de ressources hors connexion.  
  
## <a name="considerations-when-upgrading-from-includessversion2005includesssversion2005-mdmd"></a>Considérations lors de la mise à niveau de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]  
 Si vous spécifiez des groupes de domaine pour la stratégie de sécurité du cluster, vous ne pouvez pas spécifier de SID de service sur [!INCLUDE[nextref_longhorn](../../../includes/nextref-longhorn-md.md)]. Si vous souhaitez utiliser le SID de service, vous devez effectuer une mise à niveau côte à côte.  
  
 Lorsque vous sélectionnez le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] pour la mise à niveau, la recherche en texte intégral est incluse dans le programme d'installation, qu'elle soit ou non installée dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Si la recherche en texte intégral a été activée dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], le programme d'installation recrée le catalogue de recherche en texte intégral quelles que soient les options disponibles.  
  
## <a name="upgrading-to-a-includesssql14includessssql14-mdmd-multi-subnet-failover-cluster"></a>Mise à niveau vers un cluster de basculement de sous-réseaux multiples [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]  
 Il existe deux scénarios possibles pour les mises à niveau :  
  
1.  Le cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est configuré actuellement sur un seul sous-réseau. Vous devez d'abord mettre à niveau le cluster existant vers [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] en lançant le programme d'installation et en suivant le processus de mise à niveau. Après avoir terminé la mise à niveau du cluster de basculement existant, ajoutez un nœud qui se trouve sur un sous-réseau différent à l'aide de la fonctionnalité AddNode. Confirmez la modification de dépendance de ressource d'adresse IP en OR dans la page de configuration de réseau de clusters. Vous avez maintenant un cluster de basculement de sous-réseaux multiples [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
2.  Le cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est configuré actuellement sur plusieurs sous-réseaux à l'aide de la technologie d'étirement V-LAN : vous devez d'abord mettre à niveau le cluster existant vers [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]. Comme la technologie d'étirement V-LAN configure un sous-réseau unique, la configuration réseau doit être modifiée pour inclure plusieurs sous-réseaux. La dépendance de ressource d'adresse IP doit être modifiée à l'aide de l'outil d'administration de cluster de basculement Windows et la dépendance IP doit être définie sur OR.  
  
###  <a name="BestPractices"></a> Meilleures pratiques avant la mise à niveau un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Cluster de basculement  
 Pour réduire le temps mort inattendu provoqué par un redémarrage, préinstallez le package de non-redémarrage pour le .NET Framework 4.0 sur tous les nœuds de cluster de basculement avant d'exécuter la mise à niveau sur les nœuds de cluster. Il est recommandé de respecter les étapes suivantes pour la préinstallation des composants requis :  
  
-   Installez le package de non-redémarrage pour le .NET Framework 4.0 et mettez à niveau uniquement les composants partagés en commençant par les nœuds passifs. Cela entraîne l'installation du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 4.0, de Windows Installer 4.5 et des fichiers de support [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Redémarrez une ou plusieurs fois, selon les besoins.  
  
-   Effectuez le basculement vers un nœud mis à niveau.  
  
-   Mettez à niveau les composants partagés sur le dernier nœud restant.  
  
 Une fois que tous les composants partagés sont mis à niveau et que les composants requis sont installés, démarrez la mise à niveau du cluster de basculement. Vous devez exécuter la mise à niveau sur chaque nœud de cluster de basculement, en commençant par les nœuds passifs jusqu'à ce que vous atteigniez le nœud propriétaire du groupe de ressources de cluster.  
  
-   Vous ne pouvez pas ajouter de fonctionnalités à un cluster de basculement existant.  
  
-   La modification de l'édition du cluster de basculement est limitée à certains scénarios. Pour plus d’informations, consultez [Mises à niveau de la version et de l’édition prises en charge](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
##  <a name="UpgradeSteps"></a> Pour mettre à niveau un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
#### <a name="to-upgrade-a-includessnoversionincludesssnoversion-mdmd-failover-cluster"></a>Pour mettre à niveau un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
1.  Insérez le support d'installation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et, dans le dossier racine, double-cliquez sur Setup.exe. Pour effectuer l'installation à partir d'un partage réseau, accédez au dossier racine sur le partage, puis double-cliquez sur Setup.exe. Il se peut que vous deviez installer les composants requis si ceux-ci ne sont pas déjà présents sur l'ordinateur.  
  
2.  > [!IMPORTANT]  
    >  Pour plus d’informations sur les étapes 3 et 4, consultez le [meilleures pratiques avant la mise à niveau Cluster de basculement](#BestPractices) section.  
  
3.  Lorsque les composants requis sont installés, l'Assistant Installation démarre le Centre d'installation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Pour mettre à niveau une instance existante de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], cliquez sur **mise à niveau à partir de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], ou [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].**  
  
4.  Si les fichiers de support du programme d'installation sont requis, le programme d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les installe. Redémarrez votre ordinateur si vous êtes invité à le faire avant de continuer.  
  
5.  L'Outil d'analyse de configuration système effectue une opération de découverte sur votre ordinateur. Pour continuer, [!INCLUDE[clickOK](../../../includes/clickok-md.md)].  
  
6.  Dans la page Clé de produit, entrez la clé PID pour l'édition de la nouvelle version qui correspond à l'édition de l'ancienne version du produit. Par exemple, pour mettre à niveau un cluster de basculement Enterprise Edition, vous devez spécifier une clé PID pour [!INCLUDE[ssEnterprise](../../../includes/ssenterprise-md.md)]. Cliquez sur **Suivant** pour continuer. N'oubliez pas que la clé PID que vous utilisez pour une mise à niveau de cluster de basculement doit être cohérente sur tous les nœuds de cluster de basculement dans la même instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [éditions et composants de SQL Server 2014](../../editions-and-components-of-sql-server-2016.md) et [Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
7.  Dans la page Termes du contrat de licence, prenez connaissance du contrat de licence, puis activez la case à cocher indiquant que vous en acceptez les termes et conditions. Pour aider à améliorer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vous pouvez également activer l'option d'utilisation des fonctionnalités et envoyer des rapports à [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. Cliquez sur**Suivant**pour continuer. Pour mettre fin au programme d'installation, cliquez sur **Annuler**.  
  
8.  Dans la page Sélectionner une instance, spécifiez l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à mettre à niveau vers [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]. Cliquez sur**Suivant**pour continuer.  
  
9. Dans la page Sélection de composant, les fonctionnalités à mettre à niveau sont présélectionnées. Une description de chaque groupe de composants apparaît dans le volet droit après que vous avez sélectionné le nom de la fonctionnalité. N'oubliez pas que vous ne pouvez pas modifier les fonctionnalités à mettre à niveau, de même que vous ne pouvez pas ajouter de fonctionnalités pendant l'opération de mise à niveau. Pour ajouter des fonctionnalités à une instance mise à niveau de [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] une fois l’opération de mise à niveau terminée, consultez [ajouter des fonctionnalités à une Instance de SQL Server 2014 &#40;le programme d’installation&#41;](../../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-setup.md).  
  
     Les composants requis pour les fonctionnalités sélectionnées sont affichés dans le volet droit. Le programme d'installation de SQL Server installera les composants requis qui ne sont pas déjà installés pendant l'étape d'installation décrite ultérieurement dans cette procédure.  
  
10. Dans la page Configuration de l'instance, les champs sont remplis automatiquement à partir de l'ancienne instance. Vous pouvez spécifier la nouvelle valeur d'InstanceID.  
  
     **ID d’instance** - Par défaut, le nom de l’instance est utilisé comme ID d’instance. Il permet d'identifier les répertoires d'installation et les clés de Registre de votre instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Tel est le cas pour les instances par défaut et les instances nommées. Pour une instance par défaut, le nom de l'instance et l'ID d'instance sont MSSQLSERVER. Pour utiliser un ID d'instance non défini par défaut, activez la case à cocher **ID d'instance** et entrez une valeur. Si vous remplacez la valeur par défaut, vous devez spécifier le même ID d'instance pour l'instance mise à niveau sur tous les nœuds de cluster de basculement. L'ID d'instance de l'instance mise à niveau doit être identique sur tous les nœuds.  
  
     **Instances et fonctionnalités détectées** -la grille affiche les instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui se trouvent sur l’ordinateur où le programme d’installation est en cours d’exécution. Cliquez sur**Suivant**pour continuer.  
  
11. La page Espace disque nécessaire calcule l'espace disque nécessaire pour les fonctionnalités que vous spécifiez et compare cet espace à l'espace disque disponible sur l'ordinateur où le programme d'installation s'exécute.  
  
12. Dans la page de mise à niveau de recherche en texte intégral, spécifiez les options de mise à niveau pour les bases de données mises à niveau. Pour plus d’informations, consultez [Options de mise à niveau de recherche en texte intégral](../../install/full-text-search-upgrade-options.md).  
  
13. Dans la page **Création de rapports d'erreurs** , spécifiez les informations que vous souhaitez envoyer à [!INCLUDE[msCoName](../../../includes/msconame-md.md)] afin d'aider à améliorer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les options de création de rapports d'erreurs sont activées par défaut.  
  
14. L'Outil d'analyse de configuration système exécute un autre ensemble de règles pour valider la configuration de votre ordinateur avec les fonctionnalités [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que vous avez spécifiées, avant le début de l'opération de mise à niveau.  
  
15. La page Rapport de mise à niveau de cluster affiche la liste des nœuds de l'instance de cluster de basculement, ainsi que les informations de version de l'instance pour les composants [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de chaque nœud. Elle affiche l'état des scripts de base de données et l'état des scripts de réplication. De plus, elle affiche également des messages d'information sur ce qui doit se produire lorsque vous cliquez sur **Suivant**. En fonction du nombre de nœuds de cluster de basculement qui ont déjà été mis à niveau et le nombre total de nœuds, le programme d’installation affiche le comportement de basculement qui se produit lorsque vous cliquez sur **suivant**. Il indique également le temps mort inutile potentiel, si vous n'avez pas déjà installé les composants requis.  
  
16. La page Prêt pour la mise à niveau affiche une arborescence des options d'installation spécifiées durant l'exécution du programme d'installation. Pour continuer, cliquez sur **Mettre à niveau**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installe d'abord les composants requis pour les fonctionnalités sélectionnées, puis installe les fonctionnalités.  
  
17. Au cours de la mise à niveau, la page Progression de l'installation fournit des informations d'état pour que vous puissiez contrôler la progression de la mise à niveau sur le nœud actuel au fil de l'exécution du programme d'installation.  
  
18. Une fois la mise à niveau du nœud actuel terminée, la page Rapport de mise à niveau de cluster affiche des informations sur l'état de la mise à niveau pour tous les nœuds de cluster de basculement, les fonctionnalités sur chaque nœud de cluster de basculement, ainsi que leurs informations de version. Vérifiez les informations de version qui sont affichées et poursuivez la mise à niveau des nœuds restants. En cas de basculement des nœuds mis à niveau, ces informations s'affichent également sur la page d'état. Vous pouvez également procéder à une vérification supplémentaire dans l'Administrateur de cluster Windows.  
  
19. Après la mise à niveau, la page Terminé fournit un lien vers le fichier journal résumé de l'installation et d'autres remarques importantes. Pour terminer le processus d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , cliquez sur **Fermer**.  
  
20. Redémarrez l'ordinateur si vous êtes invité à le faire. Il est important de lire le message affiché par l'Assistant Installation à la fin de l'installation. Pour plus d’informations sur les fichiers journaux d’installation, consultez [Afficher et lire les fichiers journaux d’installation de SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
21. Pour terminer la mise à niveau, répétez les étapes 1 à 21 sur tous les autres nœuds du cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="to-upgrade-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster"></a>Pour mettre à niveau un cluster de basculement de sous-réseaux multiples [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
#### <a name="to-upgrade-to-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster-existing-includessnoversionincludesssnoversion-mdmd-cluster-is-a-non-multi-subnet-cluster"></a>Pour mettre à niveau vers un cluster de basculement de sous-réseaux multiples [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (le cluster [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] existant est un cluster de sous-réseaux non multiples.)  
  
1.  Suivez les étapes 1 à 24 décrites dans le [pour mettre à niveau un cluster de basculement SQL Server](#UpgradeSteps) section ci-dessus pour mettre à niveau votre cluster à [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  
  
2.  Ajoutez un nœud sur un sous-réseau différent à l'aide de l'action d'installation AddNode et confirmez la dépendance de ressource d'adresse IP sur OR dans la page **Configuration du réseau du cluster** . Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
#### <a name="to-upgrade-a-multi-subnet-cluster-currently-using-stretch-v-lan"></a>Pour mettre à niveau un cluster de sous-réseaux multiples utilisant actuellement l'étirement V-LAN  
  
1.  Suivez les étapes 1 à 24 décrites dans le [pour mettre à niveau un cluster de basculement SQL Server](#UpgradeSteps) section ci-dessus pour mettre à niveau votre cluster à [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
2.  Modifiez les paramètres réseau pour déplacer le nœud distant vers un autre sous-réseau.  
  
3.  À l'aide de l'outil d'administration de cluster de basculement Windows, ajoutez une nouvelle adresse IP pour le nouveau sous-réseau et définissez la dépendance de ressource d'adresse IP sur OR.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Après avoir effectué la mise à niveau vers [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)], effectuez les tâches suivantes :  
  
-   Inscrire vos serveurs  
  
     La mise à niveau entraîne la suppression des paramètres du Registre pour l'instance antérieure de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Après la mise à niveau, vous devez réinscrire vos serveurs.  
  
-   Mettre à jour les statistiques  
  
     Afin d'optimiser les performances des requêtes, il est recommandé de mettre à jour les statistiques sur toutes les bases de données après une mise à niveau. Utilisez la procédure stockée **sp_updatestats** pour mettre à jour les statistiques des tables définies par l’utilisateur dans les bases de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Configurer votre nouvelle installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
     Pour réduire la surface d'exposition d'un système, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installe et active de façon sélective les services et fonctionnalités clés. Pour plus d'informations sur la configuration de la surface d'exposition, consultez le fichier Lisezmoi de cette version.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer SQL Server 2014 à partir de l’invite de commandes](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Afficher et lire les fichiers journaux d'installation de SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
