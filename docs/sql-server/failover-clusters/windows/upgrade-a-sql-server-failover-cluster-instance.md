---
title: Mettre à niveau une instance de cluster de basculement
description: Procédure de mise à niveau d’une instance de cluster de basculement SQL Server à l’aide du support d’installation.
ms.custom: seo-lt-2019
ms.date: 11/21/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 24607a6372ba733165aa12fd159baea10f80ebd4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "74822023"
---
# <a name="upgrade-a-sql-server-failover-cluster-instance"></a>Mettre à niveau une instance de cluster de basculement SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge la mise à niveau d’un cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers une nouvelle version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vers un nouveau service pack ou une nouvelle mise à jour cumulative [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ou durant l’installation d’un nouveau Service Pack ou une nouvelle mise à jour cumulative Windows séparément sur tous les nœuds de cluster de basculement, avec des temps d’arrêt limités à un seul basculement manuel (ou deux basculements manuels en cas de restauration automatique vers l’instance principale d’origine).  
  
 La mise à niveau du système d’exploitation Windows d’un cluster de basculement n’est pas prise en charge par les systèmes d’exploitation antérieurs à [!INCLUDE[winblue-server-2-md](../../../includes/winblue-server-2-md.md)]. Pour mettre à niveau un nœud de cluster s’exécutant sur [!INCLUDE[winblue-server-2-md](../../../includes/winblue-server-2-md.md)] ou version supérieure, consultez [Exécuter une mise à jour ou mise à niveau propagée](#perform-a-rolling-upgrade-or-update).  
  
 Voici les détails de prise en charge :  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est prise en charge par le biais de l’interface utilisateur et à partir de l’invite de commandes. Vous pouvez exécuter une mise à niveau à partir de l’invite de commandes sur chaque nœud de cluster de basculement. Vous pouvez aussi utiliser l’interface utilisateur du programme d’installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour mettre à niveau chaque nœud de cluster.  Pour plus d’informations, consultez [Mettre à niveau une instance de cluster de basculement SQL Server &#40;programme d’installation&#41;](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md) et [Installer SQL Server à partir de l’invite de commandes](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
-   Les scénarios suivants ne sont pas pris en charge dans le cadre de la mise à niveau de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
    -   Vous ne pouvez pas effectuer une mise à niveau à partir d’une instance autonome de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers un cluster de basculement.  
  
    -   Vous ne pouvez pas ajouter de fonctionnalités à un cluster de basculement. par exemple ajouter le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] à un cluster de basculement existant [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]uniquement.  
  
    -   Vous ne pouvez pas rétrograder un nœud de cluster de basculement à une instance autonome.  
  
    -   La modification de l'édition du cluster de basculement est limitée à certains scénarios. Pour plus d’informations, consultez [Mises à niveau de la version et de l’édition prises en charge](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
-   Pendant la mise à niveau du cluster de basculement, le temps mort est limité au temps de basculement et au délai d'exécution des scripts de mise à niveau. Si vous suivez le processus de mise à niveau propagée du cluster de basculement ci-dessous et respectez tous les prérequis sur tous les nœuds avant de commencer le processus de mise à niveau, le temps mort est minime. Une mise à niveau de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] quand les tables à mémoire optimisée sont en cours d’utilisation prend plus de temps. Pour plus d’informations, consultez [Planifier et tester le plan de mise à niveau du moteur de base de données](../../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md).  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Avant de commencer, passez en revue les informations importantes suivantes :  
  
-   [Mises à niveau de la version et de l’édition prises en charge](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md) : vérifiez que vous pouvez procéder à une mise à niveau vers [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à partir de votre version du système d’exploitation Windows et de la version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Par exemple, vous ne pouvez pas effectuer directement la mise à niveau d’une instance de cluster de basculement SQL Server 2005 vers [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ou mettre à niveau un cluster de basculement exécutant [!INCLUDE[winxpsvr-md](../../../includes/winxpsvr-md.md)].  
  
-   [Choose a Database Engine Upgrade Method](../../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md): sélectionnez la méthode et les étapes de mise à niveau appropriées en fonction des versions et mises à niveau prises en charge ainsi que des autres composants installés dans votre environnement pour mettre à niveau les composants dans le bon ordre.  
  
-   [Planifier et tester le plan de mise à niveau du moteur de base de données](../../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md): consultez les notes de version et les problèmes de mise à niveau connus, ainsi que la liste de contrôle préalable à la mise à niveau, puis développez et testez votre plan de mise à niveau.  
  
-   [Configurations matérielle et logicielle requises pour l’installation de SQL Server](../../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md) : prenez connaissance de la configuration logicielle requise pour installer [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Si des logiciels supplémentaires sont nécessaires, installez-les sur chaque nœud avant de commencer le processus de mise à niveau pour réduire les éventuels temps d’arrêt.  
  
## <a name="perform-a-rolling-upgrade-or-update"></a>Exécuter une mise à jour ou mise à niveau propagée  
 Pour mettre à niveau un cluster du basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], utilisez le programme d’installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour mettre à niveau chaque nœud de cluster de basculement à la fois, en commençant par les nœuds passifs. Lorsque vous mettez à niveau chaque nœud, celui-ci est écarté de la liste des propriétaires possibles du cluster de basculement. En cas de basculement inattendu, les nœuds mis à niveau ne participent pas au basculement tant que la propriété du groupe de ressources de cluster n’est pas transférée vers un nœud mis à niveau par le programme d’installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Par défaut, le programme d’installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] détermine automatiquement le moment où le basculement doit être effectué vers un nœud mis à niveau. Cela dépend du nombre total de nœuds dans l'instance de cluster de basculement et du nombre de nœuds qui ont déjà été mis à niveau. Lorsque la moitié des nœuds ou plus a déjà été mise à niveau, le programme d’installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provoque un basculement vers un nœud mis à niveau lorsque vous effectuez une mise à niveau du nœud suivant. Lors du basculement vers un nœud mis à niveau, le groupe de clusters est déplacé vers un nœud mis à niveau. Tous les nœuds mis à niveau sont placés dans la liste des propriétaires possibles ; par ailleurs, tous les nœuds qui ne sont pas encore mis à niveau sont retirés de la liste des propriétaires possibles. Lorsque vous mettez à niveau chaque nœud restant, celui-ci est ajouté aux propriétaires possibles du cluster de basculement.  
  
 Ce processus entraîne une limitation de la durée du temps mort au temps de basculement et au délai d'exécution des scripts de mise à niveau de la base de données pendant l'ensemble de la mise à niveau du cluster de basculement.  
  
 Pour contrôler le comportement du basculement des nœuds de cluster pendant le processus de mise à niveau, exécutez l'opération de mise à niveau à l'invite de commandes et utilisez le paramètre /FAILOVERCLUSTERROLLOWNERSHIP. Pour plus d’informations, consultez [Installer SQL Server à partir de l’invite de commandes](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  

 ## <a name="upgrade-with-installation-media"></a>Mettre à niveau avec le support d’installation 
  
1.  Sur le média d’installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] portant sur l’édition qui correspond à celle que vous mettez à niveau, double-cliquez sur le fichier setup.exe dans le dossier racine. Il se peut que vous deviez installer les composants requis si ceux-ci ne sont pas déjà présents sur l'ordinateur.  
  
2.  Lorsque les composants requis sont installés, l'Assistant Installation démarre le Centre d'installation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Pour mettre à niveau une instance existante de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], sélectionnez votre instance.  
  
3.  Si les fichiers de support du programme d’installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sont requis, le programme d’installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les installe. Redémarrez votre ordinateur si vous êtes invité à le faire avant de continuer.  
  
4.  L'Outil d'analyse de configuration système effectue une opération de découverte sur votre ordinateur. Pour continuer, [!INCLUDE[clickOK](../../../includes/clickok-md.md)].  
  
5.  Dans la page Clé de produit, entrez la clé PID pour l'édition de la nouvelle version qui correspond à l'édition de l'ancienne version du produit. Par exemple, pour mettre à niveau un cluster de basculement Enterprise Edition, vous devez spécifier une clé PID pour [!INCLUDE[ssEnterprise](../../../includes/ssenterprise-md.md)]. Cliquez sur **Suivant** pour continuer. N'oubliez pas que la clé PID que vous utilisez pour une mise à niveau de cluster de basculement doit être cohérente sur tous les nœuds de cluster de basculement dans la même instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
6.  Dans la page Termes du contrat de licence, prenez connaissance du contrat de licence, puis activez la case à cocher indiquant que vous en acceptez les termes et conditions. Pour aider à améliorer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vous pouvez également activer l'option d'utilisation des fonctionnalités et envoyer des rapports à [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. Cliquez sur**Suivant**pour continuer. Pour mettre fin au programme d'installation, cliquez sur **Annuler**.  
  
7.  Dans la page Sélectionner une instance, spécifiez l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à mettre à niveau vers [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Cliquez sur**Suivant**pour continuer.  
  
8.  Dans la page Sélection de composant, les fonctionnalités à mettre à niveau sont présélectionnées. Une description de chaque groupe de composants apparaît dans le volet droit après que vous avez sélectionné le nom de la fonctionnalité. N'oubliez pas que vous ne pouvez pas modifier les fonctionnalités à mettre à niveau, de même que vous ne pouvez pas ajouter de fonctionnalités pendant l'opération de mise à niveau. Pour ajouter des fonctionnalités à une instance mise à niveau de [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] une fois l’opération de mise à niveau terminée, consultez [Ajouter des fonctionnalités à une instance de SQL Server 2016 &#40;programme d’installation&#41;](../../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md).  
  
     Les composants requis pour les fonctionnalités sélectionnées sont affichés dans le volet droit. Le programme d'installation de SQL Server installera les composants requis qui ne sont pas déjà installés pendant l'étape d'installation décrite ultérieurement dans cette procédure. Pour gagner du temps, préinstallez ces composants requis sur chaque nœud.  
  
9. Dans la page Configuration de l'instance, les champs sont remplis automatiquement à partir de l'ancienne instance. Vous pouvez spécifier la nouvelle valeur d'InstanceID.  
  
     **ID d’instance** : Par défaut, le nom de l’instance est utilisé comme ID d’instance. Il permet d'identifier les répertoires d'installation et les clés de Registre de votre instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Tel est le cas pour les instances par défaut et les instances nommées. Pour une instance par défaut, le nom de l'instance et l'ID d'instance sont MSSQLSERVER. Pour utiliser un ID d'instance non défini par défaut, activez la case à cocher **ID d'instance** et entrez une valeur. Si vous remplacez la valeur par défaut, vous devez spécifier le même ID d'instance pour l'instance mise à niveau sur tous les nœuds de cluster de basculement. L'ID d'instance de l'instance mise à niveau doit être identique sur tous les nœuds.  
  
     **Instances et fonctionnalités détectées** - La grille affiche les instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui se trouvent sur l’ordinateur où le programme d’installation s’exécute. Cliquez sur**Suivant**pour continuer.  
  
10. La page Espace disque nécessaire calcule l'espace disque nécessaire pour les fonctionnalités que vous spécifiez et compare cet espace à l'espace disque disponible sur l'ordinateur où le programme d'installation s'exécute.  
  
11. Dans la page de mise à niveau de recherche en texte intégral, spécifiez les options de mise à niveau pour les bases de données mises à niveau. Pour plus d’informations, consultez [Options de mise à niveau de recherche en texte intégral](https://msdn.microsoft.com/library/16c9376b-5fbb-4495-a429-06a2493849c9).  
  
12. Dans la page **Création de rapports d'erreurs** , spécifiez les informations que vous souhaitez envoyer à [!INCLUDE[msCoName](../../../includes/msconame-md.md)] afin d'aider à améliorer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les options de création de rapports d'erreurs sont activées par défaut.  
  
13. L'Outil d'analyse de configuration système exécute un autre ensemble de règles pour valider la configuration de votre ordinateur avec les fonctionnalités [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que vous avez spécifiées, avant le début de l'opération de mise à niveau.  
  
14. La page Rapport de mise à niveau de cluster affiche la liste des nœuds de l'instance de cluster de basculement, ainsi que les informations de version de l'instance pour les composants [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de chaque nœud. Elle affiche l'état des scripts de base de données et l'état des scripts de réplication. De plus, elle affiche également des messages d'information sur ce qui doit se produire lorsque vous cliquez sur **Suivant**. Selon le nombre de nœuds de cluster de basculement déjà mis à niveau et le nombre total de nœuds, le programme d’installation affiche une description du comportement du basculement lorsque vous cliquez sur **Suivant**. Il indique également le temps mort inutile potentiel, si vous n'avez pas déjà installé les composants requis.   
  
15. La page Prêt pour la mise à niveau affiche une arborescence des options d'installation spécifiées durant l'exécution du programme d'installation. Pour continuer, cliquez sur **Mettre à niveau**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installe d'abord les composants requis pour les fonctionnalités sélectionnées, puis installe les fonctionnalités.  
  
16. Au cours de la mise à niveau, la page Progression de l'installation fournit des informations d'état pour que vous puissiez contrôler la progression de la mise à niveau sur le nœud actuel au fil de l'exécution du programme d'installation.  
  
17. Une fois la mise à niveau du nœud actuel terminée, la page Rapport de mise à niveau de cluster affiche des informations sur l'état de la mise à niveau pour tous les nœuds de cluster de basculement, les fonctionnalités sur chaque nœud de cluster de basculement, ainsi que leurs informations de version. Vérifiez les informations de version qui sont affichées et poursuivez la mise à niveau des nœuds restants. En cas de basculement des nœuds mis à niveau, ces informations s'affichent également sur la page d'état. Vous pouvez également procéder à une vérification supplémentaire dans l'Administrateur de cluster Windows.  
  
18. Après la mise à niveau, la page Terminé fournit un lien vers le fichier journal résumé de l'installation et d'autres remarques importantes. Pour terminer le processus d'installation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , cliquez sur **Fermer**.  
  
19. Redémarrez l'ordinateur si vous êtes invité à le faire. Il est important de lire le message affiché par l'Assistant Installation à la fin de l'installation. Pour plus d’informations sur les fichiers journaux d’installation, consultez [Afficher et lire les fichiers journaux d’installation de SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
20. Pour terminer la mise à niveau, répétez ces étapes sur tous les autres nœuds du cluster de basculement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="upgrade-a-multi-subnet-failover-cluster"></a>Mettre à niveau un cluster de basculement de sous-réseaux multiples  

Procédez comme suit pour mettre à niveau votre instance de cluster de basculement SQL Server dans un environnement à plusieurs sous-réseaux. 
  
### <a name="to-upgrade-to-a-ssnoversion-multi-subnet-failover-cluster-existing-ssnoversion-cluster-is-a-non-multi-subnet-cluster"></a>Pour mettre à niveau vers un cluster de basculement de sous-réseaux multiples [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (le cluster [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] existant est un cluster de sous-réseaux non multiples.)  
  
1.  Suivez la procédure ci-dessus pour mettre à niveau votre cluster.  
  
2.  Ajoutez un nœud sur un sous-réseau différent à l'aide de l'action d'installation AddNode et confirmez la dépendance de ressource d'adresse IP sur OR dans la page **Configuration du réseau du cluster** . Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
### <a name="to-upgrade-a-multi-subnet-cluster-currently-using-stretch-v-lan"></a>Pour mettre à niveau un cluster de sous-réseaux multiples utilisant actuellement l'étirement V-LAN  
  
1.  Suivez la procédure ci-dessus pour mettre à niveau votre cluster vers [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
2.  Modifiez les paramètres réseau pour déplacer le nœud distant vers un autre sous-réseau.  
  
3.  À l'aide de l'outil d'administration de cluster de basculement Windows, ajoutez une nouvelle adresse IP pour le nouveau sous-réseau et définissez la dépendance de ressource d'adresse IP sur OR.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Après avoir effectué la mise à niveau vers [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], effectuez les tâches suivantes :  
  
-   [Mise à niveau du moteur de base de données](../../../database-engine/install-windows/complete-the-database-engine-upgrade.md)  
  
-   [Modifier le mode de compatibilité de base de données et utiliser le magasin des requêtes](../../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md)  
  
-   [Tirer parti des nouveautés de SQL Server 2016](https://msdn.microsoft.com/library/d8879659-8efa-4442-bcbb-91272647ae16)  
  

  
  
