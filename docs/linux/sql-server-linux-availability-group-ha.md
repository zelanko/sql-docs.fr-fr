---
title: "SQL Server Always On le modèles de déploiement du groupe de disponibilité | Documents Microsoft"
ms.custom: 
ms.date: 06/16/2017
ms.prod: sql-linux
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
caps.latest.revision: 34
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8e2d26fd9ce79fc8c47c7499313648d565ae1b97
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---

# <a name="high-availability-and-data-protection-for-availability-group-configurations"></a>Haute disponibilité et protection des données pour les configurations de groupe de disponibilité

Cet article présente les configurations de déploiement pris en charge pour les groupes de disponibilité SQL Server Always On sur des serveurs Linux. Un groupe de disponibilité prend en charge la haute disponibilité et protection des données. Détection de défaillance automatique, le basculement automatique et la reconnexion après un basculement transparente fournissent une haute disponibilité. Réplicas synchronisés fournissent la protection des données. 

>[!NOTE]
>En plus de la haute disponibilité et la protection des données, un groupe de disponibilité peut également assurer la récupération d’urgence, plateforme migration entre et lire la montée en puissance parallèle. Cet article traite principalement des implémentations pour la haute disponibilité et protection des données. 

Avec Windows Server clustering de basculement, une configuration commune pour une haute disponibilité utilise deux réplicas synchrones et un [témoin de partage de fichiers](http://technet.microsoft.com/library/cc731739.aspx). Le témoin de partage de fichiers valide la configuration de groupe de disponibilité - état de synchronisation et le rôle du réplica, par exemple. Cette configuration garantit que le réplica secondaire est choisi comme la cible de basculement possède les données les plus récentes et les modifications de configuration de groupe de disponibilité. 

Les solutions de haute disponibilité en cours pour Linux ne contiennent pas d’un témoin externe tels que le témoin de partage de fichiers dans un cluster de basculement Windows Server. Lorsqu’il n’existe aucun cluster de basculement Windows Server, la configuration de groupe de disponibilité est stockée dans la base de données master sur les instances participantes de SQL Server. Par conséquent, le groupe de disponibilité requiert au moins trois réplicas synchrones pour une haute disponibilité et protection des données. Après avoir créé un groupe de disponibilité sur des serveurs Linux, créer une ressource de cluster. Les paramètres de ressource de cluster déterminent la configuration pour la haute disponibilité.

Choisissez une conception de groupe de disponibilité pour répondre aux besoins spécifiques pour la haute disponibilité, protection des données et lire la montée en puissance parallèle.

>[!IMPORTANT]
>Les configurations suivantes décrivent les modèles de conception de groupe de disponibilité et les fonctionnalités de chaque modèle. Ces modèles de conception s’appliquent aux groupes de disponibilité avec `CLUSTER_TYPE = EXTERNAL` pour les solutions de haute disponibilité. 

Les modèles de conception sont deux configurations de groupe de disponibilité. Les configurations sont les suivantes :

- **Trois réplicas synchrones**

- **Deux réplicas synchrones**

## <a name="how-the-configuration-affects-default-resource-settings"></a>Impact de la configuration des paramètres de ressource par défaut

Le paramètre de ressource de cluster `required_synchronized_secondaries_to_commit` garantit que chaque transaction est écrite dans un nombre minimal de journaux du réplica secondaire avant de valider la transaction sur le réplica principal. Ce paramètre peut affecter la haute disponibilité et protection des données, selon la configuration. Lorsque vous installez l’agent de la ressource SQL Server - `mssql-server-ha` - et créer une ressource de cluster pour le groupe de disponibilité, le Gestionnaire du cluster détecte la disponibilité du groupe configuration et jeux de `required_synchronized_secondaries_to_commit` en conséquence. 

Si la prise en charge par la configuration, le paramètre d’agent ressource `required_synchronized_secondaries_to_commit` est définie sur la valeur qui fournit une haute disponibilité et protection des données. Pour plus d’informations, consultez [agent de ressource comprendre SQL Server pour STIMULATEUR](#pacemakerNotify).

Les sections suivantes expliquent le comportement par défaut pour la ressource de cluster. 

<a name="threeSynch"></a>

## <a name="three-synchronous-replicas"></a>Trois réplicas synchrones

Cette configuration se compose de trois réplicas synchrones. Par défaut, il fournit une haute disponibilité et protection des données. Elle peut également fournir la montée en puissance parallèle en lecture.

![Trois réplicas][3]

Le tableau suivant décrit le comportement de protection des données et de disponibilité élevé, selon les paramètres d’un groupe de disponibilité avec trois réplicas synchrones : 

|`required_synchronized_secondaries_to_commit`|0 |1 \*|2
| --- |:---:|:---:|:---:
|Basculement automatique après une panne du réplica principal| |✔| 
|Réplica principal disponible après une panne de réplica secondaire|✔|✔| 
|Réplica principal disponible après deux pannes de réplica secondaire|✔| |
|Basculement manuel après panne du réplica principal - possible perte de données|✔| | 

\*Paramètre lorsque le groupe de disponibilité est ajouté en tant que ressource dans un cluster par défaut.

<a name="twoSynch"></a>

## <a name="two-synchronous-replicas"></a>Deux réplicas synchrones

Cette configuration permet la protection des données. Comme les autres configurations de groupe de disponibilité, il peut autoriser la lecture montée en puissance parallèle. La configuration de deux réplicas synchrones ne fournit pas automatique haute disponibilité. 

![Deux réplicas synchrones][1]

Cette configuration nécessite deux serveurs. Ces serveurs remplir le rôle de réplica principal et le réplica secondaire. 

La configuration de deux réplicas synchrones est optimisée pour les données de protection et de distribuer la charge de travail en lecture pour les bases de données. Par défaut, la ressource est configurée pour la protection des données. Cette configuration ne fournit pas de haute disponibilité, car si des instances de SQL Server échoue, la base de données n’est pas complètement disponible ou risque de perte de données. 

Le tableau suivant décrit le comportement de protection des données en fonction des valeurs possibles pour un groupe de disponibilité avec deux réplicas synchrones : 

|`required_synchronized_secondaries_to_commit`|0 \*|1 
| --- |:---|:---
|Basculement automatique après une panne du réplica principal| |✔ \*\* | 
|Réplica principal disponible après une panne de réplica secondaire|✔| |

\*Paramètre lorsque le groupe de disponibilité est ajouté en tant que ressource dans un cluster par défaut.

\*\*Dans cette configuration, la panne de réplica principal après le groupe de disponibilité automatique bascule. Les applications ne peut pas se connecter au groupe de disponibilité jusqu'à ce que le réplica principal est en ligne - maintenant comme un réplica secondaire. 

La configuration de deux réplicas synchrones peut être plus économique car elle requiert uniquement deux instances de SQL Server sur deux serveurs.

<a name="pacemakerNotify"></a>

## <a name="understand-sql-server-resource-agent-for-pacemaker"></a>Comprendre l’agent de ressources de SQL Server pour STIMULATEUR

SQL Server 2017 CTP 1.4 ajouté `sequence_number` à `sys.availability_groups` pour autoriser STIMULATEUR identifier la base de données secondaire des réplicas sont avec le réplica principal. `sequence_number`est une valeur BIGINT monolithique qui représente la mise à jour le réplica de groupe de disponibilité local. Mises à jour STIMULATEUR le `sequence_number` avec chaque modification de configuration de groupe de disponibilité. Les exemples de modifications de configuration de basculement, ajout de réplica ou la suppression. Le nombre est mis à jour sur le serveur principal, puis répliqué vers les réplicas secondaires. Par conséquent, un réplica secondaire qui a une configuration à jour a le même numéro de séquence en tant que le serveur principal. 

Lorsque STIMULATEUR décide de promouvoir un réplica principal, il envoie d’abord un *préalable promouvoir* notification à tous les réplicas. Les réplicas de retournent le numéro de séquence. Ensuite, quand il tente réellement STIMULATEUR promouvoir un réplica principal, le réplica lui-même promeut uniquement si son numéro de séquence est le plus élevé de tous les numéros de séquence. Si son propre numéro de séquence ne correspond pas le numéro de séquence le plus élevé, le réplica rejette l’opération de promotion. De cette façon, seul le réplica ayant le numéro de séquence le plus élevé peut être promu principal, ce qui évite toute perte de données. 

Ce processus requiert au moins un réplica disponible pour la promotion avec le même numéro de séquence en tant que le réplica principal précédent. Les jeux de l’agent de ressource STIMULATEUR `required_synchronized_secondaries_to_commit` telles qu’au moins un réplica secondaire synchrone est à jour et disponible pour être la cible d’un basculement automatique par défaut. Avec chaque action d’analyse, la valeur de `required_synchronized_secondaries_to_commit` est calculée (et mises à jour si nécessaire). Le `required_synchronized_secondaries_to_commit` la valeur est « nombre de réplicas synchrones » de divisé par 2. Au moment du basculement, l’agent de ressource requiert (`total number of replicas`  -  `required_synchronized_secondaries_to_commit` réplicas) pour répondre à la promouvoir la notification préalable. Le réplica avec la plus grande `sequence_number` est devenu le principal. 

Par exemple, un groupe de disponibilité avec trois réplicas synchrones - un réplica principal et deux réplicas secondaires synchrones.

- `required_synchronized_secondaries_to_commit`est 1 ; (3 / 2 -> 1).

- Le nombre de réplicas pour répondre aux préalable promouvoir action requis est 2 ; (3 - 1 = 2). 

Dans ce scénario, les deux réplicas ont répondu pour le basculement doit être déclenchée. Pour le basculement automatique réussi après une panne de réplica principal, les deux réplicas secondaires doivent être mis à jour et de répondre à la promouvoir la notification préalable. S’ils sont en ligne et synchrone, ils ont le même numéro de séquence. Le groupe de disponibilité promeut un d’eux. Si seul un des réplicas secondaires répond à l’avant de promouvoir l’action, l’agent de ressource ne peut pas garantir que la base de données secondaire qui a répondu possède les numéros de séquence le plus élevé et un basculement n’est pas déclenché.

>[!IMPORTANT]
>Lorsque `required_synchronized_secondaries_to_commit` est 0 est risque de perte de données. Durant une panne de réplica principal, l’agent de ressource ne déclenche pas automatiquement un basculement. Vous pouvez attendre primary afin de restaurer ou basculer manuellement à l’aide de `FORCE_FAILOVER_ALLOW_DATA_LOSS`.

Vous pouvez choisir de remplacer le comportement par défaut et empêcher la ressource de groupe de disponibilité de paramètre `required_synchronized_secondaries_to_commit` automatiquement.

Le script suivant définit `required_synchronized_secondaries_to_commit` 0 sur un groupe de disponibilité nommé `<**ag1**>`. Avant d’exécuter remplacer `<**ag1**>` par le nom de votre groupe de disponibilité.

```bash
sudo pcs resource update <**ag1**> required_synchronized_secondaries_to_commit=0
```

Pour rétablir la valeur par défaut, en fonction de la configuration du groupe de disponibilité s’exécuter :

```bash
sudo pcs resource update <**ag1**> required_synchronized_secondaries_to_commit=
```

>[!NOTE]
>Lorsque vous exécutez les commandes précédentes, le serveur principal est rétrogradé temporairement la sur le site secondaire, puis promu à nouveau. La mise à jour de ressource entraîne tous les réplicas arrêter et redémarrer. La nouvelle valeur de`required_synchronized_secondaries_to_commit` est définie uniquement une fois que les réplicas sont redémarrés, pas instantanément.

<!--Image references-->
[1]: ./media/sql-server-linux-availability-group-ha/1-read-scale-out.png
[3]: ./media/sql-server-linux-availability-group-ha/3-three-replica.png
