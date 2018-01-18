---
title: "Utiliser le groupe de disponibilité SQL Server sur Linux | Documents Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 07/20/2017
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
ms.openlocfilehash: 23eedac40aff1fcab50c2e05406d3c87b988e392
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="operate-always-on-availability-groups-on-linux"></a>Fonctionnent toujours sur les groupes de disponibilité sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

## <a name="failover"></a>Basculer le groupe de disponibilité

Utilisez les outils de gestion de cluster pour basculer un groupe de disponibilité géré par un gestionnaire de cluster externe. Par exemple, si une solution utilise STIMULATEUR pour gérer un cluster Linux, utilisez `pcs` pour effectuer des basculements manuels sur RHEL ou Ubuntu. SLES utiliser `crm`. 

> [!IMPORTANT]
> Dans des conditions normales, ne basculent pas avec des outils de gestion de Transact-SQL ou SQL Server comme SSMS ou PowerShell. Lorsque `CLUSTER_TYPE = EXTERNAL`, la seule valeur acceptable pour `FAILOVER_MODE` est `EXTERNAL`. Avec ces paramètres, toutes les actions de basculement manuel ou automatique sont exécutées par le Gestionnaire de cluster externe. 

### <a name="manual-failover-examples"></a>Exemples de basculement manuel

Basculer manuellement le groupe de disponibilité avec les outils de gestion de cluster externe. Dans des conditions normales, ne démarrez pas le basculement avec Transact-SQL. Si les outils de gestion de cluster externe ne répondent pas, vous pouvez forcer le basculement du groupe de disponibilité. Pour obtenir des instructions forcer le basculement manuel, consultez [manuel déplacer lorsque les outils de cluster ne sont pas réactives](#forceManual).

Terminer le basculement manuel en deux étapes. 

1. Déplacer la ressource du groupe de disponibilité à partir du nœud de cluster qui possède les ressources vers un nouveau nœud.

   Le Gestionnaire du cluster déplace la ressource de groupe de disponibilité et ajoute une contrainte d’emplacement. Cette contrainte configure la ressource à exécuter sur le nouveau nœud. Vous devez supprimer cette contrainte afin de déplacer que soit manuellement ou automatiquement basculer dans le futur.

2. Supprimez la contrainte d’emplacement.

#### <a name="1-manually-fail-over"></a>1. Basculer manuellement

Pour basculer manuellement une ressource de groupe de disponibilité nommée *ag_cluster* au nœud de cluster nommé *Nom_nœud2*, exécutez la commande appropriée pour votre distribution :

- **Exemple RHEL/Ubuntu**

   ```bash
   sudo pcs resource move ag_cluster-master nodeName2 --master
   ```

- **Exemple SLES**

   ```bash
   crm resource migrate ag_cluster nodeName2
   ```



>[!IMPORTANT]
>Après avoir basculé manuellement une ressource, vous devez supprimer une contrainte d’emplacement qui est ajoutée automatiquement au cours du déplacement.

#### <a name="2-remove-the-location-constraint"></a>2. Supprimer la contrainte d’emplacement

Lors d’un déplacement manuel, le `pcs` commande `move` ou `crm` commande `migrate` ajoute une contrainte d’emplacement de la ressource doit être placé sur le nouveau nœud cible. Pour afficher la nouvelle contrainte, exécutez la commande suivante après avoir déplacé manuellement la ressource :

- **Exemple RHEL/Ubuntu**

   ```bash
   sudo pcs constraint --full
   ```

- **Exemple SLES**

   ```bash
   crm config show
   ```

Vous devez supprimer la contrainte d’emplacement pour permettre aux déplacements à venir (y compris le basculement automatique) d’aboutir. 

Pour supprimer la contrainte, exécutez la commande suivante. 

- **Exemple RHEL/Ubuntu**

   Dans cet exemple `ag_cluster-master` est le nom de la ressource qui a été déplacé. 

   ```bash
   sudo pcs resource clear ag_cluster-master 
   ```

- **Exemple SLES**

   Dans cet exemple `ag_cluster` est le nom de la ressource qui a été déplacé. 

   ```bash
   crm resource clear ag_cluster
   ```

Vous pouvez aussi supprimer la contrainte d’emplacement en exécutant la commande ci-dessous.  

- **Exemple RHEL/Ubuntu**

   Dans la commande `cli-prefer-ag_cluster-master` ci-dessous figure l’ID de la contrainte à supprimer. `sudo pcs constraint --full` retourne cet ID. 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```
- **Exemple SLES**

   Dans la commande suivante `cli-prefer-ms-ag_cluster` est l’ID de la contrainte. `crm config show` retourne cet ID. 
   
   ```bash
   crm configure
   delete cli-prefer-ms-ag_cluster 
   commit
   ```

>[!NOTE]
>Comme l’opération de basculement automatique n’ajoute pas de contrainte d’emplacement, aucun nettoyage n’est nécessaire. 

Pour plus d'informations, consultez :
- [Red Hat - Managing Cluster Resources](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/ch-manageresource-HAAR.html) (Red Hat - Gestion des ressources de cluster)
- [STIMULATEUR - déplacer manuellement les ressources](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-pcs/html/Clusters_from_Scratch/_move_resources_manually.html)
 [SLES ressources - Guide d’Administration](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.resource) 
 

### <a name="forceManual"></a>Manuel déplacer lorsque les outils de cluster ne sont pas réactifs 

Dans les cas extrêmes, si un utilisateur ne peut pas utiliser les outils de gestion de cluster pour l’interaction avec le cluster (par exemple, le cluster ne répond pas, les outils de gestion de cluster ont un comportement défectueux), l’utilisateur peut avoir à effectuer un basculement manuel - en ignorant le Gestionnaire du cluster externe. Cela n’est pas recommandée pour les opérations courantes et doit être utilisé dans les cas de cluster ne parvient pas à exécuter l’action de basculement à l’aide des outils de gestion du cluster.

Si vous ne peuvent pas basculer le groupe de disponibilité avec les outils de gestion de cluster, procédez comme suit pour basculer à partir des outils de SQL Server :

1. Vérifiez que la ressource de groupe de disponibilité n’est pas plus gérée par le cluster. 

      - Tentative de définition de la ressource au mode non géré. Cela signale à l’agent de ressource pour arrêter la surveillance des ressources et la gestion. Par exemple : 
      
      ```bash
      sudo pcs resource unmanage <**resourceName**>
      ```

      - Si la tentative de définir le mode de la ressource en mode non managé échoue, supprimez la ressource. Par exemple :

      ```bash
      sudo pcs resource delete <**resourceName**>
      ```

      >[!NOTE]
      >Lorsque vous supprimez une ressource elle supprime également toutes les contraintes associées. 

1. Définir manuellement la variable de contexte de session `external_cluster`.

   ```Transact-SQL
   EXEC sp_set_session_context @key = N'external_cluster', @value = N'yes';
   ```

1. Basculer le groupe de disponibilité avec Transact-SQL. Dans l’exemple ci-dessous, remplacez `<**MyAg**>` par le nom de votre groupe de disponibilité. Connectez-vous à l’instance de SQL Server qui héberge le réplica secondaire cible et exécutez la commande suivante :

   ```Transact-SQL
   ALTER AVAILABILITY GROUP <**MyAg**> FAILOVER;
   ```

1. Redémarrez la gestion et analyse de ressource de cluster. Exécutez la commande suivante :

   ```bash
   sudo pcs resource manage <**resourceName**>
   sudo pcs resource cleanup <**resourceName**>
   ```

## <a name="database-level-monitoring-and-failover-trigger"></a>Déclencheur de surveillance et de basculement au niveau de base de données

Pour `CLUSTER_TYPE=EXTERNAL`, la sémantique de déclencheur de basculement est différente par rapport à WSFC. Lorsque le groupe de disponibilité est sur une instance de SQL Server dans un cluster WSFC, en cours de transition de `ONLINE` pour la base de données provoque l’intégrité du groupe de disponibilité signaler une erreur d’état. Il signale le Gestionnaire du cluster pour déclencher une action de basculement. Sur Linux, l’instance de SQL Server ne peut pas communiquer avec le cluster. Analyse pour le contrôle d’intégrité de la base de données est effectuée « extérieur-in ». Si utilisateur a été sélectionné pour la surveillance de basculement au niveau base de données et de basculement (en définissant l’option `DB_FAILOVER=ON` lors de la création du groupe de disponibilité), le cluster vérifie si l’état de la base de données `ONLINE` chaque fois que lorsqu’elle exécute une action d’analyse. Le cluster interroge l’état dans `sys.databases`. Pour tout état autre que `ONLINE`, cela déclenche un basculement automatique (si les conditions de basculement automatique sont remplies). L’heure réelle du basculement dépend de la fréquence de l’action d’analyse, ainsi que l’état de la base de données en cours de mise à jour dans sys.databases.

## <a name="upgrade-availability-group"></a>Mettre à niveau le groupe de disponibilité

Mettre à niveau un groupe de disponibilité, passez en revue les meilleures pratiques à [la mise à niveau des instances de réplica de groupe de disponibilité](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).

Les sections suivantes expliquent comment effectuer une mise à niveau propagée avec des instances de SQL Server sur Linux avec des groupes de disponibilité. 

### <a name="upgrade-steps-on-linux"></a>Étapes de mise à niveau sur Linux

Lorsque les réplicas du groupe de disponibilité sont sur des instances de SQL Server sous Linux, le type de cluster du groupe de disponibilité est `EXTERNAL` ou `NONE`. Un groupe de disponibilité qui est géré par un gestionnaire de cluster en plus de Cluster de basculement Windows Server (WSFC) est `EXTERNAL`. STIMULATEUR avec Corosync est un exemple d’un gestionnaire de cluster externe. Un groupe de disponibilité avec aucun gestionnaire de cluster a le type de cluster `NONE` les étapes de mise à niveau décrites ici sont spécifiques de groupes de disponibilité de type cluster `EXTERNAL` ou `NONE`.

1. Avant de commencer, sauvegardez chaque base de données.
2. Mettre à niveau des instances de SQL Server qui hébergent les réplicas secondaires.

    A. Mettre à niveau tout d’abord des réplicas secondaires asynchrones.

    B. Mettre à niveau les réplicas secondaires synchrones.

   >[!NOTE]
   >Si un groupe de disponibilité possède uniquement asynchrone réplicas - pour éviter toute perte de données modifiez un réplica synchrone et attendez qu’il est synchronisé. Puis, mettez à niveau de ce réplica.
   
   b.1. Arrêter la ressource sur le nœud qui héberge le réplica secondaire ciblé pour la mise à niveau
   
   Avant d’exécuter la commande de mise à niveau, arrêtez la ressource afin que le cluster ne sera pas surveiller et inutilement d’échouer. L’exemple suivant ajoute une contrainte d’emplacement sur le nœud entraîne sur la ressource doit être arrêtée. Mise à jour `ag_cluster-master` avec le nom de ressource et `nodeName1` avec le nœud qui héberge le réplica ciblé pour la mise à niveau.

   ```bash
   pcs constraint location ag_cluster-master avoids nodeName1
   ```
   b.2. Mise à niveau de SQL Server sur le réplica secondaire

   L’exemple suivant met à niveau `mssql-server` et `mssql-server-ha` packages.

   ```bash
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
   b.3. Supprimer la contrainte d’emplacement

   Avant d’exécuter la commande de mise à niveau, arrêtez la ressource afin que le cluster ne sera pas surveiller et inutilement d’échouer. L’exemple suivant ajoute une contrainte d’emplacement sur le nœud entraîne sur la ressource doit être arrêtée. Mise à jour `ag_cluster-master` avec le nom de ressource et `nodeName1` avec le nœud qui héberge le réplica ciblé pour la mise à niveau.

   ```bash
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```
   Comme meilleure pratique, vérifiez que la ressource est démarrée (à l’aide de `pcs status` commande) et le réplica secondaire est connecté et synchronisé l’état après mise à niveau.

1. Une fois que tous les réplicas secondaires sont mis à niveau, basculez manuellement à un des réplicas secondaires synchrones.

   Pour les groupes de disponibilité avec `EXTERNAL` type de cluster, utilisez les outils de gestion de cluster échec over ; groupes de disponibilité avec `NONE` le type de cluster doit utiliser Transact-SQL à basculer. 
   L’exemple suivant bascule d’un groupe de disponibilité avec les outils de gestion de cluster. Remplacez `<targetReplicaName>` avec le nom du réplica synchrone secondaire qui deviendra principal :

   ```bash
   sudo pcs resource move ag_cluster-master <targetReplicaName> --master  
   ``` 
   
   >[!IMPORTANT]
   >Les étapes suivantes s’appliquent uniquement aux groupes de disponibilité qui n’ont pas un gestionnaire de cluster.  
   Si le type de cluster de groupe de disponibilité est `NONE`manuellement basculer. Exécutez les étapes suivantes dans l'ordre :

      A. La commande suivante définit le réplica principal vers le site secondaire. Remplacez `AG1` par le nom de votre groupe de disponibilité. Exécutez la commande Transact-SQL sur l’instance de SQL Server qui héberge le réplica principal.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY);
      ```

      B. La commande suivante définit un réplica secondaire synchrone principal. Exécutez la commande Transact-SQL suivante sur l’instance cible de SQL Server - l’instance qui héberge le réplica secondaire synchrone.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] FAILOVER;
      ```

1. Après le basculement, mettez à niveau SQL Server sur l’ancien réplica principal en répétant la procédure décrite dans les étapes ci-dessus b.1-b.3.

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

1. Pour un groupes de disponibilité avec un cluster externe manager - où type de cluster est externe, le nettoyage de la contrainte d’emplacement qui a été provoquée par le basculement manuel. 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```

1. Reprendre le déplacement des données pour le réplica secondaire qui vient d’être mis à niveau - l’ancien réplica principal. Cela est nécessaire quand une instance supérieur de la version de SQL Server transfère des blocs de journal à une instance de version inférieure dans un groupe de disponibilité. Exécutez la commande suivante sur le nouveau réplica secondaire (réplica principal précédent).

   ```transact-sql
   ALTER DATABASE database_name SET HADR RESUME;
   ```

Après la mise à niveau tous les serveurs, vous pouvez la restauration automatique - basculez à nouveau vers le serveur principal d’origine - si nécessaire. 

## <a name="drop-an-availability-group"></a>Supprimer un groupe de disponibilité

Pour supprimer un groupe de disponibilité, exécutez [DROP AVAILABILITY GROUP](../t-sql/statements/drop-availability-group-transact-sql.md). Si le type de cluster est `EXTERNAL` ou `NONE` exécuter la commande sur chaque instance de SQL Server qui héberge un réplica. Par exemple, pour supprimer un groupe de disponibilité nommé `group_name` exécutez la commande suivante :

   ```transact-sql
   DROP AVAILABILITY GROUP group_name
   ```
 

## <a name="next-steps"></a>Étapes suivantes

[Configurer Red Hat Enterprise Linux Cluster pour les ressources de Cluster de groupe de disponibilité de SQL Server](sql-server-linux-availability-group-cluster-rhel.md)

[Configurer SUSE Linux Enterprise Server Cluster pour les ressources de Cluster de groupe de disponibilité de SQL Server](sql-server-linux-availability-group-cluster-sles.md)

[Configurer le Cluster Ubuntu pour les ressources de Cluster de groupe de disponibilité de SQL Server](sql-server-linux-availability-group-cluster-ubuntu.md)
