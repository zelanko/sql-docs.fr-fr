---
title: Mise à niveau et mise à jour des serveurs de groupe de disponibilité avec un temps mort et une perte de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f670af56-dbcc-4309-9119-f919dcad8a65
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: db74916aa24c1dcd3f94fa163ae0ef87697a8fa3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247024"
---
# <a name="upgrade-and-update-of-availability-group-servers-with-minimal-downtime-and-data-loss"></a>Mise à niveau et mise à jour des serveurs de groupes de disponibilité avec un temps mort minimal et perte de données
  Lorsque de la mise à jour ou de la mise à niveau d'instances de serveur de SQL Server 2012 vers un Service Pack ou une version plus récente, réduisez le temps mort d'un groupe de disponibilité à un seul basculement manuel en effectuant une mise à jour ou une mise à niveau séquentielle. En ce qui concerne la mise à niveau des versions de SQL Server, cette mise à niveau s'appelle une mise à niveau propagée. En ce qui concerne la mise à jour de la version actuelle de SQL Server avec les correctifs ou les Service Pack, cette mise à jour s'appelle une mise à jour propagée.  
  
 Cette rubrique limite la discussion aux mises à niveau/mises à jour de SQL Server. Pour le système d’exploitation mises à niveau/mises à jour fonctionnant sur les instances de SQL Server hautement disponible, consultez [Cross-cluster Migration de groupes de disponibilité AlwaysOn pour les mises à niveau du système d’exploitation](http://msdn.microsoft.com/library/jj873730.aspx)  
  
## <a name="rolling-upgradeupdate-best-practices-for-alwayson-availability-groups"></a>Meilleures pratiques pour la mise à niveau/mise à jour propagée de groupes de disponibilité AlwaysOn  
 Appliquez les meilleures pratiques suivantes lorsque vous effectuez la mise à niveau/mise à jour du serveur afin de réduire le temps mort et la perte de données de vos groupes de disponibilité :  
  
-   Avant de procéder à la mise à niveau/mise à jour propagée :  
  
    -   Procédez à un essai de basculement manuel sur au moins un de vos réplicas avec validation synchrone.  
  
    -   Protégez vos données en effectuant une sauvegarde complète de chaque base de données de disponibilité.  
  
    -   Exécutez la commande DBCC CHECKDB sur chaque base de données de disponibilité.  
  
-   Procédez toujours à la mise à niveau/mise à jour des nœuds du réplica secondaire distant, puis des nœuds du réplica secondaire local et enfin du nœud du réplica principal.  
  
-   Les sauvegardes ne peuvent pas être exécutées dans une base de données qui est en cours de mise à niveau.  Avant de mettre les réplicas secondaires à niveau, configurez la préférence de sauvegarde automatisée pour exécuter les sauvegardes uniquement sur le réplica principal.  Avant de mettre le réplica principal à niveau, modifiez ce paramètre pour exécuter les sauvegardes uniquement sur les réplicas secondaires.  
  
-   Pour éviter les basculements involontaires des groupes de disponibilité lors du processus de mise à niveau/mise à jour, supprimez le basculement des groupes de disponibilité dans tous les réplicas avec validation synchrone avant de commencer.  
  
-   Ne procédez pas à la mise à niveau du nœud de réplica principal avant le basculement du groupe de disponibilité sur un nœud mis à niveau avec un réplica secondaire. Sinon, les applications clientes risquent de pâtir de temps morts prolongés lors de la mise à niveau/mise à jour sur le réplica principal.  
  
-   Procédez toujours au basculement du groupe de disponibilité sur un nœud de réplica secondaire avec validation synchrone. Si vous procédez au basculement vers un réplica secondaire avec validation asynchrone, les bases de données subiront une perte de données et le déplacement des données sera automatiquement suspendu tant que vous ne le reprendrez pas manuellement.  
  
-   Ne procédez pas à la mise à niveau/mise à jour du nœud de réplica principal avant la mise à niveau/mise à jour des autres nœuds de réplica secondaire. Un réplica principal mis à niveau n'envoie plus les journaux à un réplica secondaire qui n'a pas encore été mis à niveau avec la même version. Lorsque le déplacement des données vers un réplica secondaire est suspendu, aucun basculement automatique ne se produit pour ce réplica, et vos bases de données de disponibilité sont vulnérables à une perte de données.  
  
-   Avant de procéder au basculement d'un groupe de disponibilité, vérifiez que l'état de synchronisation de la cible de basculement est SYNCHRONIZED.  
  
## <a name="rolling-upgradeupdate-process"></a>Processus de mise à niveau/mise à jour propagée  
 Dans la pratique, le processus exact dépend de facteurs tels que la topologie de déploiement de vos groupes de disponibilité et du mode de validation de chaque réplica. Cependant, dans le scénario le plus simple, une mise à niveau/mise à jour propagée est un processus en plusieurs étapes impliquant les différentes étapes suivantes :  
  
 ![Mise à niveau d’un groupe de disponibilité dans le scénario HADR](../../media/alwaysonupgrade-ag-hadr.gif "Mise à niveau d’un groupe de disponibilité dans le scénario HADR")  
  
1.  Supprimer le basculement automatique sur tous les réplicas avec validation synchrone  
  
2.  Mettre à niveau/mettre à jour toutes les instances de serveur distant exécutant les réplicas secondaires avec validation asynchrone  
  
3.  Mettre à niveau/mettre à jour les instances de serveur local qui n'exécutent pas le réplica principal  
  
4.  Procéder manuellement au basculement du groupe de disponibilité sur un réplica secondaire avec validation synchrone  
  
5.  Mettre à niveau/mettre à jour l'instance du serveur qui hébergeait précédemment le réplica principal  
  
6.  Configurer le basculement automatique des partenaires de basculement selon les besoins  
  
 Si nécessaire, effectuez un basculement manuel supplémentaire pour rétablir la configuration d'origine du groupe de disponibilité.  
  
## <a name="availability-group-with-one-remote-secondary-replica"></a>Groupe de disponibilité avec un réplica secondaire distant  
 Si vous avez déployé un groupe de disponibilité uniquement à des fins de récupération d'urgence, vous devrez peut-être le basculer sur un réplica secondaire avec validation asynchrone. Cette configuration est illustrée dans la figure ci-dessous :  
  
 ![Mise à niveau d’un groupe de disponibilité dans le scénario DR](../../media/agupgrade-ag-dr.gif "Mise à niveau d’un groupe de disponibilité dans le scénario DR")  
  
 Dans ce cas, vous devez basculer le groupe de disponibilité sur le réplica secondaire avec validation asynchrone lors de la mise à niveau/mise à jour. Pour éviter la perte de données, changez le mode de validation en validation synchrone et attendez que le réplica secondaire soit synchronisé avant de basculer le groupe de disponibilité. Par conséquent, le processus de mise à niveau/mise à jour peut ressembler à ce qui suit :  
  
1.  Mettre à niveau/mettre à jour le serveur distant  
  
2.  Changer le mode de validation en validation synchrone  
  
3.  Patienter jusqu'à ce que l'état de synchronisation soit SYNCHRONIZED  
  
4.  Basculer le groupe de disponibilité sur le site distant  
  
5.  Mettre à niveau/mettre à jour le serveur (site principal) local  
  
6.  Basculer le groupe de disponibilité sur le site principal  
  
7.  Changer le mode de validation en validation asynchrone  
  
 Le mode de validation synchrone n'étant pas recommandé pour la synchronisation des données sur un site distant, les applications clientes peuvent remarquer une augmentation immédiate de la latence de la base de données après modification du paramètre. De plus, avec le basculement les messages du journal en attente d'accusé de réception sont ignorés. Le nombre de messages du journal ignorés peut être élevé en raison de la latence réseau élevée entre les deux sites, à l'origine d'un nombre élevé d'échecs de transactions des clients. Pour réduire l'impact sur les applications clientes, procédez comme suit :  
  
-   Sélectionnez avec précaution une fenêtre de maintenance lorsque le trafic est faible sur le client  
  
-   Lors de la mise à niveau/mise à jour de SQL Server sur le site principal, revenez au mode de disponibilité validation asynchrone, puis rétablissez la validation synchrone lorsque vous êtes prêt à effectuer le basculement sur le site principal  
  
## <a name="availability-group-with-failover-cluster-instance-nodes"></a>Groupe de disponibilité avec nœuds d'instance de cluster de basculement  
 Si un groupe de disponibilité contient des nœuds d'instance de cluster de basculement, mettez à niveau/jour les nœuds inactifs avant de mettre à niveau/jour les nœuds actifs. La figure ci-dessous illustre un scénario de groupe de disponibilité courant avec instances de cluster de basculement pour la haute disponibilité et la validation asynchrone entre les instances de cluster de basculement à des fins de récupération d'urgence, et l'ordre de mise à niveau.  
  
 ![Mise à niveau d’un groupe de disponibilité avec des FCI](../../media/agupgrade-ag-fci-dr.gif "Mise à niveau d’un groupe de disponibilité avec des FCI")  
  
1.  Mettre à niveau/jour REMOTE2  
  
2.  Basculer FCI2 sur REMOTE2  
  
3.  Mettre à niveau/jour REMOTE1  
  
4.  Mettre à niveau/jour PRIMARY2  
  
5.  Basculer FCI1 sur PRIMARY2  
  
6.  Mettre à niveau/jour PRIMARY1  
  
## <a name="upgradeupdate-sql-server-instances-with-multiple-availability-groups"></a>Mettre à niveau/mettre à jour les instances de SQL Server avec plusieurs groupes de disponibilité  
 Si vous exécutez plusieurs groupes de disponibilité avec réplicas principaux sur des nœuds de serveur distincts (configuration active/active), le chemin d'accès de mise à niveau/mise à jour implique davantage d'étapes de basculement afin d'assurer la haute disponibilité du processus. Supposons que vous exécutez trois groupes de disponibilité sur trois nœuds de serveur, tel que l'illustre le tableau suivant, et tous les réplicas secondaires s'exécutent en mode de validation synchrone.  
  
|Groupe de disponibilité|Nœud1|Nœud2|Node3|  
|------------------------|-----------|-----------|-----------|  
|AG1|Principal|||  
|AG2||Principal||  
|AG3|||Principal|  
  
 Il peut s'avérer nécessaire d'effectuer une mise à niveau/mise à jour propagée à charge équilibrée dans l'ordre suivant :  
  
1.  Basculer AG2 sur Nœud3 (pour libérer Nœud2)  
  
2.  Mettre à niveau/mettre à jour Nœud2  
  
3.  Basculer AG1 sur Nœud2 (pour libérer Nœud1)  
  
4.  Mettre à niveau/mettre à jour Nœud1  
  
5.  Basculer AG2 et AG3 sur Nœud1 (pour libérer Nœud3)  
  
6.  Mettre à niveau/mettre à jour Nœud3  
  
7.  Basculer AG3 sur Nœud3  
  
 Cette séquence de mise à niveau/mise à jour présente un temps mort moyen inférieur à deux basculements par groupes de disponibilité. La configuration obtenue est illustrée dans le tableau ci-dessous.  
  
|Groupe de disponibilité|Nœud1|Nœud2|Node3|  
|------------------------|-----------|-----------|-----------|  
|AG1||Principal||  
|AG2|Principal|||  
|AG3|||Principal|  
  
 Le chemin d'accès de la mise à niveau/mise à jour varie selon votre implémentation, ainsi que le temps mort pour=vant être rencontré par les applications clientes.  
  
  
