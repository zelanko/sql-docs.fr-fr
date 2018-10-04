---
title: Instances de Cluster de basculement, SQL Server sur Linux | Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 14d54a9e004364db783a4462d9e941f0e513a292
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47659807"
---
# <a name="failover-cluster-instances---sql-server-on-linux"></a>Instances de Cluster de basculement, SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article explique les concepts relatifs aux instances de cluster de basculement SQL Server (ICF) sur Linux. 

Pour créer une instance FCI à SQL Server sur Linux, consultez [configurer SQL Server FCI sur Linux](sql-server-linux-shared-disk-cluster-configure.md)

## <a name="the-clustering-layer"></a>La couche de Clustering

* Dans RHEL, la couche de clustering est basée sur Red Hat Enterprise Linux (RHEL) [module complémentaire HA](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf). 

    > [!NOTE] 
    > Accès à un module complémentaire Red Hat à haute disponibilité et la documentation requiert un abonnement. 

* SLES, la couche de clustering repose sur SUSE Linux Enterprise [haute disponibilité Extension (HAÉ)](https://www.suse.com/products/highavailability).

    Pour plus d’informations sur la configuration du cluster, les options de l’agent de ressource, la gestion, meilleures pratiques et recommandations, consultez [SUSE Linux Enterprise haute disponibilité Extension 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html).

Le complément RHEL à haute disponibilité et la HAÉ SUSE reposent sur [Pacemaker](http://clusterlabs.org/).

Comme le montre le diagramme suivant, le stockage est présenté à deux serveurs. Les composants clusters - Corosync et Pacemaker - coordonnent la gestion des ressources et des communications. Un des serveurs a la connexion active pour les ressources de stockage et le serveur SQL Server. Si Pacemaker détecte une défaillance les composants clusters gérer le déplacement des ressources vers un autre nœud.  

![Red Hat Enterprise Linux 7 partagé de Cluster de disque SQL](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 


> [!NOTE]
> À ce stade, l’intégration de SQL Server avec Pacemaker sur Linux n’est pas aussi couplée comme avec WSFC sous Windows. Dans SQL, il n’est aucune connaissance de la présence du cluster, tous les l’orchestration est en dehors d’et le service est contrôlé en tant qu’une instance autonome par Pacemaker. En outre, nom de réseau virtuel est spécifique à WSFC, il n’existe aucun équivalent de la même façon dans Pacemaker. Il est probable que @@servername et sys.servers pour renvoyer le nom du nœud, tandis que le cluster DMV sys.dm_os_cluster_nodes et sys.dm_os_cluster_properties ne seront aucun enregistrement. Pour utiliser une chaîne de connexion qui pointe vers un nom de serveur de chaîne et n’utilisez pas l’adresse IP, ils doivent enregistrer l’adresse IP utilisée pour créer la ressource d’adresse IP virtuelle (comme expliqué dans les sections suivantes) dans son serveur DNS avec le nom du serveur choisi.

## <a name="number-of-instances-and-nodes"></a>Nombre d’Instances et de nœuds

Une différence essentielle avec SQL Server sur Linux est qu’il ne peut exister une seule installation de SQL Server par le serveur Linux. Cette installation est appelée une instance. Cela signifie que contrairement à Windows Server qui prend en charge jusqu'à 25 instances fci par cluster de basculement Windows Server (WSFC), une instance FCI basé sur Linux peut uniquement être une seule instance. Cette une instance est également une instance par défaut ; Il n’existe aucun concept d’une instance nommée sur Linux. 

Un cluster Pacemaker ne peut avoir jusqu'à 16 nœuds lorsque Corosync est impliquée, donc une instance FCI unique peut couvrir jusqu'à 16 serveurs. Une instance FCI implémentée avec SQL Server Standard prend en charge jusqu'à deux nœuds de cluster même si le cluster Pacemaker a le nombre maximal de 16 nœuds.

Dans une FCI SQL Server, l’instance de SQL Server est active sur un nœud ou l’autre.

## <a name="ip-address-and-name"></a>Nom et adresse IP
Sur un cluster Pacemaker de Linux, chaque FCI SQL Server nécessite sa propre adresse IP unique et le nom. Si la configuration ICF s’étend sur plusieurs sous-réseaux, une adresse IP sera requise par sous-réseau. Le nom unique et l’ou les adresses IP sont utilisés pour accéder à l’instance FCI afin que les applications et les utilisateurs finaux n’avez pas besoin de savoir quel serveur sous-jacent du cluster Pacemaker.

Le nom de l’instance FCI dans le système DNS doit être le même que le nom de la ressource FCI qui est créé dans le cluster Pacemaker.
Le nom et l’adresse IP doivent être inscrit dans DNS.

## <a name="shared-storage"></a>Stockage partagé
Toutes les instances fci, qu’ils soient sur Linux ou Windows Server, nécessitent une certaine forme de stockage partagé. Ce stockage est présenté à tous les serveurs qui peuvent héberger éventuellement l’instance FCI, mais un seul serveur peut utiliser le stockage pour l’instance FCI à tout moment donné. Les options disponibles pour le stockage partagé sous Linux sont :

- iSCSI
- Network File System (NFS)
- Server Message Block (SMB) sous Windows Server, il existe des options légèrement différentes. Une option non pris en charge pour le cluster de basculement basés sur Linux est la possibilité d’utiliser un disque local pour le nœud pour TempDB, ce qui est l’espace de travail temporaire de SQL Server.

Dans une configuration qui s’étend sur plusieurs emplacements, ce qui est stocké à un centre de données doit être synchronisé avec les autres. En cas de basculement, l’instance FCI sera mise en ligne et le stockage est visible à être identiques. Cela nécessitera une méthode externe pour la réplication de stockage, si elle est effectuée via le matériel de stockage sous-jacent ou un utilitaire basé sur logiciel. 

>[!NOTE]
>Pour SQL Server, les déploiements basés sur Linux à l’aide de disques présentés directement sur un serveur doivent être formatés avec XFS ou EXT4. Autres systèmes de fichiers ne sont actuellement pas pris en charge. Les modifications apparaîtront ici.

Le processus pour présenter le stockage partagé est le même pour les différentes méthodes prises en charge :

- Configurer le stockage partagé
- Monter le stockage en tant que dossier pour les serveurs qui servira de nœuds du cluster Pacemaker pour l’instance FCI
- Si nécessaire, déplacez les bases de données système SQL Server dans un stockage partagé
- Test SQL Server fonctionne à partir de chaque serveur connecté au stockage partagé

Une différence majeure avec SQL Server sur Linux est que, pendant que vous pouvez configurer l’emplacement de fichier par défaut utilisateur données et de journaux, les bases de données système doivent toujours exister à `/var/opt/mssql/data`. Sur Windows Server, il est la possibilité de déplacer les bases de données système, y compris TempDB. Cela joue dans le stockage partagé comment est configuré pour une instance FCI.

Les chemins d’accès par défaut pour les bases de données non système peuvent être modifiés à l’aide de la `mssql-conf` utilitaire. Pour plus d’informations sur la façon de modifier les valeurs par défaut, [modifier l’emplacement de répertoire de données ou journal par défaut](sql-server-linux-configure-mssql-conf.md#datadir). Vous pouvez également stocker les données de SQL Server et des transactions dans d’autres emplacements tant qu’ils disposent d’une sécurité adaptée même si elle n’est pas un emplacement par défaut ; l’emplacement doit être indiqué.

Les rubriques suivantes expliquent comment configurer les types de stockage pris en charge pour une Linux basés sur FCI SQL Server :

- [Configurer l’instance de cluster de basculement - iSCSI - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [Configuration d’instance de cluster de basculement - NFS - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [Configuration d’instance de cluster de basculement - SMB - SQL Server sur Linux](sql-server-linux-shared-disk-cluster-configure-smb.md)
