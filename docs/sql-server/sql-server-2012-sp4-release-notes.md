---
title: "Notes de version de SQL Server 2012 SP4 | Microsoft Docs"
ms.prod: sql-server-2012
ms.technology: server-general
ms.custom: 
ms.date: 10/05/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67cb8b3e-3d82-47f4-840d-0f12a3bff565
caps.latest.revision: 0
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: 1d637aa3e820f1acd6dc283030d2cdfa1e6ca074
ms.contentlocale: fr-fr
ms.lasthandoff: 10/06/2017

---
# <a name="sql-server-2012-sp4-release-notes"></a>Notes de version de SQL Server 2012 SP4
Cette rubrique récapitule les améliorations apportées dans SQL Server 2012 SP4. Elle décrit également les problèmes dont vous devez avoir connaissance avant d’installer ou de dépanner SP4. Les notes de version sont disponibles uniquement en ligne, et non sur un support d’installation. Cette rubrique est mise à jour régulièrement à mesure que des problèmes sont identifiés. Pour obtenir une liste détaillée des corrections apportées dans SP4, consultez [Version SQL Server 2012 SP4](https://go.microsoft.com/fwlink/?linkid=846937).  

> Service Pack 4 inclut toutes les mises à jour cumulatives de SQL Server 2012 SP3.
  
##<a name="download-pages"></a>Pages de téléchargement
Les liens suivants renvoient vers les principaux packages de téléchargement pour SQL Server 2012 SP3. Les pages de téléchargement indiquent la configuration système requise et contiennent des instructions d'installation de base.
- [Installation du correctif SQL Server 2012 SP4](https://go.microsoft.com/fwlink/?linkid=846829)
- [SQL Server 2012 SP4 Express](https://go.microsoft.com/fwlink/?linkid=846905)
- [Microsoft SQL Server 2012 SP4 Feature Pack](https://go.microsoft.com/fwlink/?linkid=846907)

##  <a name="sp4-performance-and-scale-improvements"></a>Améliorations des performances et des capacités de SP4

- **Amélioration de la procédure de nettoyage de l’agent de distribution** : une base de données de distribution surdimensionnée provoquait une situation de blocage et d’interblocage. Cette amélioration vise à éviter certains scénarios de blocage ou d’interblocage. 
- **Mise à l’échelle dynamique des objets mémoire** : les objets mémoire sont partitionnés de façon dynamique en fonction du nombre de nœuds et de cœurs sur le matériel actuel. Le but de la promotion dynamique est d’empêcher les goulots d’étranglement potentiels et de partitionner automatiquement un objet mémoire thread-safe. Les objets mémoire non partitionnés peuvent être promus de façon dynamique pour être partitionnés par nœud. Le nombre de partitions est identique au nombre de nœuds NUMA. Les objets mémoire partitionnés par nœud peuvent ensuite être promus pour être partitionnés par UC, où le nombre de partitions est identique au nombre d’UC.
- **Autoriser un espace > 8 To pour le pool de mémoires tampons** : espace d’adressage virtuel de 128 To disponible pour le pool de mémoires tampons.
- **Nettoyage du suivi des modifications** : amélioration des performances et de l’efficacité du nettoyage du suivi des modifications pour les tables de suivi des modifications. 

## <a name="sp4-supportability-and-diagnostics-improvements"></a>Améliorations de la prise en charge et des diagnostics SP4

- **Prise en charge des vidages complets pour les agents de réplication** : si les agents de réplication rencontrent une exception non gérée, le comportement par défaut actuel est de créer un vidage minimal des symptômes de l’exception. Le comportement par défaut nécessite une procédure de dépannage complexe pour les exceptions non gérées. SP4 introduit une nouvelle clé de Registre, qui prend en charge la création d’un vidage complet pour les agents de réplication.
- **Amélioration des diagnostics dans la sortie XML du plan d’exécution de requêtes** : la sortie XML du plan d’exécution de requêtes contient maintenant des informations sur les indicateurs de trace activés, les fractions de mémoire pour la jointure de boucles imbriquées optimisée, le temps processeur et le temps écoulé. 
- **Amélioration de la corrélation entre les diagnostics XE et DMV** : utilisation des champs query_hash et query_plan_hash pour identifier une requête de façon unique. DMV les définit comme des champs varbinary(8), tandis que XEvent les définit comme des champs UINT64. Étant donné que SQL Server n’utilise pas de valeurs bigint non signées, le cast ne fonctionne pas toujours. Cette amélioration introduit de nouvelles colonnes d’action et de filtre XEvent équivalentes aux champs query_hash et query_plan_hash. La différence est qu’elles sont définies comme des colonnes INT64, ce qui permet une meilleure corrélation des requêtes entre XE et DMV. 
- **Amélioration des diagnostics d’allocation et d’utilisation de la mémoire** : ajout du nouvel XEvent query_memory_grant_usage (transféré de SQL Server 2016 SP1).
- **Ajout du suivi de protocole dans les étapes de négociation SSL** : ajout d’informations de trace des bits pour la réussite ou l’échec de la négociation, telles que le protocole, etc. Ces informations peuvent aider à résoudre certains problèmes de connectivité, par exemple, dans des scénarios de déploiement de TLS 1.2
- **Définition du niveau de compatibilité correct pour la base de données de distribution** : après l’installation du Service Pack, le niveau de compatibilité de la base de données de distribution était changé à 90. Le changement de niveau était dû à un problème avec la procédure stockée sp_vupgrade_replication. Cette procédure stockée a été modifiée afin de définir le niveau de compatibilité correct pour la base de données de distribution. 
- **Nouvelle commande DBCC pour cloner une base de données** : la nouvelle commande DBCC de clonage d’une base de données permet aux utilisateurs avec pouvoir tels que les CSS de résoudre les problèmes rencontrés avec des bases de données de production existantes en clonant le schéma et les métadonnées, sans inclure les données. L’appel est effectué avec la commande DBCC clonedatabase ('nom_base_de_données_source', 'nom_base_de_données_clone'). Les bases de données clonées ne doivent pas être utilisées dans les environnements de production. Pour savoir si une base de données a été générée à partir d’un appel à une base de données clonée, utilisez la commande suivante, select DATABASEPROPERTYEX('clonedb', 'isClone'). La valeur renvoyée 1 est true et la valeur renvoyée 0 est false. 
- **Informations sur les fichiers TempDB et la taille des fichiers dans le journal des erreurs SQL Server** : si la taille et la croissance automatique sont différentes pour les fichiers de données TempDB au démarrage, le nombre de fichiers est indiqué et un avertissement est généré.
- **Messages de prise en charge d’IFI dans le journal des erreurs SQL Server** : dans le journal des erreurs, ils indiquent si l’initialisation instantanée des fichiers de base de données est activée ou désactivée.
- **Nouvelle DMF pour remplacer la commande DBCC INPUTBUFFER** : la nouvelle fonction de gestion dynamique, sys.dm_input_buffer, utilise le paramètre session_id et remplace la commande DBCC INPUTBUFFER
- **Amélioration des événements XEvent liés à un échec du routage en lecture seule pour un groupe de disponibilité** : actuellement, l’événement XEvent read_only_rout_fail est déclenché uniquement si aucun des serveurs de la liste de routage existante n’est disponible pour les connexions. Cette amélioration apporte des informations supplémentaires pour vous aider à résoudre ce type de problème. Elle étend également les points de code où un événement XEvent peut être déclenché. 
- **Amélioration de la gestion de Service Broker avec basculement du groupe de disponibilité** : actuellement, quand Service Broker est activé sur des bases de données du groupe de disponibilité et qu’il y a un basculement du groupe de disponibilité, toutes les connexions Service Broker créées à partir du réplica principal restent ouvertes. L’amélioration ferme toutes les connexions ouvertes pendant un basculement du groupe de disponibilité.
- **[Partitionnement de NUMA logiciel automatique](https://msdn.microsoft.com/library/ms345357(SQL.120).aspx)** : dans SQL Server 2014 SP2, le NUMA logiciel automatique est utilisé quand l’indicateur de trace 8079 est activé au niveau du serveur. Quand l’indicateur de trace 8079 est activé au démarrage, SQL Server 2014 SP2 vérifie la disposition matérielle et configure automatiquement le NUMA logiciel sur les systèmes ayant 8 UC ou plus par nœud NUMA. Le comportement du NUMA logiciel automatique est compatible Hyperthread (processeur logique/HT). Le partitionnement et la création de nœuds supplémentaires permettent de dimensionner le traitement en arrière-plan en augmentant le nombre d’écouteurs, le nombre d’instances, ainsi que les capacités réseau et de chiffrement. Il est recommandé de tester les performances de la charge de travail avec le NUMA logiciel automatique avant de mettre en œuvre cette fonctionnalité dans un environnement de production.

## <a name="see-also"></a>Voir aussi
- [Installer des mises à jour de maintenance de SQL Server 2012](https://msdn.microsoft.com/library/hh479746(v=sql.110).aspx)
- [Comment identifier la version et l'édition de votre SQL Server](https://support.microsoft.com/en-us/help/321185)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

