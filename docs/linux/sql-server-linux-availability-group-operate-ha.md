---
title: Utiliser le groupe de disponibilité SQL Server sur Linux | Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/01/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: a33c18175a03b589f7b431655ff4704356f5eeaf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795997"
---
# <a name="operate-always-on-availability-groups-on-linux"></a>Fonctionnent toujours sur les groupes de disponibilité sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

## <a name="upgrade-availability-group"></a>Mettre à niveau le groupe de disponibilité

Avant de vous mettre à niveau un groupe de disponibilité, passez en revue les modèles et pratiques à [la mise à niveau des instances de réplica de groupe de disponibilité](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).

Les sections suivantes expliquent comment effectuer une mise à niveau propagée avec des instances de SQL Server sur Linux avec des groupes de disponibilité. 

### <a name="upgrade-steps-on-linux"></a>Étapes de mise à niveau sur Linux

Lorsque les réplicas du groupe de disponibilité sont sur des instances de SQL Server sous Linux, le type de cluster du groupe de disponibilité est `EXTERNAL` ou `NONE`. Un groupe de disponibilité est géré par un gestionnaire de cluster en plus de Cluster de basculement Windows Server (WSFC) est `EXTERNAL`. Pacemaker avec Corosync est un exemple d’un gestionnaire de cluster externe. Un groupe de disponibilité avec aucun gestionnaire de cluster a le type de cluster `NONE` les étapes de mise à niveau décrites ici sont spécifiques pour les groupes de disponibilité de type de cluster `EXTERNAL` ou `NONE`.

L’ordre dans lequel vous mettez à niveau d’instances dépend de si leur rôle est de base de données secondaire et ou non qu’ils hébergent les réplicas synchrones ou asynchrones. Mettre à niveau les instances de SQL Server qui hébergent les réplicas secondaires asynchrones tout d’abord. Puis mettez à niveau les instances qui hébergent les réplicas secondaires synchrones. 

   >[!NOTE]
   >Si un groupe de disponibilité possède uniquement asynchrone réplicas, pour éviter toute perte de données modifiez un réplica synchrone et attendre qu’il soit synchronisé. Puis mettez à niveau ce réplica.
   
Avant de commencer, sauvegardez chaque base de données.

1. Arrêter la ressource sur le nœud qui héberge le réplica secondaire ciblé pour la mise à niveau.
   
   Avant d’exécuter la commande de mise à niveau, arrêtez la ressource afin que le cluster ne sera pas surveiller et inutilement d’échouer. L’exemple suivant ajoute une contrainte d’emplacement sur le nœud qui entraîne sur la ressource doit être arrêtée. Mise à jour `ag_cluster-master` avec le nom de ressource et `nodeName1` avec le nœud qui héberge le réplica ciblé pour la mise à niveau.

   ```bash
   pcs constraint location ag_cluster-master avoids nodeName1
   ```

1. Mettre à niveau SQL Server sur le réplica secondaire.

   L’exemple suivant met à niveau `mssql-server` et `mssql-server-ha` packages.

   ```bash
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
1. Supprimer la contrainte d’emplacement.

   Avant d’exécuter la commande de mise à niveau, arrêtez la ressource afin que le cluster ne sera pas surveiller et inutilement d’échouer. L’exemple suivant ajoute une contrainte d’emplacement sur le nœud qui entraîne sur la ressource doit être arrêtée. Mise à jour `ag_cluster-master` avec le nom de ressource et `nodeName1` avec le nœud qui héberge le réplica ciblé pour la mise à niveau.

   ```bash
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```
   Comme meilleure pratique, vérifiez que la ressource est démarrée (à l’aide de `pcs status` commande) et le réplica secondaire est connecté et synchronisé l’état après mise à niveau.

1. Une fois que tous les réplicas secondaires sont mis à niveau, basculez manuellement vers un des réplicas secondaires synchrones.

   Pour les groupes de disponibilité avec `EXTERNAL` type de cluster, utilisez les outils de gestion de cluster échec over ; groupes de disponibilité avec `NONE` type de cluster doit utiliser Transact-SQL pour effectuer le basculement. 
   L’exemple suivant bascule d’un groupe de disponibilité avec les outils de gestion de cluster. Remplacez `<targetReplicaName>` par le nom du réplica secondaire synchrone qui deviendra principal :

   ```bash
   sudo pcs resource move ag_cluster-master <targetReplicaName> --master  
   ``` 
   
   >[!IMPORTANT]
   >Les étapes suivantes s’appliquent uniquement aux groupes de disponibilité qui n’ont pas un gestionnaire de cluster.

   Si le type de cluster de groupe de disponibilité est `NONE`manuellement effectuer un basculement. Exécutez les étapes suivantes dans l'ordre :

      A. La commande suivante définit le réplica principal vers le site secondaire. Remplacez `AG1` par le nom de votre groupe de disponibilité. Exécutez la commande Transact-SQL sur l’instance de SQL Server qui héberge le réplica principal.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY);
      ```

      B. La commande suivante définit un réplica secondaire synchrone vers le site principal. Exécutez la commande Transact-SQL suivante sur l’instance cible de SQL Server - l’instance qui héberge le réplica secondaire synchrone.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] FAILOVER;
      ```

1. Après le basculement, mettez à niveau SQL Server sur l’ancien réplica principal en répétant la procédure précédente.

   L’exemple suivant met à niveau `mssql-server` et `mssql-server-ha` packages.

   ```bash
   # add constraint for the resource to stop on the upgraded node
   # replace 'nodename2' with the name of the cluster node targeted for upgrade
   pcs constraint location ag_cluster-master avoids nodeName2
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
   
   ```bash
   # upgrade mssql-server and mssql-server-ha packages
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```

   ```bash
   # remove the constraint; make sure the resource is started and replica is connected and synchronized
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```

1. Pour une disponibilité groupes avec un gestionnaire de cluster externe - où le type de cluster est EXTERNAL, nettoyez la contrainte d’emplacement qui a été provoquée par le basculement manuel. 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```

1. Reprendre le déplacement des données pour le réplica secondaire qui vient d’être mis à niveau - le réplica principal précédent. Cette étape est requise lorsqu’une instance plus élevée de la version de SQL Server transfère des blocs de journal à une instance de version inférieure dans un groupe de disponibilité. Exécutez la commande suivante sur le nouveau réplica secondaire (réplica principal précédent).

   ```transact-sql
   ALTER DATABASE database_name SET HADR RESUME;
   ```

Après la mise à niveau tous les serveurs, vous pouvez la restaurer automatiquement. Basculez à nouveau vers le serveur principal d’origine - si nécessaire. 

## <a name="drop-an-availability-group"></a>Supprimer un groupe de disponibilité

Pour supprimer un groupe de disponibilité, exécutez [DROP AVAILABILITY GROUP](../t-sql/statements/drop-availability-group-transact-sql.md). Si le type de cluster est `EXTERNAL` ou `NONE` exécutez la commande sur chaque instance de SQL Server qui héberge un réplica. Par exemple, pour supprimer un groupe de disponibilité nommé `group_name` exécutez la commande suivante :

   ```transact-sql
   DROP AVAILABILITY GROUP group_name
   ```
 

## <a name="next-steps"></a>Étapes suivantes

[Configurer le Cluster Red Hat Enterprise Linux pour les ressources de Cluster de groupe de disponibilité de SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Configurer un Cluster SUSE Linux Enterprise Server pour les ressources de Cluster de groupe de disponibilité de SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Configurer le Cluster Ubuntu pour les ressources de Cluster de groupe de disponibilité de SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
