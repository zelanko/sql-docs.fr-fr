---
title: "Configurez un groupe de disponibilité de la lecture à l’échelle pour SQL Server sur Linux | Documents Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 10/20/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 
ms.workload: Inactive
ms.openlocfilehash: 96be9d968286f44b23748041b2beeb1383f63964
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="configure-a-read-scale-availability-group-for-sql-server-on-linux"></a>Configurez un groupe de disponibilité de la lecture à l’échelle pour SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Vous pouvez configurer un groupe de disponibilité de la lecture à l’échelle pour SQL Server sur Linux. Il existe deux architectures pour les groupes de disponibilité. Une architecture haute disponibilité utilise un gestionnaire de cluster pour assurer la continuité améliorée. Cette architecture peut également inclure des réplicas de la lecture à l’échelle. Pour créer l’architecture haute disponibilité, consultez [configurer un groupe de disponibilité AlwaysOn pour SQL Server sur Linux](sql-server-linux-availability-group-configure-ha.md).

Ce document explique comment créer un groupe de disponibilité de la lecture à l’échelle sans un gestionnaire de cluster. Cette architecture fournit à l’échelle en lecture uniquement. Il ne fournit pas une haute disponibilité.

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-availability-group"></a>Créer le groupe de disponibilité

Créez le groupe de disponibilité. Set `CLUSTER_TYPE = NONE`. En outre, définissez chaque réplica avec `FAILOVER_MODE = NONE`. Les applications clientes analytique en cours d’exécution ou le rapport de charges de travail peut directement se connectent aux bases de données secondaire. Vous pouvez également créer une liste de routage en lecture seule. Connexions au réplica principal avant lire les demandes de connexion à chacun des réplicas secondaires à partir de la liste de routage de manière alternée.

Le script Transact-SQL suivant crée un groupe de disponibilité nommé `ag1`. Le script configure les réplicas du groupe de disponibilité avec `SEEDING_MODE = AUTOMATIC`. Ce paramètre permet à SQL Server créer automatiquement la base de données sur chaque serveur secondaire après son ajout au groupe de disponibilité. Mettre à jour le script suivant pour votre environnement. Remplacez le `**<node1>**` et `**<node2>**` valeurs avec les noms des instances de SQL Server qui hébergent les réplicas. Remplacez le `**<5022>**` valeur avec le port que vous définissez pour le point de terminaison. Exécutez le script Transact-SQL suivant sur le réplica principal de SQL Server :

```SQL
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

Le script Transact-SQL suivant joint un serveur à un groupe de disponibilité nommé `ag1`. Mettre à jour le script pour votre environnement. Sur chaque réplica secondaire de SQL Server, exécutez le script Transact-SQL suivant pour rejoindre le groupe de disponibilité :

```SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../includes/ss-linux-cluster-availability-group-create-post.md)]

Ce groupe de disponibilité n’est pas une configuration à haute disponibilité. Si vous avez besoin d’une haute disponibilité, suivez les instructions à [configurer un groupe de disponibilité AlwaysOn pour SQL Server sur Linux](sql-server-linux-availability-group-configure-ha.md). En particulier, créez le groupe de disponibilité avec `CLUSTER_TYPE=WSFC` (sous Windows) ou `CLUSTER_TYPE=EXTERNAL` (dans Linux). Puis intégrer un gestionnaire de cluster à l’aide soit Windows Server clustering de basculement sur Windows ou STIMULATEUR sur Linux.

## <a name="connect-to-read-only-secondary-replicas"></a>Se connecter à des réplicas secondaires en lecture seule

Il existe deux façons de se connecter à des réplicas secondaires en lecture seule. Les applications peuvent se connecter directement à l’instance de SQL Server qui héberge le réplica secondaire et les bases de données de requête. Également pouvoir utiliser le routage en lecture seule, ce qui nécessite un port d’écoute.

* [Réplicas secondaires lisibles](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [Routage en lecture seule](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>Basculer le réplica principal sur un groupe de disponibilité avec échelle lecture

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>Étapes suivantes

* [Configurer un groupe de disponibilité distribué](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)
* [En savoir plus sur les groupes de disponibilité](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)
* [Effectuer un basculement manuel forcé](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)

