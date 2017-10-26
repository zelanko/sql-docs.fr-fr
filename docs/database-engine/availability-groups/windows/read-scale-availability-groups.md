---
title: "Groupes de disponibilité avec échelle lecture | Microsoft Docs"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6dfa046a07b9fd5a3eddbe474b5ea63c1163c26c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="read-scale-availability-groups"></a>Groupes de disponibilité avec échelle lecture
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

En plus de rassembler les meilleures fonctionnalités de haute disponibilité pour SQL Server, un groupe de disponibilité offre des solutions de mise à l’échelle intégrées complètes. Dans une application de base de données standard, plusieurs clients exécutent différents types de charges de travail qui peuvent parfois entraîner des goulots d’étranglement en raison de contraintes de ressources. Vous pouvez libérer des ressources et obtenir un débit plus élevé pour la charge de travail OLTP ou fournir des performances et une échelle plus élevées sur les charges de travail en lecture seule. Pour cela, vous pouvez exploiter la technologie de réplication la plus rapide pour SQL Server : créez un groupe de bases de données répliquées pour décharger les charges de travail de création de rapports et analytiques sur les réplicas en lecture seule. 

Avec les groupes de disponibilité, un réplica secondaire ou plus peuvent être configurés pour prendre en charge un accès en lecture seule aux bases de données secondaires.

Les applications clientes qui exécutent les charges de travail analytiques ou de création de rapports peuvent se connecter directement aux bases de données secondaires. Ou le client peut configurer une liste de routage en lecture seule et se connecter au réplica principal qui transfère la demande de connexion à chacun des réplicas secondaires à partir de la liste de routage comme un tourniquet (round robin).

## <a name="read-scale-availability-groups-without-cluster"></a>Groupes de disponibilité avec échelle lecture sans cluster

Dans [!INCLUDE[sssql15-md](..\..\..\includes\sssql15-md.md)] et les versions antérieures, tous les groupes de disponibilité avaient besoin d’un cluster. Ce cluster assurait la continuité des activités : haute disponibilité et récupération d’urgence (HADR). De plus, les réplicas secondaires pouvaient être configurés pour des opérations de lecture. La configuration et le fonctionnement d’un cluster impliquaient une grande surcharge opérationnelle, si la haute disponibilité n’était pas l’objectif. SQL Server 2017 introduit les groupes de disponibilité avec échelle lecture sans aucun cluster. 

Si le besoin de l’entreprise est de préserver les ressources pour les charges de travail critiques en cours d’exécution sur le réplica principal, les utilisateurs peuvent désormais utiliser le routage en lecture seule ou se connecter directement à des réplicas secondaires lisibles, sans dépendre de l’intégration à une technologie de clustering. Ces nouvelles fonctionnalités sont disponibles pour SQL Server 2017 exécuté sur les plateformes Windows et Linux.

>[!IMPORTANT]
>Il ne s’agit pas d’une configuration de haute disponibilité. Il n’existe aucune infrastructure pour surveiller et coordonner la détection d’échec et le basculement automatique. Pour les utilisateurs qui ont besoin de fonctionnalités HADR, utilisez un gestionnaire de cluster (WSFC sous Windows ou Pacemaker sur Linux). 

## <a name="use-distributed-availability-groups-for-geographic-read-scale"></a>Utiliser des groupes de disponibilité distribués pour l’échelle lecture géographique

Les solutions géographiquement séparées permettent d’implémenter des solutions d’échelle lecture avec des groupes de disponibilité distribués. Elles permettent le déchargement des charges de travail de lecture depuis le réplica principal vers les réplicas secondaires lisibles sur des sites plus proches de la source des charges de travail de lecture. Non seulement, l’utilisation des ressources est réduite sur le réplica principal, mais le débit de lecture est aussi amélioré en réduisant la latence du réseau et en exploitant les ressources dédiées.

Un même groupe de disponibilité distribué peut avoir jusqu’à 17 réplicas secondaires lisibles. Pour augmenter la capacité de mise à l’échelle, créez une chaîne en série de plusieurs groupes de disponibilité et augmentez le nombre de réplicas lisibles encore plus. Vous pouvez également déployer deux groupes de disponibilité distribués à partir du même groupe de disponibilité pour atteindre des lectures à faible latence dans les environnements géographiquement dispersés.




## <a name="next-steps"></a>Étapes suivantes 

[Configurer le groupe de disponibilité avec échelle lecture sur Linux](../../../linux/sql-server-linux-availability-group-configure-rs.md)

## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  

