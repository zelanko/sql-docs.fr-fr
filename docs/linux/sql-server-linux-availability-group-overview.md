---
title: Toujours sur les groupes de disponibilité pour SQL Server sur Linux | Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 04/17/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: e37742d4-541c-4d43-9ec7-a5f9b2c0e5d1
ms.openlocfilehash: cec05fbb83bf3b86babfa26df619ebc8f9a2a34d
ms.sourcegitcommit: e2d65828faed6f4dfe625749a3b759af9caa7d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59671285"
---
# <a name="always-on-availability-groups-on-linux"></a>Sur Linux, les groupes de disponibilité Always On

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article décrit les caractéristiques des groupes de disponibilité AlwaysOn (groupes de disponibilité) sous Linux sur [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] installations. Il couvre également les différences entre Linux et de cluster de basculement Windows Server (WSFC)-en fonction des groupes de disponibilité. Consultez le [documentation basée sur Windows](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) pour les principes fondamentaux de groupes de disponibilité, comme ils fonctionnent de la même sur Windows et Linux à l’exception du cluster WSFC.

À partir d’un point de vue de haut niveau, les groupes de disponibilité sous [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Linux sont les mêmes qu’ils se trouvent sur des implémentations basées sur le cluster WSFC. Cela signifie que toutes les limitations et les fonctionnalités sont identiques, à quelques exceptions près. Les principales différences sont les suivantes :

-   Microsoft Distributed Transaction Coordinator (DTC) n’est pas pris en charge sous Linux dans [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Si vos applications nécessitent l’utilisation des transactions distribuées et avez besoin d’un groupe de disponibilité, déployez [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sur Windows.
-   Déploiements basés sur Linux utilisent Pacemaker au lieu d’un cluster WSFC.
-   Contrairement à la plupart des configurations pour les groupes de disponibilité sur Windows à l’exception du scénario de Cluster du groupe de travail, Pacemaker nécessite jamais des Services de domaine Active Directory (AD DS).
-   Comment restaurer un groupe de disponibilité d’un nœud à un autre est différente entre Linux et Windows.
-   Certains paramètres tels que `required_synchronized_secondaries_to_commit` ne peut être modifiée par le biais de Pacemaker sur Linux, tandis qu’une installation basée sur un WSFC utilise Transact-SQL.

## <a name="number-of-replicas-and-cluster-nodes"></a>Nombre de réplicas et les nœuds de cluster

Un groupe de disponibilité [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)] peut avoir deux réplicas au total : un serveur principal et un secondaire qui peut être utilisé uniquement à des fins de disponibilité. Il ne peut pas être utilisé à d’autres fins, telles que les requêtes accessible en lecture. Un groupe de disponibilité [!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)] peut avoir jusqu'à neuf réplicas au total : un principal et jusqu'à huit bases de données secondaires, dont jusqu'à trois (y compris la principale) peut être synchrone. Si vous utilisez un cluster sous-jacent, il peut y avoir un maximum de 16 nœuds total lorsque Corosync est impliqué. Un groupe de disponibilité peut s’étendre sur au maximum neuf des 16 nœuds avec [!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]et deux avec [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)].

Une configuration de deux réplicas qui nécessite la possibilité de basculer automatiquement vers un autre réplica nécessite l’utilisation d’un réplica en configuration seule, comme décrit dans [réplica en Configuration seule et quorum](#configuration-only-replica-and-quorum). Configuration seule réplicas ont été introduits dans [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] à jour Cumulative 1 (CU1), qui devrait donc être la version minimale déployée pour cette configuration.

Si Pacemaker est utilisé, il doit être correctement configuré et reste donc en cours d’exécution. Cela signifie que quorum et STONITH doivent être convenablement implémenté Pacemaker du point de vue, en plus [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] exigences telle qu’un réplica en configuration seule.

Réplicas secondaires lisibles sont uniquement pris en charge avec [!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)].

## <a name="cluster-type-and-failover-mode"></a>Mode de type et le basculement de cluster

Débutez [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] est l’introduction d’un type de cluster pour les groupes de disponibilité. Pour Linux, il existe deux valeurs valides : External et None. Un type de cluster externe signifie que Pacemaker sera être utilisé sous le groupe de disponibilité. À l’aide externe pour le type de cluster exige que le mode de basculement externe ainsi (également nouveau dans [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]). Le basculement automatique est pris en charge, mais contrairement à un cluster WSFC, le mode de basculement a la valeur externe, pas automatique, quand Pacemaker est utilisé. Contrairement à un cluster WSFC, la partie de Pacemaker du groupe de disponibilité est créée après que le groupe de disponibilité est configuré.

Un type de cluster aucun signifie qu’il n’est pas nécessaire pour, ni le groupe de disponibilité utilisera, Pacemaker. Même sur les serveurs dotés de Pacemaker configuré, si un groupe de disponibilité est configuré avec un type de cluster aucun, Pacemaker ne voient pas ou gérer ce groupe de disponibilité. Un type de cluster aucun prend uniquement en charge le basculement manuel d’un serveur principal vers un réplica secondaire. Un groupe de disponibilité créé avec None est principalement pour la lecture évolutif scénario ainsi que les mises à niveau. Il peut fonctionner dans des scénarios tels que la récupération d’urgence ou de disponibilité local où aucun basculement automatique n’est nécessaire, il n’est pas recommandé. L’histoire de l’écouteur est également plus complexe sans Pacemaker.

Type de cluster est stocké dans le [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] vue de gestion dynamique (DMV) `sys.availability_groups`, dans les colonnes `cluster_type` et `cluster_type_desc`.

## <a name="requiredsynchronizedsecondariestocommit"></a>required\_synchronized\_secondaries\_to\_commit

Débutez [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] est un paramètre qui est utilisé par les groupes de disponibilité appelés `required_synchronized_secondaries_to_commit`. Le groupe de disponibilité vous indique le nombre de réplicas secondaires qui doivent être par échelons avec le réplica principal. Cela permet le basculement automatique (uniquement en cas d’intégré à Pacemaker avec un type de cluster externe) et contrôle le comportement des éléments tels que la disponibilité du site principal si le nombre approprié de réplicas secondaires est en ligne ou hors connexion. Pour en savoir plus sur cette procédure, consultez [haute disponibilité et protection des données pour les configurations de groupe de disponibilité](sql-server-linux-availability-group-ha.md). Le `required_synchronized_secondaries_to_commit` valeur est définie par défaut et gérée par Pacemaker / [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Vous pouvez substituer manuellement cette valeur.

La combinaison de `required_synchronized_secondaries_to_commit` et le nouveau numéro de séquence (qui est stocké dans `sys.availability_groups`) informe Pacemaker et [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] que, par exemple, le basculement automatique peut se produire. Dans ce cas, un réplica secondaire aurait le même numéro de séquence en tant que le réplica principal, ce qui signifie qu’il est à jour avec les dernières informations de configuration.

Il existe trois valeurs qui peuvent être définies pour `required_synchronized_secondaries_to_commit`: 0, 1 ou 2. Ils contrôlent le comportement de ce qui se passe lorsqu’un réplica devient indisponible. Les numéros correspondent au nombre de réplicas secondaires qui doivent être synchronisés avec le réplica principal. Le comportement est comme suit sous Linux :

-   0 - réplicas secondaires n’avez pas besoin être dans un état synchronisé avec le réplica principal. Toutefois si les bases de données secondaires ne sont pas synchronisés, il n’y aura aucun basculement automatique. 
-   1 - un réplica secondaire doit être dans un état synchronisé avec le réplica principal ; le basculement automatique est possible. La base de données primaire n’est pas disponible jusqu'à ce qu’un réplica synchrone secondaire n’est disponible.
-   2 - les deux réplicas secondaires dans une configuration de groupe de disponibilité au moins trois nœuds doivent être synchronisés avec le serveur principal ; le basculement automatique est possible.

`required_synchronized_secondaries_to_commit` contrôle non seulement le comportement de basculement avec des réplicas synchrones, mais une perte de données. Avec la valeur 1 ou 2, un réplica secondaire est toujours requis pour être synchronisé, il y aura toujours la redondance des données. Cela signifie qu’aucune perte de données.

Pour modifier la valeur de `required_synchronized_secondaries_to_commit`, utilisez la syntaxe suivante :

>[!NOTE]
>Modification de la valeur provoque à la ressource à redémarrer, ce qui signifie qu’une brève interruption. La seule façon d’éviter ce problème consiste à définir la ressource à non gérés par le cluster temporairement.

**Red Hat Enterprise Linux (RHEL) et Ubuntu**

```bash
sudo pcs resource update <AGResourceName> required_synchronized_secondaries_to_commit=<Value>
```

**SUSE Linux Enterprise Server (SLES)**

```bash
sudo crm resource param ms-<AGResourceName> set required_synchronized_secondaries_to_commit <value>
```

où *AGResourceName* est le nom de la ressource configurée pour le groupe de disponibilité, et *valeur* est 0, 1 ou 2. Pour la définir à la valeur par défaut de Pacemaker la gestion du paramètre, exécutez la même instruction sans valeur.

Le basculement automatique d’un groupe de disponibilité est possible lorsque les conditions suivantes sont remplies :

-   Le réplica principal et le réplica secondaire sont définies sur le déplacement des données synchrone.
-   La base de données secondaire a un état synchronisé (se synchronisent ne pas), ce qui signifie que les deux sont au même point de données.
-   Le type de cluster est défini sur externe. Le basculement automatique n’est pas possible avec un type de cluster aucun.
-   Le `sequence_number` du réplica secondaire devienne le réplica principal a le numéro de séquence le plus élevé - en d’autres termes, le réplica secondaire `sequence_number` correspond à celui du réplica principal d’origine.

Si ces conditions sont remplies et que le serveur qui héberge le réplica principal échoue, le groupe de disponibilité changent de propriété vers un réplica synchrone. Le comportement des réplicas synchrones (de laquelle il peut y avoir trois total : un réplica principal et deux réplicas secondaires) peuvent également être gérées par `required_synchronized_secondaries_to_commit`. Cela fonctionne avec les groupes de disponibilité sur Windows et Linux, mais il est configuré complètement différemment. Sur Linux, la valeur est configurée automatiquement par le cluster sur la ressource de groupe de disponibilité elle-même.

## <a name="configuration-only-replica-and-quorum"></a>Quorum et le réplica en configuration seule

Autres nouveautés de [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] depuis CU1 est un réplica en configuration seule. Étant donné que Pacemaker est différente de celle d’un cluster WSFC, en particulier lorsqu’il s’agit de quorum et nécessiter de STONITH, avoir seulement une configuration à deux nœuds ne fonctionne pas lorsqu’il s’agit d’un groupe de disponibilité. Pour une FCI, les mécanismes de quorum fournis par Pacemaker peuvent être parfaits, car tous les arbitrage de basculement FCI se produit au niveau de la couche de cluster. Pour un groupe de disponibilité, arbitrage sous Linux se produit dans [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], où toutes les métadonnées sont stockées. Il s’agit là le réplica de configuration entre en jeu.

Sans quoi, un troisième nœud et au moins un réplica synchronisé serait requis. Le réplica en configuration seule stocke la configuration du groupe de disponibilité dans la base de données master, identique à celui des autres réplicas dans la configuration du groupe de disponibilité. Le réplica en configuration seule n’a pas de bases de données utilisateur participant dans le groupe de disponibilité. Les données de configuration sont envoyées de manière synchrone depuis le serveur principal. Ces données de configuration sont ensuite utilisées pendant les basculements, qu’ils soient automatique ou manuelle.

Pour un groupe de disponibilité maintenir le quorum et activer les basculements automatiques avec un type de cluster externe, celle-ci soit doit :

-   Avoir trois réplicas synchrones ([!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)] uniquement) ; ou
-   Avoir deux réplicas (principales et secondaire) ainsi que d’un réplica en configuration seule.

Basculements manuels peuvent se produire que vous utilisiez External ou None types pour les configurations de groupe de disponibilité de cluster. Pendant un réplica en configuration seule peut être configuré avec un groupe de disponibilité qui a un type de cluster aucun, il est déconseillé, car cela complique le déploiement. Pour ces configurations, modifiez manuellement `required_synchronized_secondaries_to_commit` pour avoir une valeur d’au moins 1, pour qu’il y a au moins un réplica synchronisé.

Un réplica en configuration seule peut être hébergé sur n’importe quelle édition de [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], y compris [!INCLUDE[ssexpress-md](../includes/ssexpress-md.md)]. Cela réduira les coûts de licence et permet de s’assurer qu’il fonctionne avec les groupes de disponibilité dans [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]. Cela signifie que le troisième requis server doit simplement présenter les caractéristiques minimales pour [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], car il ne reçoit pas de trafic de transaction utilisateur pour le groupe de disponibilité.

Lorsqu’un réplica en configuration seule est utilisé, il a le comportement suivant :

-   Par défaut, `required_synchronized_secondaries_to_commit` est définie sur 0. Cela peut être modifié manuellement sur 1 si vous le souhaitez.
-   Si le serveur principal échoue et `required_synchronized_secondaries_to_commit` est 0, le réplica secondaire sera devenir le nouveau réplica principal et être disponible pour la lecture et écriture. Si la valeur est 1, le basculement automatique se produit, mais n’accepte pas de nouvelles transactions jusqu'à ce que l’autre réplica est en ligne.
-   Si un réplica secondaire échoue et `required_synchronized_secondaries_to_commit` est 0, le réplica principal continue d’accepter les transactions, mais si le réplica principal échoue à ce stade, il n’existe aucune protection pour les données ni le basculement possible (manuel ou automatique), dans la mesure où un réplica secondaire n’est pas disponible.
-   Si les réplicas en configuration seule échoue, le groupe de disponibilité fonctionnera normalement, mais aucun basculement automatique n’est possible.
-   Si un réplica secondaire synchrone et le réplica en configuration seule échouent, le serveur principal ne peut pas accepter les transactions, et ne peut avoir pour basculer le réplica principal.

Dans CU1 il existe un bogue connu dans la journalisation dans le fichier corosync.log qui est généré par le biais de `mssql-server-ha`. Si un réplica secondaire n’est pas en mesure de devenir le réplica principal en raison du nombre de réplicas requises disponibles, le message en cours indique que « prévus pour recevoir les numéros de séquence 1 mais reçus uniquement 2. N’est pas suffisant de réplicas sont en ligne en toute sécurité promouvoir le réplica local. » Les numéros de doivent être annulées, et il doit indiquer « attendu recevoir les numéros de séquence 2 mais uniquement reçus 1. N’est pas suffisant de réplicas sont en ligne en toute sécurité promouvoir le réplica local. » 

## <a name="multiple-availability-groups"></a>Plusieurs groupes de disponibilité 

Plus d’un groupe de disponibilité peut être créée par cluster Pacemaker ou un ensemble de serveurs. La seule limite concerne des ressources système. La propriété du groupe de disponibilité est indiquée par le maître. Groupes de disponibilité différents peuvent être détenus par différents nœuds ; Il faut pas tous être en cours d’exécution sur le même nœud.

## <a name="drive-and-folder-location-for-databases"></a>Emplacement de lecteur et le dossier pour les bases de données

Comme sur les groupes de disponibilité basé sur Windows, la structure de dossiers et de lecteur pour les bases de données utilisateur participant à un groupe de disponibilité doit être identique. Par exemple, si les bases de données utilisateur sont dans `/var/opt/mssql/userdata` sur le serveur A, ce même dossier doit exister sur le serveur B. La seule exception à cela est indiquée dans la section [l’interopérabilité avec les réplicas et les groupes de disponibilité Windows](#interoperability-with-windows-based-availability-groups-and-replicas).

## <a name="the-listener-under-linux"></a>L’écouteur sous Linux

L’écouteur est une fonctionnalité facultative pour un groupe de disponibilité. Il fournit un point d’entrée unique pour toutes les connexions (lecture/écriture pour le réplica principal et/ou les réplicas en lecture seule vers le site secondaire) afin que les applications et les utilisateurs finaux n’avez pas besoin de connaître le serveur qui héberge les données. Dans un cluster WSFC, c’est la combinaison d’une ressource de nom réseau et une ressource d’adresse IP, qui est ensuite enregistrée dans AD DS (si nécessaire), ainsi que de DNS. En association avec la ressource de groupe de disponibilité proprement dit, il fournit cette abstraction. Pour plus d’informations sur un écouteur, consultez [écouteurs, connectivité Client et basculement d’Application](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md).

L’écouteur sous Linux est configuré différemment, mais ses fonctionnalités sont les mêmes. Il n’existe aucun concept d’une ressource de nom de réseau dans Pacemaker, ni est un objet créé dans AD DS ; Il est simplement une ressource d’adresse IP créée dans Pacemaker pouvant s’exécuter sur les nœuds. Une entrée associée à la ressource d’adresse IP pour l’écouteur dans le système DNS avec un « nom convivial » doit être créé. La ressource IP de l’écouteur sera active sur le serveur qui héberge le réplica principal pour ce groupe de disponibilité.

Si Pacemaker est utilisé et une ressource d’adresse IP est créée qui est associé à l’écouteur, il y aura une brève interruption comme l’adresse IP s’arrête sur le serveur et démarre sur l’autre, qu’il s’agisse de basculement automatique ou manuel. Si cette fonction abstraction grâce à la combinaison de l’adresse IP et un nom unique, il ne masque pas la panne. Une application doit être en mesure de gérer la déconnexion en demandant une sorte de fonctionnalité pour détecter et vous reconnecter.

Toutefois, la combinaison du nom DNS et adresse IP est toujours pas suffisamment pour fournir les fonctionnalités fournies par un écouteur sur un cluster WSFC, tels que le routage en lecture seule pour les réplicas secondaires. Lorsque vous configurez un groupe de disponibilité, un « écouteur » doit être configuré dans [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Ceci peut être observé dans l’Assistant, ainsi que la syntaxe Transact-SQL. Il existe deux façons que cela peut être configuré pour fonctionner de la même manière que sur Windows :

-   Pour un groupe de disponibilité avec un type de cluster externe, l’adresse IP associée à « l’écouteur » créé dans [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] doit être l’adresse IP de la ressource créée dans Pacemaker.
-   Pour un groupe de disponibilité créé avec un type de cluster aucun, utilisez l’adresse IP associée avec le réplica principal.

L’instance associée à l’adresse IP fournie puis devienne le coordinateur pour des éléments tels que les demandes de routage en lecture seule à partir d’applications.

## <a name="interoperability-with-windows-based-availability-groups-and-replicas"></a>Interopérabilité avec les réplicas et les groupes de disponibilité Windows 

Un groupe de disponibilité qui a un type de cluster d’externe ou qui est WSFC ne peut pas avoir ses réplicas multi-plateforme. Cela est vrai si le groupe de disponibilité est [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)] ou [!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]. Cela signifie que dans une configuration de groupe de disponibilité traditionnelle avec un cluster sous-jacent, un réplica ne peut pas être sur un cluster WSFC et l’autre sur Linux avec Pacemaker.

Un groupe de disponibilité avec un type de cluster aucun peut avoir ses réplicas à franchir les limites du système d’exploitation, il peut donc être les deux réplicas basés sur Linux et Windows dans le même groupe de disponibilité. Voici un exemple ici où le réplica principal est Windows, alors que la base de données secondaire est sur l’une des distributions Linux.

![Hybride None](./media/sql-server-linux-availability-group-overview/image1.png)

Un groupe de disponibilité distribué peut également traverser les limites du système d’exploitation. Les groupes de disponibilité sous-jacents sont liés par les règles pour la façon dont ils sont configurés, tel que celui configuré étant externe Linux uniquement, mais le groupe de disponibilité auquel il est joint peut être configuré à l’aide d’un cluster WSFC. Prenons l'exemple suivant :

![Groupe de disponibilité Dist hybride](./media/sql-server-linux-availability-group-overview/image2.png)

<!-- Distributed AGs are also supported for upgrades from [!INCLUDE[sssql15-md](../includes/sssql15-md.md)] to [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. For more information on how to achieve this, see [the article "x"].

If using automatic seeding with a distributed availability group that crosses OSes, it can handle the differences in folder structure. How this works is described in [the documentation for automatic seeding].
-->
 
## <a name="next-steps"></a>Étapes suivantes
[Configurer le groupe de disponibilité pour SQL Server sur Linux](sql-server-linux-availability-group-configure-ha.md)

[Configurer le groupe de disponibilité avec échelle lecture pour SQL Server sur Linux](sql-server-linux-availability-group-configure-rs.md)

[Ajouter le groupe de disponibilité des ressources de Cluster sur RHEL](sql-server-linux-availability-group-cluster-rhel.md)

[Ajouter le groupe de disponibilité des ressources de Cluster sur SLES](sql-server-linux-availability-group-cluster-sles.md)

[Ajouter le groupe de disponibilité des ressources de Cluster sur Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

[Configurer un groupe de disponibilité d’inter-plateformes](sql-server-linux-availability-group-cross-platform.md)

