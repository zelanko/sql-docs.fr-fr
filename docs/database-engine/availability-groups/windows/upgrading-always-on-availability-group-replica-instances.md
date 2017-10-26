---
title: "Mise à niveau d’instances de réplica d’un groupe de disponibilité Always On | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f670af56-dbcc-4309-9119-f919dcad8a65
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1783e700e516978e4eded68fa675addd8d31a234
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="upgrading-always-on-availability-group-replica-instances"></a>Mise à niveau d’instances de réplica d’un groupe de disponibilité Always On
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Pendant la mise à niveau d’un groupe de disponibilité Always On [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers une nouvelle version [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , un nouveau Service Pack [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ou une mise à jour cumulative, ou pendant l’installation d’un nouveau Service Pack ou une nouvelle mise à jour cumulative Windows, vous pouvez réduire les temps d’arrêt pour chaque réplica principal à un seul basculement manuel en effectuant une mise à niveau propagée (ou deux basculements manuels en cas de restauration automatique vers l’instance principale d’origine). Pendant le processus de mise à niveau, un réplica secondaire sera pas disponible pour le basculement ou pour des opérations en lecture seule et, après la mise à niveau, le réplica secondaire peut prendre un certain temps rattraper son retard sur le nœud de réplica principal en fonction du volume d’activité sur le nœud de réplica principal (attendez-vous à un trafic réseau important).  
  
> [!NOTE]  
>  Cette rubrique limite la discussion à la mise à niveau de SQL Server lui-même. Elle ne couvre pas la mise à niveau du système d’exploitation contenant le cluster WSFC (Windows Server Failover Clusting). La mise à niveau du système d’exploitation Windows qui héberge le cluster de basculement n’est pas prise en charge psr les systèmes d’exploitation antérieurs à Windows Server 2012 R2. Pour mettre à niveau un nœud de cluster s’exécutant sur Windows Server 2012 R2, consultez la rubrique [Cluster Operating System Rolling Upgrade](https://technet.microsoft.com/library/dn850430.aspx)(Mise à niveau propagée du système d’exploitation de cluster).  
  
## <a name="prerequisites"></a>Configuration requise  
 Avant de commencer, passez en revue les informations importantes suivantes :  
  
-   [Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md): vérifiez que vous pouvez procéder à une mise à niveau vers SQL Server 2016 à partir de votre version du système d’exploitation Windows et de la version de SQL Server. Par exemple, vous ne pouvez pas mettre à niveau directement une instance SQL Server 2005 vers [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   [Choose a Database Engine Upgrade Method](../../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md): sélectionnez la méthode et les étapes de mise à niveau appropriées en fonction des versions et mises à niveau prises en charge ainsi que des autres composants installés dans votre environnement pour mettre à niveau les composants dans le bon ordre.  
  
-   [Planifier et tester le plan de mise à niveau du moteur de base de données](../../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md): consultez les notes de version et les problèmes de mise à niveau connus, ainsi que la liste de contrôle préalable à la mise à niveau, puis développez et testez votre plan de mise à niveau.  
  
-   [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2016](../../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md): prenez connaissance de la configuration logicielle requise pour installer [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Si des logiciels supplémentaires sont nécessaires, installez-les sur chaque nœud avant de commencer le processus de mise à niveau pour réduire les éventuels temps d’arrêt.  
  
## <a name="rolling-upgrade-best-practices-for-always-on-availability-groups"></a>Bonnes pratiques pour la mise à niveau propagée de groupes de disponibilité Always On  
 Appliquez les meilleures pratiques suivantes lorsque vous effectuez la mise à niveau/mise à jour du serveur afin de réduire les temps d’arrêt et la perte de données de vos groupes de disponibilité :  
  
-   Avant de procéder à la mise à niveau propagée :  
  
    -   Procédez à un essai de basculement manuel sur au moins l’une de vos instances de réplica avec validation synchrone.  
  
    -   Protégez vos données en effectuant une sauvegarde complète de chaque base de données de disponibilité.  
  
    -   Exécutez la commande DBCC CHECKDB sur chaque base de données de disponibilité.  
  
-   Procédez toujours d’abord à la mise à niveau des instances du réplica secondaire distant, puis des instances du réplica secondaire local et enfin de l’instance du réplica principal.  
  
-   Les sauvegardes ne peuvent pas être exécutées dans une base de données qui est en cours de mise à niveau.  Avant de mettre les réplicas secondaires à niveau, configurez la préférence de sauvegarde automatisée pour exécuter les sauvegardes uniquement sur le réplica principal.  Pendant une mise à niveau, aucun réplica ne sera lisible ou disponible pour les sauvegardes. Pendant une mise à niveau sans version, vous pouvez configurer des sauvegardes automatisées s’exécutant sur des réplicas secondaires avant la mise à niveau du réplica principal.  
  
-   Pendant une mise à niveau de version, les instances de réplica secondaire accessibles en écriture ne peuvent pas être lues après une mise à niveau d’un réplica secondaire et avant que le réplica principal ne soit basculé vers un réplica secondaire mis à niveau ou que le réplica principal ne soit mis à niveau.  
  
-   Pour éviter les basculements involontaires des groupes de disponibilité lors du processus de mise à niveau, supprimez le basculement des groupes de disponibilité dans tous les réplicas avec validation synchrone avant de commencer.  
  
-   Ne procédez pas à la mise à niveau de l’instance de réplica principal avant d’avoir basculé le groupe de disponibilité vers une instance mise à niveau avec un réplica secondaire. Sinon, les applications clientes risquent de connaître des temps morts prolongés lors de la mise à niveau sur l’instance de réplica principal.  
  
-   Procédez toujours au basculement du groupe de disponibilité sur une instance de réplica secondaire avec validation synchrone. Si vous procédez au basculement vers une instance de réplica secondaire avec validation asynchrone, les bases de données subiront une perte de données et le déplacement des données sera automatiquement suspendu tant que vous ne le reprendrez pas manuellement.  
  
-   Ne procédez pas à la mise à niveau de l’instance de réplica principal avant la mise à niveau ou à jour des instances nœuds de réplica secondaire. Un réplica principal mis à niveau n'envoie plus les journaux à un réplica secondaire dont l’instance [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] n'a pas encore été mise à niveau à la même version. Lorsque le déplacement des données vers un réplica secondaire est suspendu, aucun basculement automatique ne se produit pour ce réplica, et vos bases de données de disponibilité sont vulnérables à une perte de données.  
  
-   Avant de procéder au basculement d'un groupe de disponibilité, vérifiez que l'état de synchronisation de la cible de basculement est SYNCHRONIZED.  
  
## <a name="rolling-upgrade-process"></a>Processus de mise à niveau propagée  
 Dans la pratique, le processus exact dépend de facteurs tels que la topologie de déploiement de vos groupes de disponibilité et du mode de validation de chaque réplica. Cependant, dans le scénario le plus simple, une mise à niveau propagée est un processus en plusieurs étapes impliquant les étapes suivantes :  
  
 ![Mise à niveau d’un groupe de disponibilité dans le scénario HADR](../../../database-engine/availability-groups/windows/media/alwaysonupgrade-ag-hadr.gif "Mise à niveau d’un groupe de disponibilité dans le scénario HADR")  
  
1.  Supprimer le basculement automatique sur tous les réplicas avec validation synchrone  
  
2.  Mettre à niveau toutes les instances de réplica secondaire distant exécutant les réplicas secondaires avec validation asynchrone  
  
3.  Mettre à niveau instances de réplica secondaire local qui n'exécutent pas le réplica principal  
  
4.  Procéder manuellement au basculement du groupe de disponibilité sur un réplica secondaire local avec validation synchrone  
  
5.  Mettre à niveau ou mettre à jour l'instance de réplica local qui hébergeait précédemment le réplica principal  
  
6.  Configurer le basculement automatique des partenaires de basculement selon les besoins  
  
 Si nécessaire, effectuez un basculement manuel supplémentaire pour rétablir la configuration d'origine du groupe de disponibilité.  
  
## <a name="availability-group-with-one-remote-secondary-replica"></a>Groupe de disponibilité avec un réplica secondaire distant  
 Si vous avez déployé un groupe de disponibilité uniquement à des fins de récupération d'urgence, vous devrez peut-être le basculer sur un réplica secondaire avec validation asynchrone. Cette configuration est illustrée dans la figure ci-dessous :  
  
 ![Mise à niveau d’un groupe de disponibilité dans le scénario DR](../../../database-engine/availability-groups/windows/media/agupgrade-ag-dr.gif "Mise à niveau d’un groupe de disponibilité dans le scénario DR")  
  
 Dans ce cas, vous devez basculer le groupe de disponibilité sur le réplica secondaire avec validation asynchrone lors de la mise à niveau propagée. Pour éviter la perte de données, changez le mode de validation en validation synchrone et attendez que le réplica secondaire soit synchronisé avant de basculer le groupe de disponibilité. Par conséquent, le processus de mise à niveau à jour peut ressembler à ce qui suit :  
  
1.  Mise à niveau l’instance de réplica secondaire sur le site distant  
  
2.  Changer le mode de validation en validation synchrone  
  
3.  Patienter jusqu'à ce que l'état de synchronisation soit SYNCHRONIZED  
  
4.  Basculer le groupe de disponibilité sur réplica secondaire sur le site distant  
  
5.  Mettre à niveau ou mettre à jour l’instance de réplica local (site principal)  
  
6.  Basculer de nouveau le groupe de disponibilité sur le site principal  
  
7.  Changer le mode de validation en validation asynchrone  
  
 Le mode de validation synchrone n'étant pas recommandé pour la synchronisation des données sur un site distant, les applications clientes peuvent remarquer une augmentation immédiate de la latence de la base de données après modification du paramètre. De plus, avec le basculement les messages du journal en attente d'accusé de réception sont ignorés. Le nombre de messages du journal ignorés peut être élevé en raison de la latence réseau élevée entre les deux sites, à l'origine d'un nombre élevé d'échecs de transactions des clients. Pour réduire l'impact sur les applications clientes, procédez comme suit :  
  
-   Sélectionnez avec précaution une fenêtre de maintenance lorsque le trafic est faible sur le client  
  
-   Lors de la mise à niveau ou mise à jour sur le site principal [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , revenez au mode de disponibilité validation asynchrone, puis rétablissez la validation synchrone lorsque vous êtes prêt à effectuer le basculement sur le site principal  
  
## <a name="availability-group-with-failover-cluster-instance-nodes"></a>Groupe de disponibilité avec nœuds d'instance de cluster de basculement  
 Si un groupe de disponibilité contient des nœuds d'instance de cluster de basculement, mettez à niveau les nœuds inactifs avant de mettre à niveau les nœuds actifs. La figure ci-dessous illustre un scénario de groupe de disponibilité courant avec instances de cluster de basculement pour la haute disponibilité et la validation asynchrone entre les instances de cluster de basculement à des fins de récupération d'urgence, et l'ordre de mise à niveau.  
  
 ![Mise à niveau d’un groupe de disponibilité avec des FCI](../../../database-engine/availability-groups/windows/media/agupgrade-ag-fci-dr.gif "Mise à niveau d’un groupe de disponibilité avec des FCI")  
  
1.  Mettre à niveau ou à jour REMOTE2  
  
2.  Basculer FCI2 sur REMOTE2  
  
3.  Mettre à niveau ou à jour REMOTE1  
  
4.  Mettre à niveau ou à jour PRIMARY2  
  
5.  Basculer FCI1 sur PRIMARY2  
  
6.  Mettre à niveau ou à jour PRIMARY1  
  
## <a name="upgrade-update-sql-server-instances-with-multiple-availability-groups"></a>Mettre à niveau/mettre à jour des instances de SQL Server avec plusieurs groupes de disponibilité  
 Si vous exécutez plusieurs groupes de disponibilité avec réplicas principaux sur des nœuds de serveur distincts (configuration active/active), le chemin d'accès de mise à niveau implique davantage d'étapes de basculement afin d'assurer la haute disponibilité du processus. Supposons que vous exécutez trois groupes de disponibilité sur trois nœuds de serveur, tel que l'illustre le tableau suivant, et tous les réplicas secondaires s'exécutent en mode de validation synchrone.  
  
|Groupe de disponibilité|Nœud1|Nœud2|Node3|  
|------------------------|-----------|-----------|-----------|  
|AG1|Principal|||  
|AG2||Principal||  
|AG3|||Principal|  
  
 Il peut s'avérer nécessaire d'effectuer une mise à niveau/ propagée à charge équilibrée dans l'ordre suivant :  
  
1.  Basculer AG2 sur Nœud3 (pour libérer Nœud2)  
  
2.  Mettre à niveau ou à jour Nœud2  
  
3.  Basculer AG1 sur Nœud2 (pour libérer Nœud1)  
  
4.  Mettre à niveau ou à jour Nœud1  
  
5.  Basculer AG2 et AG3 sur Nœud1 (pour libérer Nœud3)  
  
6.  Mettre à niveau ou à jour Nœud3  
  
7.  Basculer AG3 sur Nœud3  
  
 Cette séquence de mise à niveau présente un temps d’arrêt moyen inférieur à deux basculements par groupe de disponibilité. La configuration obtenue est illustrée dans le tableau ci-dessous.  
  
|Groupe de disponibilité|Nœud1|Nœud2|Node3|  
|------------------------|-----------|-----------|-----------|  
|AG1||Principal||  
|AG2|Principal|||  
|AG3|||Principal|  
  
 Le chemin d'accès de la mise à niveau varie selon votre implémentation. Le temps mort que les applications clientes peuvent rencontrer varie également.  
  
> [!NOTE]  
>  Dans de nombreux cas, une fois la mise à niveau propagée terminée, le serveur principal d’origine sera restauré automatiquement sur le réplica principal.  
  
## <a name="see-also"></a>Voir aussi  
 [Effectuer une mise à niveau vers SQL Server 2016 à l’aide de l’Assistant Installation &#40;programme d’installation&#41;](../../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)   
 [Installer SQL Server 2016 à partir de l’invite de commandes](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)  
  
  

