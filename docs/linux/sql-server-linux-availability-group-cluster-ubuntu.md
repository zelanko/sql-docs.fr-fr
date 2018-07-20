---
title: Configurer le Cluster Ubuntu pour le groupe de disponibilité de SQL Server | Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: dd0d6fb9-df0a-41b9-9f22-9b558b2b2233
ms.openlocfilehash: 48a6ed32b8b0898d44c28a425064ef46fc1e1561
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083131"
---
# <a name="configure-ubuntu-cluster-and-availability-group-resource"></a>Configurer le Cluster d’Ubuntu et les ressources du groupe de disponibilité

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce document explique comment créer un cluster à trois nœuds sur Ubuntu et ajouter un groupe de disponibilité créé précédemment en tant que ressource dans le cluster. Pour la haute disponibilité, un groupe de disponibilité sur Linux nécessite trois nœuds, consultez [haute disponibilité et protection des données pour les configurations de groupe de disponibilité](sql-server-linux-availability-group-ha.md).

> [!NOTE] 
> À ce stade, l’intégration de SQL Server avec Pacemaker sur Linux n’est pas aussi couplée comme avec WSFC sous Windows. Dans SQL, il n’est aucune connaissance de la présence du cluster, tous les l’orchestration est en dehors de, et le service est contrôlé en tant qu’une instance autonome par Pacemaker. En outre, nom de réseau virtuel est spécifique à WSFC, il n’existe aucun équivalent de la même façon dans Pacemaker. Toujours sur des vues de gestion dynamique qui interrogent des informations de cluster retournent des lignes vides. Vous pouvez toujours créer un écouteur pour l’utiliser pour une reconnexion après un basculement transparente, mais vous devez inscrire manuellement le nom de l’écouteur sur le serveur DNS avec l’adresse IP utilisée pour créer la ressource d’adresse IP virtuelle (comme expliqué dans les sections suivantes).

Les sections suivantes guident à travers les étapes pour configurer une solution de cluster de basculement. 

## <a name="roadmap"></a>Feuille de route

Les étapes pour créer un groupe de disponibilité sur des serveurs Linux pour la haute disponibilité sont différentes de la procédure sur un cluster de basculement Windows Server. La liste suivante décrit les étapes principales : 

1. [Configurer SQL Server sur les nœuds de cluster](sql-server-linux-setup.md).

2. [Créer le groupe de disponibilité](sql-server-linux-availability-group-configure-ha.md). 

3. Configurer un gestionnaire de ressources de cluster, tels que Pacemaker. Ces instructions sont fournies dans ce document.
   
   La façon de configurer un gestionnaire de ressources de cluster dépend de la distribution de Linux spécifique. 

   >[!IMPORTANT]
   >Les environnements de production nécessitent un agent de délimitation, tels que STONITH pour la haute disponibilité. Démonstrations de cette documentation n’utilisent pas les agents de délimitation. Les démonstrations sont pour le test et validation uniquement. 
   
   >Un cluster Linux utilise délimitation pour retourner le cluster à un état connu. La façon de configurer la délimitation dépend de la distribution et l’environnement. À ce stade, la délimitation n’est pas disponible dans certains environnements de cloud. Consultez [des stratégies de prise en charge pour RHEL haute disponibilité des Clusters - plateformes de virtualisation](https://access.redhat.com/articles/29440) pour plus d’informations.

5.  [Ajouter le groupe de disponibilité en tant que ressource dans le cluster](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource). 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installer et configurer Pacemaker sur chaque nœud de cluster

1. Sur tous les nœuds, ouvrez les ports du pare-feu. Ouvrez le port pour le service à haute disponibilité Pacemaker, instance de SQL Server et le point de terminaison de groupe de disponibilité. Le port TCP par défaut pour le serveur exécutant SQL Server est 1433.  

   ```bash
   sudo ufw allow 2224/tcp
   sudo ufw allow 3121/tcp
   sudo ufw allow 21064/tcp
   sudo ufw allow 5405/udp
        
   sudo ufw allow 1433/tcp # Replace with TDS endpoint
   sudo ufw allow 5022/tcp # Replace with DATA_MIRRORING endpoint
        
   sudo ufw reload
   ```
   
   Vous pouvez également désactiver le pare-feu :
        
   ```bash
   sudo ufw disable
   ```

1. Installez les packages Pacemaker. Sur tous les nœuds, exécutez les commandes suivantes :

   ```bash
   sudo apt-get install pacemaker pcs fence-agents resource-agents
   ```

2. Définissez le mot de passe pour l’utilisateur par défaut qui est créé pendant l’installation des packages Pacemaker et Corosync. Utilisez le même mot de passe sur tous les nœuds. 

   ```bash
   sudo passwd hacluster
   ```

## <a name="enable-and-start-pcsd-service-and-pacemaker"></a>Activer et démarrer le service de pcsd et Pacemaker

La commande suivante active et démarre pacemaker et pcsd service. Exécuter tous les nœuds. Ainsi, les nœuds de rejoindre le cluster après le redémarrage. 

```bash
sudo systemctl enable pcsd
sudo systemctl start pcsd
sudo systemctl enable pacemaker
```
>[!NOTE]
>Commande d’activation du pacemaker peut se terminer avec l’erreur « pacemaker de démarrage par défaut ne contient aucun runlevels, abandon ». Il s’agit sans incidence, configuration de cluster puisse continuer. 

## <a name="create-the-cluster"></a>Créer le Cluster

1. Supprimer toute configuration de cluster existant à partir de tous les nœuds. 

   En cours d’exécution « sudo apt-get install PC » installe des PC, corosync et pacemaker en même temps et commence à s’exécuter toutes les 3 des services.  Démarrage de corosync génère un modèle de ' / etc/cluster/corosync.conf' fichier.  Pour que les étapes suivantes à réussir ce fichier ne doit pas exister – la solution de contournement consiste donc à arrêter pacemaker / corosync et supprimer ' / etc/cluster/corosync.conf', et ensuite les étapes suivantes terminer avec succès. « pcs cluster destroy » fait la même chose, et vous pouvez l’utiliser comme une étape d’installation initiale du cluster.
   
   La commande suivante supprime les fichiers de configuration de cluster existants et arrête tous les services de cluster. Cela détruit définitivement le cluster. Exécutez-le en tant que première étape dans un environnement de préproduction. Notez que « pcs cluster destroy » désactivé le service pacemaker et doit être réactivé. Exécutez la commande suivante sur tous les nœuds.
   
   >[!WARNING]
   >La commande détruit les ressources de cluster existant.

   ```bash
   sudo pcs cluster destroy 
   sudo systemctl enable pacemaker
   ```

1. Créer le cluster. 

   >[!WARNING]
   >En raison d’un problème connu que le fournisseur de clustering est examen, en commençant le cluster (« pcs cluster start') échoue avec l’erreur suivante. Il s’agit, car le fichier journal configuré dans /etc/corosync/corosync.conf qui est créé lorsque la commande d’installation de cluster est exécutée, est incorrect. Pour contourner ce problème, modifiez le fichier journal pour : /var/log/corosync/corosync.log. Sinon, vous pouvez créer le fichier /var/log/cluster/corosync.log.
 
   ```Error
   Job for corosync.service failed because the control process exited with error code. 
   See "systemctl status corosync.service" and "journalctl -xe" for details.
   ```
  
La commande suivante crée un cluster à trois nœuds. Avant d’exécuter le script, remplacez les valeurs entre `< ... >`. Exécutez la commande suivante sur le nœud principal. 

   ```bash
   sudo pcs cluster auth <node1> <node2> <node3> -u hacluster -p <password for hacluster>
   sudo pcs cluster setup --name <clusterName> <node1> <node2…> <node3>
   sudo pcs cluster start --all
   sudo pcs cluster enable --all
   ```
   
   >[!NOTE]
   >Si vous avez configuré un cluster sur les mêmes nœuds, vous devez utiliser l’option « --force » pendant l’exécution de « pcs cluster setup ». Notez que cela revient à exécuter « pcs cluster destroy » et que le service Pacemaker doit être réactivé à l’aide de « sudo systemctl enable pacemaker ».


## <a name="configure-fencing-stonith"></a>Configurer la délimitation (STONITH)

Fournisseurs de cluster pacemaker nécessitent STONITH doit être activé et un appareil de délimitation configuré pour une configuration de cluster pris en charge. Lorsque le Gestionnaire de ressources de cluster ne peut pas déterminer l’état d’un nœud ou d’une ressource sur un nœud, la délimitation est utilisée pour mettre le cluster à un état connu à nouveau. Délimitation de niveau ressource garantit principalement qu’il n’existe aucune altération des données en cas de panne en configurant une ressource. Vous pouvez utiliser la délimitation au niveau de la ressource, par exemple, avec DRBD (Distributed répliquées bloc appareil) pour marquer le disque sur un nœud comme obsolètes lorsque la liaison de communication tombe en panne. Délimitation de niveau de nœud garantit qu’un nœud ne s’exécute pas toutes les ressources. Cela est effectué en réinitialisant le nœud et l’implémentation de Pacemaker de celui-ci est appelée STONITH (ce qui signifie « dépanner l’autre nœud dans la tête »). Pacemaker prend en charge une grande variété d’appareils de délimitation, par exemple, une alimentation de secours ou la gestion cartes d’interface pour les serveurs. Pour plus d’informations, consultez [Clusters Pacemaker à partir de zéro](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html) et [délimitation et Stonith](http://clusterlabs.org/doc/crm_fencing.html) 

Étant donné que le niveau de nœud clôtures configuration dépend largement de votre environnement, nous la désactivons pour ce didacticiel (il peut être configuré ultérieurement). Exécutez le script suivant sur le nœud principal : 

```bash
sudo pcs property set stonith-enabled=false
```

>[!IMPORTANT]
>La désactivation de STONITH est uniquement pour des fins de test. Si vous envisagez d’utiliser Pacemaker dans un environnement de production, vous devez planifier une implémentation de STONITH en fonction de votre environnement et laissez cette option activée. Notez qu’à ce stade il n’existe aucun agent de délimitation pour les environnements de cloud (y compris Azure) ou l’Hyper-V. Par conséquent, le fournisseur de cluster n’offre pas de prise en charge pour les clusters de production en cours d’exécution dans ces environnements. 

## <a name="set-cluster-property-cluster-recheck-interval"></a>Définir la propriété cluster cluster-revérification-intervalle

`cluster-recheck-interval` Indique l’intervalle d’interrogation à laquelle le cluster vérifie les modifications dans les paramètres de ressource, de contraintes ou d’autres options de cluster. Si un réplica tombe en panne, le cluster tente de redémarrer le réplica à un intervalle qui est lié par le `failure-timeout` valeur et le `cluster-recheck-interval` valeur. Par exemple, si `failure-timeout` est définie sur 60 secondes et `cluster-recheck-interval` est définie sur 120 secondes, le redémarrage est tenté à un intervalle est supérieur à 60 secondes et inférieure à 120 secondes. Nous vous recommandons de définir d’expiration de l’échec à 60 s et revérifie-cluster-intervalle à une valeur qui est supérieure à 60 secondes. Définissant l’intervalle de revérification de cluster sur une valeur faible n’est pas recommandée.

Pour mettre à jour la valeur de propriété à `2 minutes` exécuter :

```bash
sudo pcs property set cluster-recheck-interval=2min
```

> [!IMPORTANT] 
> Si vous disposez déjà d’une ressource de groupe de disponibilité gérée par un cluster Pacemaker, notez que toutes les distributions qui utilisent le dernier package 1.1.18-11.el7 Pacemaker disponible introduisent un changement de comportement pour le cluster start-échec-est-irrécupérable paramètre lorsque son la valeur est false. Cette modification affecte le flux de travail de basculement. Si un réplica principal connaît une panne, le cluster est prévu pour basculer vers un des réplicas secondaires disponibles. Au lieu de cela, les utilisateurs constatent que le cluster continue d’essayer de démarrer le réplica principal a échoué. Si ce principal est jamais en ligne (en raison d’une panne permanente), le cluster bascule jamais vers un autre réplica secondaire disponible. Grâce à cette modification, une configuration précédemment recommandée pour définir le début-échec-est-irrécupérable n’est plus valide et que le paramètre doit être rétablie à sa valeur par défaut de `true`. En outre, la ressource de groupe de disponibilité doit être mis à jour pour inclure le `failover-timeout` propriété. 
>
>Pour mettre à jour la valeur de propriété à `true` exécuter :
>
>```bash
>sudo pcs property set start-failure-is-fatal=true
>```
>
>Mettre à jour de votre propriété de ressource de groupe de disponibilité existante `failure-timeout` à `60s` exécuter (remplacez `ag1` par le nom de votre ressource de groupe de disponibilité) :
>
>```bash
>pcs resource update ag1 meta failure-timeout=60s
>```

## <a name="install-sql-server-resource-agent-for-integration-with-pacemaker"></a>Installer l’agent de ressources de SQL Server pour l’intégration à Pacemaker

Exécutez les commandes suivantes sur tous les nœuds. 

```bash
sudo apt-get install mssql-server-ha
```

## <a name="create-a-sql-server-login-for-pacemaker"></a>Créer une connexion SQL Server pour Pacemaker

[!INCLUDE [SLES-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="create-availability-group-resource"></a>Créer une ressource de groupe de disponibilité

Pour créer la ressource de groupe de disponibilité, utilisez `pcs resource create` commande et définissez les propriétés de ressource. Commande ci-dessous crée un `ocf:mssql:ag` maître/esclave des ressources de type pour le groupe de disponibilité avec le nom `ag1`. 

```bash
sudo pcs resource create ag_cluster ocf:mssql:ag ag_name=ag1 meta failure-timeout=30s --master meta notify=true

```

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

## <a name="create-virtual-ip-resource"></a>Créer la ressource d’adresse IP virtuelle

Pour créer la ressource d’adresse IP virtuelle, exécutez la commande suivante sur un nœud. Utiliser une adresse IP statique disponible à partir du réseau. Avant d’exécuter le script, remplacez les valeurs comprises entre `< ... >` avec une adresse IP valide.

```bash
sudo pcs resource create virtualip ocf:heartbeat:IPaddr2 ip=<10.128.16.240>
```

Il n’existe aucun nom de serveur virtuel équivalent dans Pacemaker. Pour utiliser une chaîne de connexion qui pointe vers un nom de serveur de chaîne et n’utilisez pas l’adresse IP, inscrire l’adresse de la ressource d’adresse IP et le nom du serveur virtuel souhaité dans DNS. Pour les configurations de récupération d’urgence, inscrivez le nom du serveur virtuel souhaité et l’adresse IP avec les serveurs DNS principal et le site de récupération d’urgence.

## <a name="add-colocation-constraint"></a>Ajouter une contrainte de colocalisation

Presque chaque décision dans un cluster Pacemaker, comme choisir où une ressource doit s’exécuter, est effectuée en comparant les scores. Scores sont calculés par ressource, et le Gestionnaire de ressources de cluster choisit le nœud avec le score le plus élevé pour une ressource particulière. (Si un nœud a un score négatif pour une ressource, la ressource ne peut pas s’exécuter sur ce nœud.) Utilisez des contraintes pour configurer les décisions du cluster. Les contraintes ont un score. Si une contrainte a un score inférieur à l’infini, il est uniquement une recommandation. Un score d’infini signifie qu’il est obligatoire. Pour vous assurer que le réplica principal et la ressource d’adresse ip virtuelle sont sur le même hôte, définir une contrainte de colocalisation avec un score d’infini. Pour ajouter la contrainte de colocalisation, exécutez la commande suivante sur un nœud. 

```bash
sudo pcs constraint colocation add virtualip ag_cluster-master INFINITY with-rsc-role=Master
```

## <a name="add-ordering-constraint"></a>Ajouter une contrainte de classement

La contrainte de colocalisation a une contrainte de classement implicite. Il déplace la ressource d’adresse IP virtuelle avant de poursuivre la ressource de groupe de disponibilité. Par défaut, la séquence d’événements est :

1. Problèmes des utilisateurs `pcs resource move` au groupe de disponibilité principal de Nœud1 vers Nœud2.
1. La ressource d’adresse IP virtuelle s’arrête sur node1.
1. La ressource d’adresse IP virtuelle démarre sur node2.

   >[!NOTE]
   >À ce stade, l’adresse IP temporairement pointe vers node2 si node2 est toujours un basculement antérieur secondaire. 
   
1. Le groupe de disponibilité principal sur node1 est rétrogradé vers le site secondaire.
1. Le groupe de disponibilité secondaire sur node2 est promu vers le site principal. 

Pour empêcher l’adresse IP de temporairement pointant vers le nœud avec la base de données secondaire pre-basculement, ajoutez une contrainte de classement. 

Pour ajouter une contrainte de classement, exécutez la commande suivante sur un nœud :

```bash
sudo pcs constraint order promote ag_cluster-master then start virtualip
```

>[!IMPORTANT]
>Après avoir configuré le cluster et ajouter le groupe de disponibilité en tant que ressource de cluster, vous ne pouvez pas utiliser Transact-SQL pour basculer les ressources de groupe de disponibilité. Ressources de cluster de SQL Server sur Linux sont couplés pas aussi étroitement avec le système d’exploitation tels qu’ils sont sur un Cluster de basculement du serveur Windows (WSFC). Service SQL Server n’est pas informé de la présence du cluster. Tous les orchestration s’effectue via les outils de gestion de cluster. Dans RHEL ou Ubuntu utiliser `pcs`. 

<!---[!INCLUDE [Pacemaker Concepts](..\includes\ss-linux-cluster-pacemaker-concepts.md)]--->

## <a name="next-steps"></a>Étapes suivantes

[Utiliser le groupe de disponibilité de haute disponibilité](sql-server-linux-availability-group-failover-ha.md)

