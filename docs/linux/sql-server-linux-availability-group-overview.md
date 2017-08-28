---
title: "Groupe de disponibilité Always On pour SQL Server sur Linux | Documents Microsoft"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 06/14/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: e37742d4-541c-4d43-9ec7-a5f9b2c0e5d1
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c5c7e602ac1beedb028072b4c82578e9948af43d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="availability-groups-for-sql-server-on-linux"></a>Groupes de disponibilité pour SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Un groupe de disponibilité SQL Server Always On est une haute disponibilité (HA), récupération d’urgence (DR) et la solution de montée en puissance parallèle. Il fournit à haute disponibilité pour les groupes de bases de données sur le stockage en attachement direct. Il prend en charge plusieurs serveurs secondaires pour la haute disponibilité intégrée et récupération d’urgence, la détection automatique de panne, le basculement transparent rapide et l’équilibrage de charge de lecture. Ce large éventail de fonctionnalités permet de vous permet d’atteindre une disponibilité optimale SLA pour vos charges de travail.

Groupes de disponibilité de SQL Server ont été introduits dans SQL Server 2012 et ont été améliorés avec chaque version. Cette fonctionnalité est désormais disponible sur Linux. Pour prendre en compte les charges de travail SQL Server aux besoins rigoureux de continuité des activités, les groupes de disponibilité exécuter sur tous les prises en charge [distributions du système d’exploitation Linux](sql-server-linux-release-notes.md). En outre, toutes les fonctionnalités qui rendent les groupes de disponibilité une solution de récupération d’urgence haute disponibilité flexible, intégrée et efficace sont également disponibles sur Linux. notamment : 

- **Basculement de plusieurs bases de données** un groupe de disponibilité prend en charge un environnement de basculement pour un ensemble de bases de données utilisateur, appelées bases de données de disponibilité.
- **Un rapide de détection de défaillance et basculement** en tant que ressource dans un cluster à haute disponibilité, un groupe de disponibilité tire parti de l’intelligence de cluster intégrés pour la détection de basculement immédiat et l’action de basculement.
- **Basculement transparent à l’aide de la ressource IP virtuelle** client permet d’utiliser la chaîne de connexion unique au principal en cas de basculement. Nécessite une intégration avec un gestionnaire de cluster.
- **Plusieurs secondaires synchrones et asynchrones** un groupe de disponibilité prend en charge jusqu'à huit réplicas secondaires. Avec la réplication synchrone, le réplica principal attend pour valider la transaction, que le réplica principal attend de transactions être écrites sur disque sur le journal des transactions. Le réplica principal n’attend pas d’écritures sur les réplicas synchrones asynchrones.  
- **Basculement manuel ou automatique** basculement vers un réplica secondaire synchrone peut être déclenché automatiquement par le cluster ou à la demande par l’administrateur de base de données.
- **Secondaires actifs disponibles pour les charges de travail en lecture et de sauvegarde** un ou plusieurs réplicas secondaires peuvent être configurés pour prendre en charge un accès en lecture seule aux bases de données secondaire et/ou à autoriser les sauvegardes de bases de données secondaires.
- **L’amorçage automatique** SQL Server crée automatiquement les réplicas secondaires pour chaque base de données dans le groupe de disponibilité.
- **Routage en lecture seule** SQL Server achemine les connexions entrantes à un écouteur de groupe de disponibilité vers un réplica secondaire est configuré pour autoriser des charges de travail en lecture seule. 
- **Déclencheur de surveillance et de basculement de l’intégrité au niveau de base de données** surveillance au niveau de base de données et des diagnostics améliorés. 
- **Configurations de récupération d’urgence** avec les groupes de disponibilité distribués ou le programme d’installation du groupe de disponibilité de sous-réseaux multiples. 
- **Les fonctionnalités de lecture à l’échelle** dans SQL Server 2017 vous pouvez créer un groupe de disponibilité avec ou sans la haute disponibilité pour les opérations en lecture seule de montée en puissance parallèle. 


Pour plus d’informations sur les groupes de disponibilité de SQL Server, consultez [groupes de disponibilité SQL Server Always On](http://msdn.microsoft.com/library/hh510230.aspx).

## <a name="availability-group-terminology"></a>Terminologie de groupe de disponibilité

Un groupe de disponibilité prend en charge un environnement de basculement pour un ensemble discret de bases de données utilisateur - connu en tant que bases de données de disponibilité - qui basculent ensemble. Un groupe de disponibilité prend en charge un ensemble de bases de données primaires en lecture-écriture et un à huit ensembles de bases de données secondaires correspondantes. Éventuellement, les bases de données secondaires peuvent être rendues disponibles pour l'accès en lecture seule et/ou certaines opérations de sauvegarde. Un groupe de disponibilité définit un ensemble de deux ou plusieurs partenaires de basculement, appelés réplicas de disponibilité. Réplicas de disponibilité sont des composants du groupe de disponibilité. Pour plus d’informations, consultez [vue d’ensemble de toujours sur les groupes de disponibilité (SQL Server)](http://msdn.microsoft.com/library/ff877884.aspx).

Les termes suivants décrivent les principales parties d’une solution de groupe de disponibilité de SQL Server :

 Groupe de disponibilité  
 Conteneur d’un ensemble de bases de données ( *bases de données de disponibilité*) qui basculent ensemble.  
  
 Base de données de disponibilité  
 Base de données qui appartient à un groupe de disponibilité. Pour chaque base de données de disponibilité, le groupe de disponibilité conserve une seule copie en lecture-écriture (la *base de données primaire*) et une à huit copies en lecture seule (les*bases de données secondaires*).  
  
 base de données primaire  
 Copie en lecture-écriture d'une base de données de disponibilité.  
  
 base de données secondaire  
 Copie en lecture seule d'une base de données de disponibilité.  
  
 réplica de disponibilité  
 Instanciation d’un groupe de disponibilité hébergé par une instance spécifique de SQL Server et qui conserve une copie locale de chaque base de données de disponibilité qui appartient au groupe de disponibilité. Il existe deux types de réplicas de disponibilité : un seul *réplica principal* et un à huit *réplicas secondaires*.  
  
 réplica principal  
 Réplica de disponibilité qui rend les bases de données primaires disponibles pour les connexions en lecture-écriture à partir des clients et envoie également des enregistrements du journal des transactions pour chaque base de données primaire à chaque réplica secondaire.  
  
 réplica secondaire  
 Réplica de disponibilité qui conserve une copie secondaire de chaque base de données de disponibilité, et sert de cible potentielle d'un basculement du groupe de disponibilité. Éventuellement, un réplica secondaire peut prendre en charge l'accès en lecture seule et la création de sauvegardes sur des bases de données secondaires.  
  
 écouteur de groupe de disponibilité  
 Nom du serveur auquel les clients peuvent se connecter afin d’accéder à une base de données dans le réplica principal ou secondaire d’un groupe de disponibilité. Les écouteurs de groupe de disponibilité dirigent les connexions entrantes vers un réplica principal ou un réplica secondaire en lecture seule.  


## <a name="new-in-sql-server-2017-for-availability-groups"></a>Nouveautés de SQL Server 2017 pour les groupes de disponibilité

SQL Server 2017 introduit de nouvelles fonctionnalités pour les groupes de disponibilité.

**CLUSTER_TYPE** utiliser avec `CREATE AVAILABILITY GROUP`. Identifie le type de gestionnaire du cluster de serveur qui gère un groupe de disponibilité. Peut être un des types suivants :

   - **WSFC** cluster de basculement de serveur Winows. Sous Windows, il est la valeur par défaut pour CLUSTER_TYPE.
   - **EXTERNE** un gestionnaire de cluster qui n’est pas Windows server cluster de basculement - par exemple, sur Linux avec STIMULATEUR.
   - **AUCUN** aucun gestionnaire de cluster. Utilisé pour un groupe de disponibilité de la lecture à l’échelle.

Pour plus d’informations sur ces options, consultez [créer un groupe de disponibilité](http://msdn.microsoft.com/library/ff878399.aspx) ou [ALTER AVAILABILITY GROUP](http://msdn.microsoft.com/library/ff878601.aspx).

**Garantie est validée sur les réplicas secondaires synchrones.**

Use `required_synchronized_secondaries_to_commit`with `CREATE AVAILABILITY GROUP` or `ALTER AVAILABILITY GROUP`. Lorsque `required_synchronized_secondaries_to_commit` est défini sur une valeur supérieure à 0, les transactions sur le réplica principal attend jusqu'à ce que la transaction est validée sur le nombre spécifié de bases de données **secondaire synchrone** journaux de transaction de base de données réplica. Si suffisamment réplicas secondaires synchrones ne sont pas en ligne, toutes les connexions au réplica principal sont rejetées jusqu'à ce que les communications avec des réplicas secondaires suffisamment reprendre.

**Groupes de disponibilité de la lecture à l’échelle**

Créer un groupe de disponibilité sans un cluster pour prendre en charge les charges de travail en lecture à l’échelle. Consultez [groupes de disponibilité à l’échelle en lecture](../database-engine/availability-groups/windows/read-scale-availability-groups.md).

## <a name="next-steps"></a>Étapes suivantes

[Configurer le groupe de disponibilité pour SQL Server sur Linux](sql-server-linux-availability-group-configure-ha.md)

[Configurer le groupe de disponibilité de la lecture à l’échelle pour SQL Server sur Linux](sql-server-linux-availability-group-configure-rs.md)

[Ajouter le groupe de disponibilité des ressources de Cluster sur RHEL](sql-server-linux-availability-group-cluster-rhel.md)

[Ajouter le groupe de disponibilité des ressources de Cluster sur SLES](sql-server-linux-availability-group-cluster-sles.md)

[Ajouter le groupe de disponibilité des ressources de Cluster sur Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

