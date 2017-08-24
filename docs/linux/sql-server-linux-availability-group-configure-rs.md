---
title: "Configurer le groupe de disponibilité de montée en puissance parallèle en lecture pour SQL Server sur Linux | Documents Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 06/14/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cf249ff8e6d2e82d1cf413bdec0272e3796b72cb
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="configure-read-scale-out-availability-group-for-sql-server-on-linux"></a>Configurer le groupe de disponibilité de montée en puissance parallèle en lecture pour SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

Vous pouvez configurer un groupe de disponibilité de montée en puissance parallèle en lecture pour SQL Server sur Linux. Il existe deux architectures pour les groupes de disponibilité. A *haute disponibilité* architecture utilise un gestionnaire de cluster pour assurer la continuité améliorée. Cette architecture peut également inclure des réplicas en lecture de montée en puissance parallèle. Pour créer l’architecture haute disponibilité, consultez [configurer toujours sur le groupe de disponibilité pour SQL Server sur Linux](sql-server-linux-availability-group-configure-ha.md).

Ce document explique comment créer un *lecture montée en puissance parallèle* groupe de disponibilité sans un gestionnaire de cluster. Cette architecture offre uniquement la lecture avec montée en charge uniquement. Il ne fournit pas de haute disponibilité.

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-availability-group"></a>Créer le groupe de disponibilité

Créez le groupe de disponibilité. Set `CLUSTER_TYPE = NONE`. En outre, définissez chaque réplica avec `FAILOVER_MODE = NONE`. Les applications clientes analytique en cours d’exécution ou le rapport de charges de travail peut directement se connectent aux bases de données secondaire. Vous pouvez également créer une liste de routage en lecture seule. Connexions au réplica principal avant lire les demandes de connexion à chacun des réplicas secondaires à partir de la liste de routage de manière alternée.

Le script Transact-SQL suivant crée un nom de groupe de disponibilité `ag1`. Le script configure les réplicas du groupe de disponibilité avec `SEEDING_MODE = AUTOMATIC`. Ce paramètre permet à SQL Server créer automatiquement la base de données sur chaque serveur secondaire après son ajout au groupe de disponibilité. Mettre à jour le script suivant pour votre environnement. Remplacez le `**<node1>**` et `**<node2>**` valeurs avec les noms des instances de SQL Server qui hébergent les réplicas. Remplacez le `**<5022>**` avec le port que vous définissez pour le point de terminaison. Exécutez l’instruction Transact-SQL suivant sur le réplica principal de SQL Server :

```Transact-SQL
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'**<node1>**' WITH (
            ENDPOINT_URL = N'tcp://**<node1>:**<5022>**',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'**<node2>**' WITH ( 
            ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**', 
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );
        
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-servers-to-the-availability-group"></a>Joindre des serveurs SQL secondaires au groupe de disponibilité

Le script Transact-SQL suivant joint un serveur à un groupe de disponibilité nommé `ag1`. Mettre à jour le script pour votre environnement. Sur chaque réplica secondaire de SQL Server, exécutez Transact-SQL suivant pour rejoindre le groupe de disponibilité.

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

Ce n’est pas une configuration à haute disponibilité, si vous avez besoin d’une haute disponibilité, suivez les instructions à [configurer groupe de disponibilité AlwaysOn pour SQL Server sur Linux](sql-server-linux-availability-group-configure-ha.md). En particulier, créez le groupe de disponibilité avec `CLUSTER_TYPE=WSFC` (sous Windows) ou `CLUSTER_TYPE=EXTERNAL` (dans Linux) et s’intégrer à un gestionnaire de cluster - WSFC sur Windows ou STIMULATEUR sur Linux.

## <a name="connect-to-read-only-secondary-replicas"></a>Se connecter à des réplicas secondaires en lecture seule

Il existe deux façons de se connecter aux réplicas secondaires en lecture seule. Les applications peuvent se connecter directement à l’instance de SQL Server qui héberge le réplica secondaire et les bases de données de requête, ou ils peuvent utiliser le routage en lecture seule. routage en lecture seule requiert un port d’écoute.

[Réplicas secondaires lisibles](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)

[routage en lecture seule](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-primary-replica-on-read-scale-out-availability-group"></a>Basculer le réplica principal sur le groupe de disponibilité de montée en puissance parallèle en lecture

Chaque groupe de disponibilité possède uniquement un réplica principal. Le réplica principal lit et écrit. Pour modifier le réplica qui est le serveur principal, vous pouvez basculer. Dans un groupe de disponibilité pour la haute disponibilité, le Gestionnaire du cluster automatise dans le processus de basculement. Dans un groupe de disponibilité de montée en puissance parallèle en lecture, le processus de basculement est manuel. Il existe deux façons de basculer sur le réplica principal dans un groupe de disponibilité de l’échelle de lecture.

- Forcé basculement manuel sur avec perte de données

- Manuel de basculement sans perte de données

### <a name="forced-fail-over-with-data-loss"></a>Basculement forcé avec perte de données

Utilisez cette méthode lorsque le réplica principal n’est pas disponible et ne peut pas être récupéré. Vous trouverez plus d’informations sur le basculement forcé avec une perte de données à [effectuer un basculement manuel forcé](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).

Forcez le basculement avec perte de données, connectez-vous à l’instance SQL qui héberge le réplica secondaire cible et exécuter :
```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

### <a name="manual-fail-over-without-data-loss"></a>Manuel de basculement sans perte de données

Utilisez cette méthode lorsque le réplica principal est disponible, mais vous devez temporairement ou définitivement modifier la configuration et de modifier l’instance SQL Server qui héberge le réplica principal. Avant d’émettre le basculement manuel sur, assurez-vous que le réplica secondaire cible est à jour, pour qu’il n’y a aucune perte de données potentielle. 

Les étapes suivantes décrivent comment procéder manuellement au basculement sans perte de données :

1. Effectuer la validation synchrone de réplica secondaire cible.

   ```Transact-SQL
   ALTER AVAILABILITY GROUP [ag1] MODIFY REPLICA ON N'**<node2>*' WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```
1. Mise à jour `required_synchronized_secondaries_to_commit`à 1.

   Ce paramètre garantit que chaque transaction active est validée dans le réplica principal et au moins un réplica synchrone secondaire. Le groupe de disponibilité est prêt à effectuer le basculement lorsque le synchronization_state_desc est synchronisé et les numéros de séquence est le même pour les deux principaux et le réplica secondaire cible. Exécutez cette requête à vérifier :

   ```Transact-SQL
   SELECT ag.name, 
      drs.database_id, 
      drs.group_id, 
      drs.replica_id, 
      drs.synchronization_state_desc, 
      ag.sequence_number
   FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
   WHERE drs.group_id = ag.group_id; 
   ```

1. Rétrograder le réplica principal au réplica secondaire. Une fois le réplica principal est rétrogradé, il est en lecture seule. Exécutez cette commande sur l’instance SQL hébergeant le réplica principal pour mettre à jour le rôle de base de données secondaire :

   ```Transact-SQL
   ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY); 
   ```

1. Promouvoir le réplica secondaire cible principale. 

   ```Transact-SQL
   ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ```  

   > [!NOTE] 
   > Pour supprimer un groupe de disponibilité utiliser [DROP AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/drop-availability-group-transact-sql). Pour un groupe de disponibilité créé avec CLUSTER_TYPE NONE ou externe, la commande doit être exécutée sur toutes les parties de réplicas du groupe de disponibilité.

## <a name="next-steps"></a>Étapes suivantes

[Configurer le groupe de disponibilité distribué](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)

[En savoir plus sur les groupes de disponibilité](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)


