---
title: Configurer un Cluster SLES pour le groupe de disponibilité de SQL Server | Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 04/30/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 85180155-6726-4f42-ba57-200bf1e15f4d
ms.openlocfilehash: dc6298c55104aeabcf2da799be4ed1977ea39620
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38057327"
---
# <a name="configure-sles-cluster-for-sql-server-availability-group"></a>Configurer un Cluster SLES pour le groupe de disponibilité de SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce guide fournit des instructions pour créer un cluster à trois nœuds pour SQL Server sur SUSE Linux Enterprise Server (SLES) 12 SP2. Pour la haute disponibilité, un groupe de disponibilité sur Linux nécessite trois nœuds, consultez [haute disponibilité et protection des données pour les configurations de groupe de disponibilité](sql-server-linux-availability-group-ha.md). La couche de clustering est basée sur SUSE [haute disponibilité Extension (HAÉ)](https://www.suse.com/products/highavailability) , construit sur [Pacemaker](http://clusterlabs.org/). 

Pour plus d’informations sur la configuration du cluster, les options de l’agent de ressource, la gestion, meilleures pratiques et recommandations, consultez [SUSE Linux Enterprise haute disponibilité Extension 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html).

>[!NOTE]
>À ce stade, l’intégration de SQL Server avec Pacemaker sur Linux n’est pas aussi couplée comme avec WSFC sous Windows. Service SQL Server sur Linux n’est pas compatible avec les clusters. Pacemaker gère l’ensemble de l’orchestration de ressources de cluster, y compris la ressource de groupe de disponibilité. Sur Linux, vous fiez pas à toujours sur Disponibilité groupe vues de gestion dynamique (DMV) qui fournissent des informations de cluster comme sys.dm_hadr_cluster. En outre, nom de réseau virtuel est spécifique à WSFC, il n’existe aucun équivalent de la même façon dans Pacemaker. Vous pouvez toujours créer un écouteur pour l’utiliser pour une reconnexion après un basculement transparente, mais vous devrez inscrire manuellement le nom de l’écouteur sur le serveur DNS avec l’adresse IP utilisée pour créer la ressource d’adresse IP virtuelle (comme expliqué dans les sections suivantes).


## <a name="roadmap"></a>Feuille de route

La procédure de création d’un groupe de disponibilité pour la haute disponibilité diffère entre les serveurs Linux et d’un cluster de basculement Windows Server. La liste suivante décrit les étapes principales : 

1. [Configurer SQL Server sur les nœuds de cluster](sql-server-linux-setup.md).

2. [Créer le groupe de disponibilité](sql-server-linux-availability-group-failover-ha.md). 

3. Configurer un gestionnaire de ressources de cluster, tels que Pacemaker. Ces instructions sont fournies dans ce document.
   
   La façon de configurer un gestionnaire de ressources de cluster dépend de la distribution de Linux spécifique. 

   >[!IMPORTANT]
   >Les environnements de production nécessitent un agent de délimitation, tels que STONITH pour la haute disponibilité. Les exemples de cet article n’utilisent pas les agents de délimitation. Ils sont pour le test et validation uniquement. 
   
   >Un cluster Pacemaker utilise délimitation pour retourner le cluster à un état connu. La façon de configurer la délimitation dépend de la distribution et l’environnement. À ce stade, la délimitation n’est pas disponible dans certains environnements de cloud. Consultez [Extension de haute disponibilité SUSE Linux Enterprise](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing).

5. [Ajouter le groupe de disponibilité en tant que ressource dans le cluster](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server). 

## <a name="prerequisites"></a>Prérequis

Pour terminer le scénario de bout en bout suivant, vous avez besoin de trois ordinateurs pour déployer le cluster de trois nœuds. Les étapes suivantes décrivent comment configurer ces serveurs.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Installer et configurer le système d’exploitation sur chaque nœud de cluster 

La première étape consiste à configurer le système d’exploitation sur les nœuds de cluster. Pour cette procédure pas à pas, utilisez SLES 12 SP2 avec un abonnement valide pour le module complémentaire de haute disponibilité.

### <a name="install-and-configure-sql-server-service-on-each-cluster-node"></a>Installer et configurer le service SQL Server sur chaque nœud de cluster

1. Installer et configurer le service SQL Server sur tous les nœuds. Pour obtenir des instructions détaillées, consultez [installer SQL Server sur Linux](sql-server-linux-setup.md).

1. Désignez un seul nœud en tant que nœuds principaux et d’autres bases de données secondaires. Utiliser ces termes tout au long de ce guide.

1. Assurez-vous que les nœuds sont va faire partie du cluster peuvent communiquer entre eux.

   L’exemple suivant `/etc/hosts` avec des ajouts pour trois nœuds nommés SLES1, SLES2 et SLES3.

   ```
   127.0.0.1   localhost
   10.128.16.33 SLES1
   10.128.16.77 SLES2
   10.128.16.22 SLES3
   ```

   Tous les nœuds de cluster doivent être en mesure des uns aux autres via SSH. Outils tels que `hb_report` ou `crm_report` (pour le dépannage) et l’Explorateur de l’historique de Hawk nécessitent l’accès SSH sans mot de passe entre les nœuds, sinon ils peuvent collecter que les données à partir du nœud actuel. Au cas où vous utilisez un port SSH non standard, utilisez l’option-X (consultez `man` page). Par exemple, si votre port SSH est le 3479, appeler un `crm_report` avec :

   ```bash
   sudo crm_report -X "-p 3479" [...]
   ```

   Pour plus d’informations, consultez le [Guide d’Administration SLES - section divers](http://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.misc).


## <a name="create-a-sql-server-login-for-pacemaker"></a>Créer une connexion SQL Server pour Pacemaker

[!INCLUDE [SLES-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="configure-an-always-on-availability-group"></a>Configurer un groupe de disponibilité Always On

Sur des serveurs Linux, configurez le groupe de disponibilité, puis configurez les ressources de cluster. Pour configurer le groupe de disponibilité, consultez [configurer groupe de disponibilité AlwaysOn pour SQL Server sur Linux](sql-server-linux-availability-group-configure-ha.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installer et configurer Pacemaker sur chaque nœud de cluster

1. Installer l’extension de haute disponibilité

   Pour référence, consultez [l’installation de SUSE Linux Enterprise Server et l’Extension de haute disponibilité](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.installation)

1. Installer le package de l’agent de ressources de SQL Server sur les deux nœuds.

   ```bash
   sudo zypper install mssql-server-ha
   ```

## <a name="set-up-the-first-node"></a>Configurer le premier nœud

   Reportez-vous à [instructions d’installation SLES](http://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node)

1. Connectez-vous en tant que `root` à l’ordinateur physique ou virtuel à utiliser en tant que nœud de cluster.
2. Démarrez le script de démarrage en exécutant :
   ```bash
   sudo ha-cluster-init
   ```

   NTP n’a pas été configuré pour démarrer au moment du démarrage, un message s’affiche. 

   Si vous décidez de continuer malgré tout, le script génère des clés pour l’accès SSH et de l’outil de synchronisation Csync2 automatiquement et démarrer les services nécessaires pour les deux. 

3. Pour configurer la couche de communication de cluster (Corosync) : 

   A. Entrez une adresse réseau à lier. Par défaut, le script propose l’adresse réseau d’eth0. Vous pouvez également entrer une adresse réseau différente, par exemple l’adresse de bond0. 

   B. Entrez une adresse de multidiffusion. Le script propose une adresse aléatoire que vous pouvez utiliser comme valeur par défaut. 

   c. Entrez un port de multidiffusion. Le script propose 5405 comme valeur par défaut. 

   d. Pour configurer `SBD ()`, entrez un chemin d’accès persistant pour la partition de votre appareil de bloc que vous souhaitez utiliser pour SBD. Le chemin d’accès doit être cohérente sur tous les nœuds du cluster. 
   Enfin, le script démarre le service Pacemaker pour mettre le cluster d’un nœud en ligne et activer l’interface de gestion Web Hawk2. L’URL à utiliser pour Hawk2 s’affiche sur l’écran. 

4. Pour les détails du processus de configuration, consultez `/var/log/sleha-bootstrap.log`. Vous disposez maintenant d’un cluster à un nœud en cours d’exécution. Vérifiez l’état du cluster avec l’état de crm :

   ```bash
   sudo crm status
   ```

   Vous pouvez également voir la configuration de cluster avec `crm configure show xml` ou `crm configure show`.

5. La procédure de démarrage crée un utilisateur Linux nommé hacluster avec le mot de passe linux. Remplacez le mot de passe par défaut avec un fichier sécurisé dès que possible : 

   ```bash
   sudo passwd hacluster
   ```

## <a name="add-nodes-to-the-existing-cluster"></a>Ajouter des nœuds au cluster existant

Si vous avez un cluster en cours d’exécution avec un ou plusieurs nœuds, ajoutez plus de nœuds de cluster avec le script de démarrage ha-cluster-join. Le script requiert seulement l’accès à un nœud de cluster existant et effectue automatiquement la configuration de base sur l’ordinateur actuel. Procédez comme suit :

Si vous avez configuré les nœuds de cluster existants avec la `YaST` module d’un cluster, assurez-vous que les conditions préalables suivantes sont remplies avant d’exécuter `ha-cluster-join`:
- L’utilisateur racine sur les nœuds existants a des clés SSH en place pour la méthode de connexion. 
- `Csync2` est configuré sur les nœuds existants. Pour plus d’informations, consultez Configuration de Csync2 avec YaST. 

1. Connectez-vous en tant que racine à l’ordinateur physique ou virtuel censé rejoindre le cluster. 
2. Démarrez le script de démarrage en exécutant : 

   ```bash
   sudo ha-cluster-join
   ```

   NTP n’a pas été configuré pour démarrer au moment du démarrage, un message s’affiche. 

3. Si vous décidez de continuer, vous demandera l’adresse IP d’un nœud existant. Entrez l’adresse IP. 

4. Si vous n’avez pas déjà configuré un accès SSH sans mot de passe entre les deux ordinateurs, vous également demandera le mot de passe racine du nœud existant. 

   Après vous être connecté au nœud spécifié, le script copie la configuration de Corosync, configure SSH et `Csync2`et met l’ordinateur actuel en ligne en tant que nouveau nœud de cluster. Mis à part cela, il démarre le service requis pour Hawk. Si vous avez configuré le stockage partagé avec `OCFS2`, il crée également automatiquement le point de montage répertoire pour la `OCFS2` système de fichiers. 

5. Répétez les étapes précédentes pour tous les ordinateurs que vous souhaitez ajouter au cluster. 

6. Pour plus d’informations du processus, consultez `/var/log/ha-cluster-bootstrap.log`. 

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
   >`admin_addr` est la ressource de cluster IP virtuelle qui est configurée pendant l’installation de cluster à un nœud initial.

Après avoir ajouté tous les nœuds, vérifiez si vous avez besoin d’ajuster la stratégie quorum non dans les options de cluster global. Cela est particulièrement important pour les clusters à deux nœuds. Pour plus d’informations, consultez la Section 4.1.2, Option non-quorum-policy. 

## <a name="set-cluster-property-cluster-recheck-interval"></a>Définir la propriété cluster cluster-revérification-intervalle

`cluster-recheck-interval` Indique l’intervalle d’interrogation à laquelle le cluster vérifie les modifications dans les paramètres de ressource, de contraintes ou d’autres options de cluster. Si un réplica tombe en panne, le cluster tente de redémarrer le réplica à un intervalle qui est lié par le `failure-timeout` valeur et le `cluster-recheck-interval` valeur. Par exemple, si `failure-timeout` est définie sur 60 secondes et `cluster-recheck-interval` est définie sur 120 secondes, le redémarrage est tenté à un intervalle est supérieur à 60 secondes et inférieure à 120 secondes. Nous vous recommandons de définir d’expiration de l’échec à 60 s et revérifie-cluster-intervalle à une valeur qui est supérieure à 60 secondes. Définissant l’intervalle de revérification de cluster sur une valeur faible n’est pas recommandée.

Pour mettre à jour la valeur de propriété à `2 minutes` exécuter :

```bash
crm configure property cluster-recheck-interval=2min
```

> [!IMPORTANT] 
> Si vous disposez déjà d’une ressource de groupe de disponibilité gérée par un cluster Pacemaker, notez que toutes les distributions qui utilisent le dernier package 1.1.18-11.el7 Pacemaker disponible introduisent un changement de comportement pour le cluster start-échec-est-irrécupérable paramètre lorsque son la valeur est false. Cette modification affecte le flux de travail de basculement. Si un réplica principal connaît une panne, le cluster est prévu pour basculer vers un des réplicas secondaires disponibles. Au lieu de cela, les utilisateurs constatent que le cluster continue d’essayer de démarrer le réplica principal a échoué. Si ce principal est jamais en ligne (en raison d’une panne permanente), le cluster bascule jamais vers un autre réplica secondaire disponible. Grâce à cette modification, une configuration précédemment recommandée pour définir le début-échec-est-irrécupérable n’est plus valide et que le paramètre doit être rétablie à sa valeur par défaut de `true`. En outre, la ressource de groupe de disponibilité doit être mis à jour pour inclure le `failover-timeout` propriété. 
>
>Pour mettre à jour la valeur de propriété à `true` exécuter :
>
>```bash
>crm configure property start-failure-is-fatal=true
>```
>
>Mettre à jour de votre propriété de ressource de groupe de disponibilité existante `failure-timeout` à `60s` exécuter (remplacez `ag1` par le nom de votre ressource de groupe de disponibilité) : 
>
>```bash
>crm configure edit ag1
># In the text editor, add `meta failure-timeout=60s` after any `param`s and before any `op`s
>```

Pour plus d’informations sur les propriétés du cluster Pacemaker, consultez [configuration des ressources de Cluster](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_config_crm_resources.html).

# <a name="configure-fencing-stonith"></a>Configurer la délimitation (STONITH)
Fournisseurs de cluster pacemaker nécessitent STONITH doit être activé et un appareil de délimitation configuré pour une configuration de cluster pris en charge. Lorsque le Gestionnaire de ressources de cluster ne peut pas déterminer l’état d’un nœud ou d’une ressource sur un nœud, la délimitation est utilisée pour mettre le cluster à un état connu à nouveau.

Délimitation de niveau ressource garantit principalement qu’il n’existe aucune altération des données en cas de panne en configurant une ressource. Vous pouvez utiliser la délimitation au niveau de la ressource, par exemple, avec DRBD (Distributed répliquées bloc appareil) pour marquer le disque sur un nœud comme obsolètes lorsque la liaison de communication tombe en panne.

Délimitation de niveau de nœud garantit qu’un nœud ne s’exécute pas toutes les ressources. Cela est effectué en réinitialisant le nœud et l’implémentation de Pacemaker de celui-ci est appelée STONITH (ce qui signifie « dépanner l’autre nœud dans la tête »). Pacemaker prend en charge une grande variété de périphériques, tels que d’un onduleur approvisionnement ou gestion des cartes d’interface pour les serveurs de clôture.

Pour plus d’informations, consultez [Clusters Pacemaker à partir de zéro](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html), [délimitation et Stonith](http://clusterlabs.org/doc/crm_fencing.html) et [haute disponibilité SUSE documentation : délimitation et STONITH](https://www.suse.com/documentation/sle_ha/book_sleha/data/cha_ha_fencing.html).

Au moment de l’initialisation du cluster, STONITH est désactivé si aucune configuration n’est détectée. Il peut être activé ultérieurement en exécutant la commande suivante :

```bash
sudo crm configure property stonith-enabled=true
```
  
>[!IMPORTANT]
>La désactivation de STONITH est uniquement pour des fins de test. Si vous envisagez d’utiliser Pacemaker dans un environnement de production, vous devez planifier une implémentation de STONITH en fonction de votre environnement et laissez cette option activée. SUSE ne fournit pas d’agents de délimitation pour les environnements de cloud (y compris Azure) ou l’Hyper-V. Par conséquent, le fournisseur de cluster n’offre pas de prise en charge pour les clusters de production en cours d’exécution dans ces environnements. Nous travaillons sur une solution pour cet écart qui est disponible dans les versions futures.


## <a name="configure-the-cluster-resources-for-sql-server"></a>Configurer les ressources de cluster pour SQL Server

Reportez-vous à [SLES Administration Guid](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.manual_config)

### <a name="create-availability-group-resource"></a>Créer une ressource de groupe de disponibilité

La commande suivante crée et configure la ressource de groupe de disponibilité pour les trois réplicas du groupe de disponibilité [ag1]. Le surveiller les opérations et les délais d’expiration doit être spécifié explicitement dans SLES basé sur le fait que des délais d’expiration sont fortement dépendants de la charge de travail et doivent être soigneusement ajustés pour chaque déploiement.
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
      meta failure-timeout=60s \
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

### <a name="create-virtual-ip-resource"></a>Créer la ressource d’adresse IP virtuelle

Si vous n’avez pas créé la ressource d’adresse IP virtuelle lorsque vous avez exécuté `ha-cluster-init` vous pouvez créer cette ressource maintenant. La commande suivante crée une ressource d’adresse IP virtuelle. Remplacez `<**0.0.0.0**>` avec une adresse disponible à partir de votre réseau et `<**24**>` avec le nombre de bits dans le masque de sous-réseau CIDR. Exécuter sur un nœud.

```bash
crm configure \
primitive admin_addr \
   ocf:heartbeat:IPaddr2 \
   params ip=<**0.0.0.0**> \
      cidr_netmask=<**24**>
```

### <a name="add-colocation-constraint"></a>Ajouter une contrainte de colocalisation
Presque chaque décision dans un cluster Pacemaker, comme choisir où une ressource doit s’exécuter, est effectuée en comparant les scores. Scores sont calculés par ressource, et le Gestionnaire de ressources de cluster choisit le nœud avec le score le plus élevé pour une ressource particulière. (Si un nœud a un score négatif pour une ressource, la ressource ne peut pas s’exécuter sur ce nœud.) Nous pouvons manipuler les décisions du cluster avec des contraintes. Les contraintes ont un score. Si une contrainte a un score inférieur à l’infini, il est uniquement une recommandation. Un score d’infini signifie qu’il est indispensable. Nous voulons vérifier que principal du groupe de disponibilité et virtuel ressource ip sont exécutées sur le même hôte, nous le définissons une contrainte de colocalisation avec un score d’infini. 

Pour définir la contrainte de colocalisation pour l’adresse IP virtuelle pour s’exécuter sur le même nœud que le maître, exécutez la commande suivante sur un nœud :

```bash
crm configure
colocation vip_on_master inf: \
    admin_addr ms-ag_cluster:Master
commit
```

### <a name="add-ordering-constraint"></a>Ajouter une contrainte de classement
La contrainte de colocalisation a une contrainte de classement implicite. Il déplace la ressource d’adresse IP virtuelle avant de poursuivre la ressource de groupe de disponibilité. Par défaut, la séquence d’événements est : 

1. Ressource de problèmes utilisateur migrer vers le maître du groupe de disponibilité de Nœud1 vers Nœud2.
2. La ressource d’adresse IP virtuelle s’arrête sur le nœud 1.
3. La ressource d’adresse IP virtuelle démarre sur le nœud 2. À ce stade, l’adresse IP temporairement pointe vers le nœud 2 pendant que le nœud 2 est toujours un basculement antérieur secondaire. 
4. Le maître du groupe de disponibilité sur le nœud 1 est rétrogradé pour subordonné.
5. Le subordonné de groupe de disponibilité sur le nœud 2 est promu à maîtriser. 

Pour empêcher l’adresse IP de temporairement pointant vers le nœud avec la base de données secondaire pre-basculement, ajoutez une contrainte de classement. Pour ajouter une contrainte de classement, exécutez la commande suivante sur un nœud : 

```bash
crm crm configure \
   order ag_first inf: ms-ag_cluster:promote admin_addr:start
```


>[!IMPORTANT]
>Après avoir configuré le cluster et ajouter le groupe de disponibilité en tant que ressource de cluster, vous ne pouvez pas utiliser Transact-SQL pour basculer les ressources de groupe de disponibilité. Ressources de cluster de SQL Server sur Linux sont couplés pas aussi étroitement avec le système d’exploitation tels qu’ils sont sur un Cluster de basculement du serveur Windows (WSFC). Service SQL Server n’est pas informé de la présence du cluster. Tous les orchestration s’effectue via les outils de gestion de cluster. Dans SLES utiliser `crm`. 

Basculer manuellement le groupe de disponibilité avec `crm`. Ne pas lancer un basculement avec Transact-SQL. Pour plus d’informations, consultez [basculement](sql-server-linux-availability-group-failover-ha.md#failover).


Pour plus d'informations, consultez :
- [La gestion des ressources de cluster](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.config.crm).   
- [Haute disponibilité Concepts](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.concepts)
- [Référence rapide pacemaker](https://github.com/ClusterLabs/pacemaker/blob/master/doc/pcs-crmsh-quick-ref.md) 

<!---[!INCLUDE [Pacemaker Concepts](..\includes\ss-linux-cluster-pacemaker-concepts.md)]--->

## <a name="next-steps"></a>Étapes suivantes

[Utiliser le groupe de disponibilité de haute disponibilité](sql-server-linux-availability-group-failover-ha.md)
