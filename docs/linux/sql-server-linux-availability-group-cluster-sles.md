---
title: "Configurer SLES Cluster pour le groupe de disponibilité de SQL Server | Documents Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 05/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 85180155-6726-4f42-ba57-200bf1e15f4d
ms.workload: Inactive
ms.openlocfilehash: d8ebecb0d6ff5892bdee8cf4cf98287f1ace33e0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="configure-sles-cluster-for-sql-server-availability-group"></a>Configurer SLES Cluster pour le groupe de disponibilité de SQL Server

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Ce guide fournit des instructions pour créer un cluster à trois nœuds pour SQL Server sur SUSE Linux Enterprise Server (SLES) 12 SP2. Pour la haute disponibilité, un groupe de disponibilité sur Linux nécessite trois nœuds, voir [haute disponibilité et protection des données pour les configurations de groupe de disponibilité](sql-server-linux-availability-group-ha.md). La couche de gestion de clusters est basée sur SUSE [haute disponibilité Extension (HAÉ)](https://www.suse.com/products/highavailability) construit sur [STIMULATEUR](http://clusterlabs.org/). 

Pour plus d’informations sur la configuration du cluster, les options de l’agent de ressources, la gestion, meilleures pratiques et recommandations, consultez [SUSE Linux Enterprise haute disponibilité Extension 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html).

>[!NOTE]
>À ce stade, l’intégration de SQL Server avec STIMULATEUR sur Linux n’est pas comme exhaustivement comme WSFC sur Windows. Service SQL Server sur Linux n’est pas compatible avec les clusters. STIMULATEUR gère l’ensemble de l’orchestration de ressources de cluster, y compris la ressource de groupe de disponibilité. Sur Linux, ne vous fiez pas à toujours sur Disponibilité groupe vues de gestion dynamique (DMV) qui fournissent des informations de cluster comme sys.dm_hadr_cluster. En outre, nom de réseau virtuel est spécifique à WSFC, il n’existe aucun équivalent de la même dans STIMULATEUR. Vous pouvez toujours créer un écouteur pour l’utiliser pour la reconnexion après un basculement transparente, mais vous devez inscrire manuellement le nom de l’écouteur sur le serveur DNS avec l’adresse IP utilisée pour créer la ressource IP virtuelle (comme expliqué ci-dessous).


## <a name="roadmap"></a>Feuille de route

Les étapes pour créer un groupe de disponibilité sur des serveurs Linux pour une haute disponibilité sont différentes des étapes sur un cluster de basculement Windows Server. La liste suivante décrit les étapes de haut niveau : 

1. [Configurer SQL Server sur les nœuds de cluster](sql-server-linux-setup.md).

2. [Créer le groupe de disponibilité](sql-server-linux-availability-group-failover-ha.md). 

3. Configurer un gestionnaire de ressources de cluster, comme STIMULATEUR. Ces instructions sont fournies dans ce document.
   
   La façon de configurer un gestionnaire de ressources du cluster dépend de la distribution Linux spécifique. 

   >[!IMPORTANT]
   >Les environnements de production requièrent un agent de délimitation, tels que STONITH pour la haute disponibilité. Les démonstrations dans cette documentation n’utilisent pas les agents de délimitation. Les démonstrations sont pour le test et de validation uniquement. 
   
   >Un cluster STIMULATEUR utilise délimitation pour retourner le cluster à un état connu. La façon de configurer la délimitation dépend de la distribution et l’environnement. À ce stade, la délimitation n’est pas disponible dans certains environnements de cloud. Consultez [SUSE Linux Enterprise haute disponibilité Extension](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing).

5. [Ajouter le groupe de disponibilité en tant que ressource dans le cluster](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server). 

## <a name="prerequisites"></a>Conditions préalables

Pour terminer le scénario de bout en bout ci-dessous, vous avez besoin de trois ordinateurs pour déployer le trois nœuds cluster. Les étapes ci-dessous décrivent comment configurer ces serveurs.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Installer et configurer le système d’exploitation sur chaque nœud de cluster 

La première étape consiste à configurer le système d’exploitation sur les nœuds de cluster. Pour cette procédure pas à pas, utilisez SLES 12 SP2 avec un abonnement valide pour le module complémentaire à haute disponibilité.

### <a name="install-and-configure-sql-server-service-on-each-cluster-node"></a>Installer et configurer le service SQL Server sur chaque nœud de cluster

1. Installer et configurer un service SQL Server sur tous les nœuds. Pour obtenir des instructions détaillées, consultez [installer SQL Server sur Linux](sql-server-linux-setup.md).

1. Désigner un nœud en tant que nœuds principaux et d’autres en tant que bases de données secondaires. Utilisez ces termes tout au long de ce guide.

1. Assurez-vous que les nœuds devant faire partie du cluster peuvent communiquer entre eux.

   L’exemple suivant `/etc/hosts` avec les ajouts de trois nœuds nommés SLES1, SLES2 et SLES3.

   ```
   127.0.0.1   localhost
   10.128.16.33 SLES1
   10.128.16.77 SLES2
   10.128.16.22 SLES3
   ```

   Tous les nœuds de cluster doivent être en mesure des uns aux autres via une connexion SSH. Outils tels que `hb_report` ou `crm_report` (pour la résolution des problèmes) et l’Explorateur de l’historique de Hawk nécessitent un passwordless accès SSH entre les nœuds, sinon ils peuvent uniquement collecter des données à partir du nœud actuel. En cas d’utilisation d’un port SSH non standard, utilisez l’option -X (consultez `man` page). Par exemple, si votre port SSH est 3479, appeler un `crm_report` avec :

   ```bash
   sudo crm_report -X "-p 3479" [...]
   ```

   Pour plus d’informations, consultez la [Guide d’Administration SLES - section divers](http://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.misc).


## <a name="create-a-sql-server-login-for-pacemaker"></a>Créer une connexion SQL Server pour STIMULATEUR

[!INCLUDE [SLES-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="configure-an-always-on-availability-group"></a>Configurer un groupe de disponibilité Always On

Sur des serveurs Linux configurer le groupe de disponibilité, puis configurez les ressources de cluster. Pour configurer le groupe de disponibilité, consultez [configurer groupe de disponibilité AlwaysOn pour SQL Server sur Linux](sql-server-linux-availability-group-configure-ha.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installer et configurer STIMULATEUR sur chaque nœud de cluster

1. Installer l’extension de la haute disponibilité

   Pour référence, consultez [installation SUSE Linux Enterprise Server et l’Extension de haute disponibilité](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.installation)

1. Installer un package de l’agent de ressource SQL Server sur les deux nœuds.

   ```bash
   sudo zypper install mssql-server-ha
   ```

## <a name="set-up-the-first-node"></a>Configurer le premier nœud

   Reportez-vous à [des instructions d’installation SLES](http://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node)

1. Connectez-vous en tant que `root` à l’ordinateur physique ou virtuel à utiliser en tant que nœud de cluster.
2. Démarrez le script de démarrage en exécutant :
   ```bash
   sudo ha-cluster-init
   ```

   NTP n’a pas été configuré pour démarrer au démarrage, un message s’affiche. 

   Si vous décidez de continuer, le script sera automatiquement générer des clés pour l’accès SSH et l’outil de synchronisation Csync2 et démarrer les services nécessaires pour les deux. 

3. Pour configurer la couche de communication du cluster (Corosync) : 

   a. Entrez une adresse réseau à lier. Par défaut, le script va vous proposer l’adresse réseau d’eth0. Vous pouvez également entrer une adresse réseau différente, par exemple l’adresse de bond0. 

   b. Entrez une adresse de multidiffusion. Le script propose une adresse aléatoire que vous pouvez utiliser comme valeur par défaut. 

   c. Entrez un port de multidiffusion. Le script propose 5405 comme valeur par défaut. 

   d. Pour configurer `SBD ()`, entrez un chemin persistant pour la partition de votre appareil de bloc que vous souhaitez utiliser pour le même jour ouvrable. Le chemin d’accès doit être cohérente sur tous les nœuds du cluster. 
   Enfin, le script démarre le service STIMULATEUR pour mettre le cluster d’un nœud en ligne et d’activer l’interface de gestion Web Hawk2. L’URL à utiliser pour Hawk2 s’affiche sur l’écran. 

4. Pour les détails du processus de configuration, consultez `/var/log/sleha-bootstrap.log`. Vous avez maintenant un cluster à un nœud en cours d’exécution. Vérifiez l’état du cluster avec l’état de crm :

   ```bash
   sudo crm status
   ```

   Vous pouvez également consulter la configuration de cluster avec `crm configure show xml` ou `crm configure show`.

5. La procédure de démarrage crée un utilisateur Linux nommé hacluster avec le mot de passe linux. Remplacez le mot de passe par défaut sûre dès que possible : 

   ```bash
   sudo passwd hacluster
   ```

## <a name="add-nodes-to-the-existing-cluster"></a>Ajouter des nœuds au cluster existant

Si vous avez un cluster exécutant avec un ou plusieurs nœuds, ajouter des nœuds de cluster avec le script de démarrage à haute disponibilité cluster-jointure. Le script requiert seulement l’accès à un nœud de cluster existant et terminera automatiquement la configuration de base sur l’ordinateur actuel. Suivez les étapes ci-dessous :

Si vous avez configuré les nœuds de cluster existants avec les `YaST` module de cluster, assurez-vous que les conditions préalables suivantes sont remplies avant d’exécuter `ha-cluster-join`:
- L’utilisateur racine sur les nœuds existants a des clés SSH en place pour la connexion passwordless. 
- `Csync2`est configuré sur les nœuds existants. Pour plus d’informations, reportez-vous à la configuration de Csync2 avec YaST. 

1. Ouvrez une session en tant que racine de l’ordinateur physique ou virtuel censé rejoindre le cluster. 
2. Démarrez le script de démarrage en exécutant : 

   ```bash
   sudo ha-cluster-join
   ```

   NTP n’a pas été configuré pour démarrer au démarrage, un message s’affiche. 

3. Si vous décidez de continuer, le système vous demandera l’adresse IP d’un nœud existant. Entrez l’adresse IP. 

4. Si vous n’avez pas déjà configuré un accès SSH passwordless entre les deux ordinateurs, vous serez également être invité au mot de passe racine du nœud existant. 

   Une fois connecté au nœud spécifié, le script sera copier la configuration Corosync, configurer SSH et `Csync2`et entraîne l’affichage en ligne l’ordinateur actuel en tant que nouveau nœud du cluster. En outre, il démarrera le service requis pour Hawk. Si vous avez configuré le stockage partagé avec `OCFS2`, il créera automatiquement le répertoire de point de montage pour le `OCFS2` système de fichiers. 

5. Répétez les étapes ci-dessus pour tous les ordinateurs que vous souhaitez ajouter au cluster. 

6. Pour obtenir les détails du processus, consultez `/var/log/ha-cluster-bootstrap.log`. 

1. Vérifiez l’état du cluster avec `sudo crm status`. Si vous avez correctement ajouté le deuxième nœud, voici ce que vous obtenez en sortie :

   ```bash
   sudo crm status
   
   3 nodes configured
   1 resource configured
   Online: [ SLES1 SLES2 SLES3]
   Full list of resources:   
   admin_addr     (ocf::heartbeat:IPaddr2):       Started node1
   ```

   >[!NOTE]
   >`admin_addr`est la ressource de cluster IP virtuelle qui est configurée pendant l’installation de cluster à un nœud initial.

Après avoir ajouté tous les nœuds, vérifiez si vous devez ajuster la stratégie quorum non dans les options de cluster global. Cela est particulièrement important pour les clusters à deux nœuds. Pour plus d’informations, reportez-vous à la Section 4.1.2, Option non-quorum-policy. 

## <a name="set-cluster-property-start-failure-is-fatal-to-false"></a>Définissez la propriété cluster start-échec-est-irrécupérable false

`Start-failure-is-fatal`Indique si un échec pour démarrer une ressource sur un nœud empêche d’autres tentatives de démarrage sur ce nœud. Lorsque la valeur `false`, le cluster décide s’il faut essayer de démarrer sur le même nœud en fonction d’actuelle count et migration seuil d’échec la ressource. Par conséquent, une fois le basculement se produit, STIMULATEUR va tenter de démarrage de la ressource de groupe de disponibilité sur l’ancien principal une fois que l’instance SQL est disponible. STIMULATEUR s’occupe de rétrograder le réplica secondaire, et il rejoindra automatiquement le groupe de disponibilité. En outre, si `start-failure-is-fatal` a la valeur `false`, le cluster revient aux limites configurées failcount configurés avec le seuil de la migration, par conséquent, vous devez vous assurer par défaut pour le seuil de migration est mis à jour en conséquence.

Pour mettre à jour la valeur de propriété d’exécution false :
```bash
sudo crm configure property start-failure-is-fatal=false
sudo crm configure rsc_defaults migration-threshold=5000
```
Si la propriété a la valeur par défaut `true`, si la première tentative de démarrage de la ressource échoue, l’intervention de l’utilisateur est requis après un basculement automatique pour nettoyer le nombre d’échecs de ressources et réinitialiser la configuration à l’aide de : `sudo crm resource cleanup <resourceName>` commande.

Pour plus d’informations sur les propriétés du cluster STIMULATEUR, consultez [configuration des ressources de Cluster](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_config_crm_resources.html).

# <a name="configure-fencing-stonith"></a>Configurer la délimitation (STONITH)
Fournisseurs de cluster STIMULATEUR nécessitent STONITH doit être activée et un appareil de délimitation configuré pour une installation de clusters prises en charge. Lorsque le Gestionnaire de ressources de cluster ne peut pas déterminer l’état d’un nœud ou d’une ressource sur un nœud, délimitation est utilisée pour remettre le cluster à un état connu.
Délimitation de niveau de ressources permet de garantir principalement aucune altération des données en cas de panne en configurant une ressource. Vous pouvez utiliser la délimitation au niveau de la ressource, par exemple, avec DRBD (Distributed répliquées bloc Device) pour marquer le disque sur un nœud comme obsolètes lorsque la liaison de communication s’arrête.
Délimitation de niveau de nœud garantit qu’un nœud ne s’exécute pas toutes les ressources. Pour ce faire, vous devez réinitialiser le nœud et l’implémentation de stimulateur de celle-ci est appelée STONITH (ce qui signifie « dépanner l’autre nœud dans l’en-tête »). STIMULATEUR prend en charge une grande variété d’appareils de délimitation, par exemple, une alimentation de secours ou la gestion cartes d’interface pour les serveurs.
Pour plus d’informations, consultez [Clusters STIMULATEUR partant](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html), [délimitation et Stonith](http://clusterlabs.org/doc/crm_fencing.html) et [SUSE HA documentation : délimitation et STONITH](https://www.suse.com/documentation/sle_ha/book_sleha/data/cha_ha_fencing.html).

Au moment de l’initialisation du cluster, STONITH est désactivée si aucune configuration n’est détectée. Il peut être activé ultérieurement par la commande ci-dessous en cours d’exécution

```bash
sudo crm configure property stonith-enabled=true
```
  
>[!IMPORTANT]
>La désactivation de STONITH est uniquement pour des tests. Si vous envisagez d’utiliser STIMULATEUR dans un environnement de production, vous devez planifier une implémentation STONITH en fonction de votre environnement et qu’il soit activé. Notez que SUSE ne fournit pas de délimitation agents Hyper-V ou des environnements de cloud (y compris Azure). Par conséquent, le fournisseur de cluster n’offre pas de prise en charge des clusters de production en cours d’exécution dans ces environnements. Nous travaillons sur une solution pour cet intervalle qui est disponible dans les versions futures.


## <a name="configure-the-cluster-resources-for-sql-server"></a>Configurer les ressources de cluster pour SQL Server

Reportez-vous à [SLES Administration Guid](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.manual_config)

### <a name="create-availability-group-resource"></a>Créer la ressource du groupe de disponibilité

La commande suivante crée et configure la ressource du groupe de disponibilité pour les 3 réplicas du groupe de disponibilité [ag1]. Les opérations d’analyse et les délais d’attente doivent être spécifiés explicitement dans SLES basée sur le fait que des délais d’attente sont fortement dépendant de charge de travail et doivent être ajustés avec soin pour chaque déploiement.
Exécutez la commande sur l’un des nœuds du cluster :

1. Exécutez `crm configure` pour ouvrir l’invite de crm :

   ```bash
   sudo crm configure 
   ```

1. Dans l’invite de crm, exécutez la commande suivante pour configurer les propriétés de ressource.

   ```bash
primitive ag_cluster \
   ocf:mssql:ag \
   params ag_name="ag1" \
   op start timeout=60s \
   op stop timeout=60s \
   op promote timeout=60s \
   op demote timeout=10s \
   op monitor timeout=60s interval=10s \
   op monitor timeout=60s interval=11s role="Master" \
   op monitor timeout=60s interval=12s role="Slave" \
   op notify timeout=60s
ms ms-ag_cluster ag_cluster \
   meta master-max="1" master-node-max="1" clone-max="3" \
  clone-node-max="1" notify="true" \
commit
   ```

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

### <a name="create-virtual-ip-resource"></a>Créer la ressource IP virtuelle

Si vous n’avez pas créé la ressource IP virtuelle lors de l’exécution `ha-cluster-init` vous pouvez créer maintenant cette ressource. La commande suivante crée une ressource IP virtuelle. Remplacez `<**0.0.0.0**>` avec une adresse disponible à partir de votre réseau et `<**24**>` avec le nombre de bits dans le masque de sous-réseau CIDR. Exécutez sur un nœud.

```bash
crm configure \
primitive admin_addr \
   ocf:heartbeat:IPaddr2 \
   params ip=<**0.0.0.0**> \
      cidr_netmask=<**24**>
```

### <a name="add-colocation-constraint"></a>Ajouter une contrainte de colocalisation
Presque chaque décision dans un cluster STIMULATEUR, comme choisir où une ressource doit s’exécuter, s’effectue en comparant les scores. Les scores sont calculés par la ressource et le Gestionnaire de ressources de cluster choisit le nœud avec le score le plus élevé pour une ressource particulière. (Si un nœud possède un score négatif pour une ressource, la ressource ne peut pas s’exécuter sur ce nœud.) Nous pouvons manipuler les décisions du cluster avec des contraintes. Les contraintes ont un score. Si une contrainte a un score inférieur à l’infini, il est uniquement une recommandation. Un score d’infini signifie qu’il est indispensable. Vous souhaitez vous assurer que principal du groupe de disponibilité et virtuel ressource ip sont exécutés sur le même hôte, donc nous allons définir une contrainte de colocalisation avec un score d’infini. 

Pour définir la contrainte de la colocalisation pour l’adresse IP virtuelle pour s’exécuter sur le même nœud que le maître, exécutez la commande suivante sur un nœud :

```bash
crm configure
colocation vip_on_master inf: \
    admin_addr ms-ag_cluster:Master
commit
```

### <a name="add-ordering-constraint"></a>Ajouter la contrainte de classement
La contrainte de colocalisation a une contrainte de classement implicite. Il déplace la ressource IP virtuelle avant de passer la ressource de groupe de disponibilité. Par défaut, la séquence d’événements est : 

1. Ressource de problèmes utilisateur migrer de Nœud1 vers Nœud2 vers le maître du groupe de disponibilité.
2. La ressource IP virtuelle s’arrête sur le nœud 1.
3. La ressource IP virtuelle démarre sur le nœud 2. À ce stade, l’adresse IP temporairement pointe vers le nœud 2 pendant que le nœud 2 est toujours un pre-basculement secondaire. 
4. Le maître du groupe de disponibilité sur le nœud 1 est rétrogradé pour esclave.
5. L’esclave du groupe de disponibilité sur le nœud 2 est promue au masque. 

Pour éviter que l’adresse IP temporairement en pointant sur le nœud avec le serveur secondaire avant le basculement, ajoutez une contrainte de classement. Pour ajouter une contrainte de classement, exécutez la commande suivante sur un nœud : 

```bash
crm crm configure \
   order ag_first inf: ms-ag_cluster:promote admin_addr:start
```


>[!IMPORTANT]
>Une fois que vous configurez le cluster et ajoutez le groupe de disponibilité en tant que ressource de cluster, vous ne pouvez pas utiliser Transact-SQL pour basculer les ressources de groupe de disponibilité. Ressources de cluster de SQL Server sur Linux non couplées aussi étroitement avec le système d’exploitation qu’ils sont sur un Cluster de basculement du serveur Windows (WSFC). Service SQL Server n’est pas informé de la présence du cluster. Orchestration toutes s’effectue via les outils de gestion de cluster. Dans SLES utiliser `crm`. 

Basculer manuellement le groupe de disponibilité avec `crm`. Ne démarrez pas le basculement avec Transact-SQL. Pour obtenir des instructions, consultez [basculement](sql-server-linux-availability-group-failover-ha.md#failover).


Pour plus d’informations, consultez :
- [La gestion des ressources de cluster](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.config.crm).   
- [Haute disponibilité Concepts](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.concepts)
- [Référence rapide de STIMULATEUR](https://github.com/ClusterLabs/pacemaker/blob/master/doc/pcs-crmsh-quick-ref.md) 

<!---[!INCLUDE [Pacemaker Concepts](..\includes\ss-linux-cluster-pacemaker-concepts.md)]--->

## <a name="next-steps"></a>Étapes suivantes

[Utiliser le groupe de disponibilité haute disponibilité](sql-server-linux-availability-group-failover-ha.md)
