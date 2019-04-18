---
title: SQL Server Always On le modèles de déploiement du groupe de disponibilité | Microsoft Docs
ms.custom: sql-linux
ms.date: 04/17/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: linux
ms.topic: conceptual
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b0b7e735b2897f8bc942f1d4e6c151f27f588e8c
ms.sourcegitcommit: e2d65828faed6f4dfe625749a3b759af9caa7d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59671175"
---
# <a name="high-availability-and-data-protection-for-availability-group-configurations"></a>Haute disponibilité et protection des données pour les configurations de groupe de disponibilité

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article présente les configurations de déploiement pris en charge pour les groupes de disponibilité SQL Server Always On sur des serveurs Linux. Un groupe de disponibilité prend en charge la haute disponibilité et protection des données. Détection de défaillance automatique, le basculement automatique et une reconnexion après un basculement transparente fournissent une haute disponibilité. Réplicas synchronisés offrent la protection des données. 

Sur un Windows Server Cluster (basculement), une configuration courante pour la haute disponibilité utilise les deux réplicas synchrones et un troisième serveur ou partage de fichiers pour fournir un quorum. Le témoin de partage de fichiers valide la configuration de groupe de disponibilité - état de synchronisation et le rôle du réplica, par exemple. Cette configuration garantit que le réplica secondaire est choisi comme la cible de basculement possède les données les plus récentes et les modifications de configuration de groupe de disponibilité. 

Le cluster WSFC synchronise les métadonnées de configuration pour l’arbitrage de basculement entre les réplicas de groupe de disponibilité et le témoin de partage de fichiers. Quand un groupe de disponibilité n’est pas sur un cluster WSFC, les instances de SQL Server stockent les métadonnées de configuration dans la base de données master.

Par exemple, un groupe de disponibilité sur un cluster Linux a `CLUSTER_TYPE = EXTERNAL`. Il n’existe aucun WSFC arbitrer le basculement. Dans ce cas, les métadonnées de configuration sont gérée et gérée par les instances de SQL Server. Étant donné qu’aucun serveur témoin dans ce cluster, une troisième instance de SQL Server est nécessaire pour stocker les métadonnées d’état de configuration. Les trois instances de SQL Server constituent le stockage des métadonnées distribuée pour le cluster. 

Le Gestionnaire du cluster peut interroger les instances de SQL Server dans le groupe de disponibilité et orchestrer le basculement pour assurer une haute disponibilité. Dans un cluster Linux, Pacemaker est le Gestionnaire du cluster. 

SQL Server 2017 CU 1 active la haute disponibilité pour un groupe de disponibilité avec `CLUSTER_TYPE = EXTERNAL` pour deux réplicas synchrones ainsi qu’un réplica en configuration seule. Le réplica en configuration seule peut être hébergé sur n’importe quelle édition de SQL Server 2017 CU1 ou version ultérieure - y compris SQL Server Express edition. Le réplica en configuration seule conserve les informations de configuration sur le groupe de disponibilité dans la base de données master, mais ne contient-elle pas les bases de données utilisateur dans le groupe de disponibilité. 

## <a name="how-the-configuration-affects-default-resource-settings"></a>Les effets des paramètres de ressources par défaut

SQL Server 2017 introduit la `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` paramètre de ressource de cluster. Ce paramètre garantit le nombre spécifié de l’écriture des réplicas secondaires les données de transaction pour vous connecter avant que le réplica principal valide chaque transaction. Lorsque vous utilisez un gestionnaire de cluster externe, ce paramètre affecte la haute disponibilité et protection des données. La valeur par défaut pour le paramètre varie selon l’architecture au moment de que la création de la ressource de cluster. Lorsque vous installez l’agent de ressource SQL Server - `mssql-server-ha` - et créer une ressource de cluster pour le groupe de disponibilité, le Gestionnaire de cluster détecte la disponibilité de groupe configuration et jeux `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` en conséquence. 

Si la prise en charge par la configuration, le paramètre d’agent de ressource `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` est définie sur la valeur qui fournit une haute disponibilité et protection des données. Pour plus d’informations, consultez [agent de ressource comprendre SQL Server pour pacemaker](#pacemakerNotify).

Les sections suivantes expliquent le comportement par défaut pour la ressource de cluster. 

Choisir une conception de groupe de disponibilité pour répondre aux besoins professionnels spécifiques pour une haute disponibilité et protection des données avec échelle lecture.

Les configurations suivantes décrivent les modèles de conception de groupe de disponibilité et les fonctionnalités de chaque modèle. Ces modèles de conception s’appliquent aux groupes de disponibilité avec `CLUSTER_TYPE = EXTERNAL` pour les solutions de haute disponibilité. 

- **Trois réplicas synchrones**
- **Deux réplicas synchrones**
- **Deux réplicas synchrones et un réplica en configuration seule**

<a name="threeSynch"></a>

## <a name="three-synchronous-replicas"></a>Trois réplicas synchrones

Cette configuration se compose de trois réplicas synchrones. Par défaut, il fournit une haute disponibilité et protection des données. Il peut également fournir à l’échelle en lecture.

![Trois réplicas][3]

Un groupe de disponibilité avec trois réplicas synchrones peut fournir en lecture à l’échelle, haute disponibilité et protection des données. Le tableau suivant décrit le comportement de disponibilité. 

| |échelle de lecture|Haute disponibilité & </br> protection de données | Protection des données|
|:---|---|---|---|
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 |1<sup>\*</sup>|2|
|Indisponibilité du réplica principal |Basculement automatique. Nouveau réplica principal est R / w. |Basculement automatique. Nouveau réplica principal est R / w. |Basculement automatique. Nouveau réplica principal n’est pas disponible pour les transactions utilisateur jusqu'à ce que le réplica principal précédent récupère et joint le groupe de disponibilité comme secondaire. |
|Une indisponibilité du réplica secondaire  | Principal est R / w. Aucun basculement automatique si le serveur principal échoue. |Principal est R / w. Aucun basculement automatique si le serveur principal échoue également. | Principal n’est pas disponible pour les transactions utilisateur. |

<sup>\*</sup> Par défaut

<a name="twoSynch"></a>

## <a name="two-synchronous-replicas"></a>Deux réplicas synchrones

Cette configuration permet la protection des données. Comme les autres configurations de groupe de disponibilité, il peut activer avec échelle lecture. La configuration de deux réplicas synchrones ne fournit pas de haute disponibilité automatique. Configurer deux réplicas est uniquement applicable à SQL Server 2017 RTM et est plus pris en charge avec une version ultérieure (CU1 et au-delà) les versions de SQL Server 2017...

![Deux réplicas synchrones][1]

Un groupe de disponibilité avec deux réplicas synchrones fournit une protection à l’échelle en lecture et de données. Le tableau suivant décrit le comportement de disponibilité. 

| |échelle de lecture |Protection des données|
|:---|---|---|
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 <sup>\*</sup>|1|
|Indisponibilité du réplica principal | Basculement manuel. Perte de données possible. Nouveau réplica principal est R / w.| Basculement automatique. Nouveau réplica principal n’est pas disponible pour les transactions utilisateur jusqu'à ce que le réplica principal précédent récupère et joint le groupe de disponibilité comme secondaire.|
|Une indisponibilité du réplica secondaire  |Principal est en lecture/écriture, exécution exposée à une perte de données. |Principal n’est pas disponible pour les transactions utilisateur jusqu'à ce que la récupération du réplica secondaire.|

<sup>\*</sup> Par défaut

<a name = "configOnly"></a>

## <a name="two-synchronous-replicas-and-a-configuration-only-replica"></a>Deux réplicas synchrones et un réplica en configuration seule

Un groupe de disponibilité avec réplicas synchrones deux (ou plus) et un réplica en configuration seule offre une protection des données et peut également fournir une haute disponibilité. Le diagramme suivant représente cette architecture :

![Groupe de disponibilité configuration seule][2]

1. Réplication synchrone des données utilisateur vers le réplica secondaire. Il inclut également des métadonnées de configuration de groupe de disponibilité.
2. Réplication synchrone des métadonnées de configuration de groupe de disponibilité. Il n’inclut pas les données utilisateur.

Dans le diagramme de groupe de disponibilité, un réplica principal envoie les données de configuration pour le réplica secondaire et le réplica en configuration seule. Le réplica secondaire reçoit également des données de l’utilisateur. Le réplica en configuration seule ne reçoit pas de données utilisateur. Le réplica secondaire est en mode de disponibilité synchrones. Le réplica en configuration seule ne contient pas les bases de données du groupe de disponibilité - seules les métadonnées sur le groupe de disponibilité. Données de configuration sur le réplica en configuration seule sont validées synchrone.

> [!NOTE]
> Un groupe availabilility avec réplica en configuration seule est une nouveauté pour SQL Server 2017 CU1. Toutes les instances de SQL Server dans le groupe de disponibilité doivent être SQL Server 2017 CU1 ou version ultérieure. 

La valeur par défaut `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` est 0. Le tableau suivant décrit le comportement de disponibilité. 

| |Haute disponibilité & </br> protection de données | Protection des données|
|:---|---|---|
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 <sup>\*</sup>|1|
|Indisponibilité du réplica principal | Basculement automatique. Nouveau réplica principal est R / w. | Basculement automatique. Nouveau réplica principal n’est pas disponible pour les transactions utilisateur. |
|Indisponibilité du réplica secondaire | Réplica principal est lecture/écriture, exécution exposée à une perte de données (si principal échoue et ne peuvent pas être récupérée). Aucun basculement automatique si le serveur principal échoue également. | Principal n’est pas disponible pour les transactions utilisateur. Aucun réplica vers lequel basculer principale n’échoue également. |
|Panne de réplica configuration uniquement | Principal est R / w. Aucun basculement automatique si le serveur principal échoue également. | Principal est R / w. Aucun basculement automatique si le serveur principal échoue également. |
|Base de données secondaire synchrone + configuration uniquement indisponibilité du réplica| Principal n’est pas disponible pour les transactions utilisateur. Aucun basculement automatique. | Principal n’est pas disponible pour les transactions utilisateur. Aucun réplica vers lequel basculer if principal échoue également. |

<sup>\*</sup> Par défaut

> [!NOTE]
> L’instance de SQL Server qui héberge le réplica en configuration seule peut également héberger d’autres bases de données. Il peut également participer en tant qu’une configuration seule base de données pour plus d’un groupe de disponibilité. 

## <a name="requirements"></a>Configuration requise

- Tous les réplicas dans un groupe de disponibilité avec un réplica en configuration seule doivent être SQL Server 2017 CU 1 ou version ultérieure.
- N’importe quelle édition de SQL Server peut héberger un réplica en configuration seule, y compris SQL Server Express. 
- Le groupe de disponibilité doit au moins un réplica secondaire - en plus le réplica principal.
- Réplicas uniquement de configuration ne comptent pas dans le nombre maximal de réplicas pour chaque instance de SQL Server. SQL Server standard edition autorise jusqu'à trois réplicas, SQL Server Enterprise Edition permet jusqu'à 9.

## <a name="considerations"></a>Observations

- Pas plus d’un réplica en configuration seule par groupe de disponibilité. 
- Un réplica en configuration seule ne peut pas être un réplica principal.
- Vous ne pouvez pas modifier le mode de disponibilité d’un réplica en configuration seule. Pour modifier à partir d’un réplica en configuration seule vers un réplica secondaire synchrone ou asynchrone, supprimez le réplica en configuration seule et ajouter un réplica secondaire avec le mode de disponibilité requis. 
- Un réplica en configuration seule est synchrone avec les métadonnées de groupe de disponibilité. Aucune donnée utilisateur. 
- Un groupe de disponibilité avec un réplica principal et réplica en une configuration seule, mais aucun réplica secondaire n’est pas valide. 
- Vous ne pouvez pas créer un groupe de disponibilité sur une instance de SQL Server Express edition. 

<a name="pacemakerNotify"></a>

## <a name="understand-sql-server-resource-agent-for-pacemaker"></a>Comprendre l’agent de ressources de SQL Server pour pacemaker

SQL Server 2017 CTP 1.4 a ajouté `sequence_number` à `sys.availability_groups` pour permettre à Pacemaker identifier la base de données secondaire à jour les réplicas sont avec le réplica principal. `sequence_number` est une valeur BIGINT monotone qui représente à jour le réplica de groupe de disponibilité local. Mises à jour de pacemaker le `sequence_number` à chaque modification de configuration de groupe de disponibilité. Les exemples de modifications de configuration de basculement, ajout de réplica ou la suppression. Le nombre est mis à jour sur le serveur principal, puis répliqué vers les réplicas secondaires. Par conséquent, un réplica secondaire qui a une configuration à jour a le même numéro de séquence en tant que le réplica principal. 

Quand Pacemaker décide de promouvoir un réplica en principal, il envoie d’abord un *prépromotion* notification à tous les réplicas. Le retour des réplicas le numéro de séquence. Ensuite, quand Pacemaker tente effectivement de promouvoir un réplica en principal, le réplica n’assure sa promotion si son numéro de séquence est supérieur à tous les numéros de séquence. Si son propre numéro de séquence ne correspond pas le numéro de séquence le plus élevé, le réplica rejette l’opération de promotion. De cette façon, seul le réplica ayant le numéro de séquence le plus élevé peut être promu principal, ce qui évite toute perte de données. 

Ce processus requiert au moins un réplica disponible pour la promotion avec le même numéro de séquence que le principal précédent. Les jeux de l’agent de ressource Pacemaker `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` telles qu’au moins un réplica secondaire synchrone est à jour et disponible pour être la cible d’un basculement automatique par défaut. Avec chaque action d’analyse, la valeur de `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` est calculée (et mis à jour si nécessaire). Le `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` valeur est « nombre de réplicas synchrones » divisé par 2. Au moment du basculement, l’agent de ressource requiert (`total number of replicas`  -  `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` réplicas) pour répondre à la notification de prépromotion. Le réplica le plus élevé `sequence_number` est devenu le principal. 

Par exemple, un groupe de disponibilité avec trois réplicas synchrones : un réplica principal et deux réplicas secondaires synchrones.

- `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` est 1 ; (3 / 2 -> 1).

- Le nombre requis de réplicas pour répondre à l’action de prépromotion est 2 ; (3 - 1 = 2). 

Dans ce scénario, deux réplicas doivent répondre pour le basculement soit déclenché. Pour le basculement automatique réussi après une panne de réplica principal, les deux réplicas secondaires doivent être à jour et de répondre à la notification de prépromotion. S’ils sont en ligne et synchrone, ils ont le même numéro de séquence. Le groupe de disponibilité promeut un d’eux. Si seul un des réplicas secondaires répond à l’action de prépromotion l’agent de ressource ne peut pas garantir que la base de données secondaire qui a répondu a le sequence_number le plus élevé et un basculement n’est pas déclenché.

> [!IMPORTANT]
> Quand la valeur de `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` est 0, il existe un risque de perte de données. Pendant une panne de réplica principal, l’agent de ressource ne déclenche pas automatiquement un basculement. Vous pouvez attendre principal à récupérer, ou basculer manuellement à l’aide de `FORCE_FAILOVER_ALLOW_DATA_LOSS`.

Vous pouvez choisir de remplacer le comportement par défaut et empêcher la ressource de groupe de disponibilité de paramètre `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` automatiquement.

Le script suivant définit `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` 0 sur un groupe de disponibilité nommé `<**ag1**>`. Avant de l’exécuter, remplacez `<**ag1**>` par le nom de votre groupe de disponibilité.

```bash
sudo pcs resource update <**ag1**> required_synchronized_secondaries_to_commit=0
```

Pour rétablir la valeur par défaut, selon la configuration du groupe de disponibilité exécuter :

```bash
sudo pcs resource update <**ag1**> required_synchronized_secondaries_to_commit=
```

> [!NOTE]
> Lorsque vous exécutez les commandes précédentes, le réplica principal est temporairement rétrogradé vers le site secondaire, puis promu à nouveau. La mise à jour de ressource entraîne tous les réplicas arrêter et redémarrer. La nouvelle valeur pour`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` est définie uniquement une fois que les réplicas sont redémarrés, pas instantanément.

## <a name="see-also"></a>Voir aussi

[Groupes de disponibilité sur Linux](sql-server-linux-availability-group-overview.md)

<!--Image references-->
[1]: ./media/sql-server-linux-availability-group-ha/1-read-scale-out.png
[2]: ./media/sql-server-linux-availability-group-ha/2-configuration-only.png
[3]: ./media/sql-server-linux-availability-group-ha/3-three-replica.png
[4]: ./media/sql-server-linux-availability-group-ha/configuration-only-example.png
