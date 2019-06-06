---
title: Configurer un Cluster RHEL pour le groupe de disponibilité de SQL Server
titleSuffix: SQL Server
description: En savoir plus sur les clusters de groupe de disponibilité lors de l’exécution de Red Hat Enterprise Linux (RHEL)
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/12/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: b7102919-878b-4c08-a8c3-8500b7b42397
ms.openlocfilehash: 6c1c966c394f871a5772c6df5226d6a136dd12dc
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66713523"
---
# <a name="configure-rhel-cluster-for-sql-server-availability-group"></a>Configurer un Cluster RHEL pour le groupe de disponibilité de SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce document explique comment créer un cluster de groupe de disponibilité de trois nœuds pour SQL Server sur Red Hat Enterprise Linux. Pour la haute disponibilité, un groupe de disponibilité sur Linux nécessite trois nœuds, consultez [haute disponibilité et protection des données pour les configurations de groupe de disponibilité](sql-server-linux-availability-group-ha.md). La couche de clustering est basée sur Red Hat Enterprise Linux (RHEL) [module complémentaire HA](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf) , construit sur [Pacemaker](https://clusterlabs.org/). 

> [!NOTE] 
> Accès à la documentation complète de Red Hat requiert un abonnement valide. 

Pour plus d’informations sur la configuration du cluster, options d’agents de ressources et la gestion, visitez [documentation de référence RHEL](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html).

> [!NOTE] 
> SQL Server n’est pas aussi étroitement intégré à Pacemaker sur Linux car il s’agit avec le clustering de basculement Windows Server. Une instance de SQL Server n’est pas conscient du cluster. Pacemaker fournit l’orchestration de ressource de cluster. En outre, le nom de réseau virtuel est spécifique au clustering de basculement Windows Server, il n’existe aucun équivalent dans Pacemaker. Disponibilité groupe vues de gestion dynamique (DMV) qui interrogent des informations de cluster retournent les lignes vides sur des clusters Pacemaker. Pour créer un écouteur pour une reconnexion après un basculement transparent, vous devez inscrire manuellement le nom de l’écouteur dans DNS avec l’adresse IP utilisée pour créer la ressource d’adresse IP virtuelle. 

Les sections suivantes guident à travers les étapes pour configurer un cluster Pacemaker et ajouter un groupe de disponibilité en tant que ressource dans le cluster pour la haute disponibilité.

## <a name="roadmap"></a>Feuille de route

Les étapes pour créer un groupe de disponibilité sur des serveurs Linux pour la haute disponibilité sont différentes de la procédure sur un cluster de basculement Windows Server. La liste suivante décrit les étapes principales : 

1. [Configurer SQL Server sur les nœuds de cluster](sql-server-linux-setup.md).

2. [Créer le groupe de disponibilité](sql-server-linux-availability-group-configure-ha.md). 

3. Configurer un gestionnaire de ressources de cluster, tels que Pacemaker. Ces instructions sont fournies dans ce document.
   
   La façon de configurer un gestionnaire de ressources de cluster dépend de la distribution de Linux spécifique. 

   >[!IMPORTANT]
   >Les environnements de production nécessitent un agent de délimitation, tels que STONITH pour la haute disponibilité. Démonstrations de cette documentation n’utilisent pas les agents de délimitation. Les démonstrations sont pour le test et validation uniquement. 
   
   >Un cluster Linux utilise délimitation pour retourner le cluster à un état connu. La façon de configurer la délimitation dépend de la distribution et l’environnement. Actuellement, la délimitation n’est pas disponible dans certains environnements de cloud. Pour plus d’informations, consultez [des stratégies de prise en charge pour RHEL haute disponibilité des Clusters - plateformes de virtualisation](https://access.redhat.com/articles/29440).

5. [Ajouter le groupe de disponibilité en tant que ressource dans le cluster](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource).  

## <a name="configure-high-availability-for-rhel"></a>Configurer la haute disponibilité pour RHEL

Pour configurer la haute disponibilité pour RHEL, activer l’abonnement de haute disponibilité, puis configurez Pacemaker.

### <a name="enable-the-high-availability-subscription-for-rhel"></a>Activer l’abonnement de haute disponibilité pour RHEL

Chaque nœud du cluster doit avoir un abonnement approprié pour RHEL et l’ajout de la haute disponibilité. Passez en revue les exigences à [comment installer des packages de cluster haute disponibilité dans Red Hat Enterprise Linux](https://access.redhat.com/solutions/45930). Suivez ces étapes pour configurer l’abonnement et les référentiels :

1. Enregistrer le système.

   ```bash
   sudo subscription-manager register
   ```

   Fournissez votre nom d’utilisateur et le mot de passe.   

1. Liste des pools disponibles pour l’inscription.

   ```bash
   sudo subscription-manager list --available
   ```

   Dans la liste des pools disponibles, notez l’ID du pool pour l’abonnement de haute disponibilité.

1. Mettre à jour le script suivant. Remplacez `<pool id>` avec l’ID du pool pour la haute disponibilité de l’étape précédente. Exécutez le script pour attacher l’abonnement.

   ```bash
   sudo subscription-manager attach --pool=<pool id>
   ```

1. Activer le référentiel.

   ```bash
   sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
   ```

Pour plus d’informations, consultez [clusters Pacemaker - Open Source pour la haute disponibilité](https://clusterlabs.org/pacemaker/). 

Une fois que vous avez configuré l’abonnement, procédez comme suit pour configurer Pacemaker :

### <a name="configure-pacemaker"></a>Configurer Pacemaker

Après avoir inscrit l’abonnement, procédez comme suit pour configurer Pacemaker :
   
[!INCLUDE [RHEL-Configure-Pacemaker](../includes/ss-linux-cluster-pacemaker-configure-rhel.md)]

Une fois que Pacemaker est configurée, utilisez `pcs` pour interagir avec le cluster. Exécuter toutes les commandes sur un nœud du cluster. 

## <a name="configure-fencing-stonith"></a>Configurer la délimitation (STONITH)

Fournisseurs de cluster pacemaker nécessitent STONITH doit être activé et un appareil de délimitation configuré pour une configuration de cluster pris en charge. STONITH est l’acronyme « déménager à l’autre nœud dans la tête ». Lorsque le Gestionnaire de ressources de cluster ne peut pas déterminer l’état d’un nœud ou d’une ressource sur un nœud, délimitation apporte à nouveau le cluster à un état connu.

Délimitation de niveau ressource permet de s’assurer qu’il n’existe aucune altération des données en cas de panne en configurant une ressource. Par exemple, vous pouvez utiliser la délimitation de niveau de ressources pour marquer le disque sur un nœud comme obsolètes lorsque la liaison de communication tombe en panne. 

Délimitation de niveau de nœud garantit qu’un nœud ne s’exécute pas toutes les ressources. Pour cela, vous devez réinitialiser le nœud. Pacemaker prend en charge une grande variété d’appareils de clôture. Un onduleur approvisionnement ou gestion des cartes d’interface pour les serveurs sont des exemples.

Pour plus d’informations sur STONITH et délimitation, consultez les articles suivants :

* [Clusters pacemaker à partir de zéro](https://clusterlabs.org/pacemaker/doc/en-US/Pacemaker/1.1/html/Clusters_from_Scratch/index.html)
* [La délimitation et STONITH](https://clusterlabs.org/doc/crm_fencing.html)
* [Module complémentaire de Red Hat haute disponibilité avec Pacemaker : Délimitation](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/ch-fencing-HAAR.html)

Étant donné que le niveau de nœud clôtures configuration dépend largement de votre environnement, désactivez-la pour ce didacticiel (il peut être configuré ultérieurement). Le script suivant désactive la délimitation de niveau de nœud :

```bash
sudo pcs property set stonith-enabled=false
```
  
>[!IMPORTANT]
>La désactivation de STONITH est uniquement pour des fins de test. Si vous envisagez d’utiliser Pacemaker dans un environnement de production, vous devez planifier une implémentation de STONITH en fonction de votre environnement et laissez cette option activée. RHEL ne fournit pas d’agents de délimitation pour les environnements de cloud (y compris Azure) ou l’Hyper-V. Par conséquent, le fournisseur de cluster n’offre pas de prise en charge pour les clusters de production en cours d’exécution dans ces environnements. Nous travaillons sur une solution pour cet écart qui est disponible dans les versions futures.

## <a name="set-cluster-property-cluster-recheck-interval"></a>Définir la propriété cluster cluster-revérification-intervalle

`cluster-recheck-interval` Indique l’intervalle d’interrogation à laquelle le cluster vérifie les modifications dans les paramètres de ressource, de contraintes ou d’autres options de cluster. Si un réplica tombe en panne, le cluster tente de redémarrer le réplica à un intervalle qui est lié par le `failure-timeout` valeur et le `cluster-recheck-interval` valeur. Par exemple, si `failure-timeout` est définie sur 60 secondes et `cluster-recheck-interval` est définie sur 120 secondes, le redémarrage est tenté à un intervalle est supérieur à 60 secondes et inférieure à 120 secondes. Nous vous recommandons de définir d’expiration de l’échec à 60 s et revérifie-cluster-intervalle à une valeur qui est supérieure à 60 secondes. Définissant l’intervalle de revérification de cluster sur une valeur faible n’est pas recommandée.

Pour mettre à jour la valeur de propriété à `2 minutes` exécuter :

```bash
sudo pcs property set cluster-recheck-interval=2min
```

> [!IMPORTANT] 
> Toutes les distributions qui utilisent le dernier package 1.1.18-11.el7 Pacemaker disponibles (notamment RHEL 7.3 et 7.4) introduisent un changement de comportement pour le paramètre de démarrage-échec-est-irrécupérable cluster lorsque sa valeur est false. Cette modification affecte le flux de travail de basculement. Si un réplica principal connaît une panne, le cluster est prévu pour basculer vers un des réplicas secondaires disponibles. Au lieu de cela, les utilisateurs constatent que le cluster continue d’essayer de démarrer le réplica principal a échoué. Si ce principal est jamais en ligne (en raison d’une panne permanente), le cluster bascule jamais vers un autre réplica secondaire disponible. Grâce à cette modification, une configuration précédemment recommandée pour définir le début-échec-est-irrécupérable n’est plus valide et que le paramètre doit être rétablie à sa valeur par défaut de `true`. En outre, la ressource de groupe de disponibilité doit être mis à jour pour inclure le `failover-timeout` propriété. 

Pour mettre à jour la valeur de propriété à `true` exécuter :

```bash
sudo pcs property set start-failure-is-fatal=true
```

Pour mettre à jour le `ag_cluster` propriété de ressource `failure-timeout` à `60s` exécuter :

```bash
pcs resource update ag_cluster meta failure-timeout=60s
```


Pour plus d’informations sur les propriétés du cluster Pacemaker, consultez [propriétés des Clusters Pacemaker](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-clusteropts-HAAR.html).

## <a name="create-a-sql-server-login-for-pacemaker"></a>Créer une connexion SQL Server pour Pacemaker

[!INCLUDE [SQL-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="create-availability-group-resource"></a>Créer une ressource de groupe de disponibilité

Pour créer la ressource de groupe de disponibilité, utilisez `pcs resource create` commande et définissez les propriétés de ressource. La commande suivante crée un `ocf:mssql:ag` maître/esclave des ressources de type pour le groupe de disponibilité avec le nom `ag1`.

```bash
sudo pcs resource create ag_cluster ocf:mssql:ag ag_name=ag1 meta failure-timeout=60s master notify=true
``` 

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

<a name="createIP"></a>

## <a name="create-virtual-ip-resource"></a>Créer la ressource d’adresse IP virtuelle

Pour créer la ressource d’adresse IP virtuelle, exécutez la commande suivante sur un nœud. Utiliser une adresse IP statique disponible à partir du réseau. Remplacez l’adresse IP entre `<10.128.16.240>` avec une adresse IP valide.

```bash
sudo pcs resource create virtualip ocf:heartbeat:IPaddr2 ip=<10.128.16.240>
```

Il n’existe aucun nom de serveur virtuel équivalent dans Pacemaker. Pour utiliser une chaîne de connexion qui pointe vers un nom de serveur de chaîne au lieu d’une adresse IP, inscrire l’adresse de la ressource IP virtuelle et le nom du serveur virtuel souhaité dans DNS. Pour les configurations de récupération d’urgence, inscrivez le nom du serveur virtuel souhaité et l’adresse IP avec les serveurs DNS principal et le site de récupération d’urgence.

## <a name="add-colocation-constraint"></a>Ajouter une contrainte de colocalisation

Presque chaque décision dans un cluster Pacemaker, comme choisir où une ressource doit s’exécuter, est effectuée en comparant les scores. Scores sont calculés par ressource. Le Gestionnaire de ressources de cluster choisit le nœud avec le score le plus élevé pour une ressource particulière. Si un nœud a un score négatif pour une ressource, la ressource ne peut pas s’exécuter sur ce nœud.

Sur un cluster pacemaker, vous pouvez manipuler les décisions du cluster avec des contraintes. Les contraintes ont un score. Si une contrainte a un score inférieur à `INFINITY`, Pacemaker considère qu’en tant que recommandation. Un score de `INFINITY` est obligatoire.

Pour vous assurer que le réplica principal et les ressources d’adresse ip virtuelle exécutent sur le même hôte, définir une contrainte de colocalisation avec un score d’infini. Pour ajouter la contrainte de colocalisation, exécutez la commande suivante sur un nœud.

```bash
sudo pcs constraint colocation add virtualip ag_cluster-master INFINITY with-rsc-role=Master
```

## <a name="add-ordering-constraint"></a>Ajouter une contrainte de classement

La contrainte de colocalisation a une contrainte de classement implicite. Il déplace la ressource d’adresse IP virtuelle avant de poursuivre la ressource de groupe de disponibilité. Par défaut, la séquence d’événements est :

1. Problèmes des utilisateurs `pcs resource move` au groupe de disponibilité principal de Nœud1 vers Nœud2.
1. La ressource d’adresse IP virtuelle s’arrête sur le nœud 1.
1. La ressource d’adresse IP virtuelle démarre sur le nœud 2.
  
   >[!NOTE]
   >À ce stade, l’adresse IP temporairement pointe vers le nœud 2 pendant que le nœud 2 est toujours un basculement antérieur secondaire. 
   
1. Le groupe de disponibilité principal sur le nœud 1 est rétrogradé vers le site secondaire.
1. Le groupe de disponibilité secondaire sur le nœud 2 est promu vers le site principal. 

Pour empêcher l’adresse IP de temporairement pointant vers le nœud avec la base de données secondaire pre-basculement, ajoutez une contrainte de classement. 

Pour ajouter une contrainte de classement, exécutez la commande suivante sur un nœud :

```bash
sudo pcs constraint order promote ag_cluster-master then start virtualip
```

>[!IMPORTANT]
>Après avoir configuré le cluster et ajouter le groupe de disponibilité en tant que ressource de cluster, vous ne pouvez pas utiliser Transact-SQL pour basculer les ressources de groupe de disponibilité. Ressources de cluster de SQL Server sur Linux sont couplés pas aussi étroitement avec le système d’exploitation tels qu’ils sont sur un Cluster de basculement du serveur Windows (WSFC). Service SQL Server n’est pas informé de la présence du cluster. Tous les orchestration s’effectue via les outils de gestion de cluster. Dans RHEL ou Ubuntu utiliser `pcs` et en cours d’utilisation SLES `crm` outils. 

Basculer manuellement le groupe de disponibilité avec `pcs`. Ne démarrez pas le basculement avec Transact-SQL. Pour obtenir des instructions, consultez [basculement](sql-server-linux-availability-group-failover-ha.md#failover).

## <a name="next-steps"></a>Étapes suivantes

[Utiliser le groupe de disponibilité de haute disponibilité](sql-server-linux-availability-group-failover-ha.md)
