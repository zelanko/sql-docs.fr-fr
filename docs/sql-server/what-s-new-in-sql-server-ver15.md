---
title: Nouveautés de SQL Server 2019 | Microsoft Docs
ms.date: 08/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 718f0c6c5fa6b517f2b60bbca0f06f58310c6d22
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155482"
---
# <a name="whats-new-in-includesql-server-2019includessssqlv15-mdmd"></a>Nouveautés de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] s’appuie sur les versions précédentes pour faire de SQL Server une plateforme compatible avec de nombreux langages de développement, types de données et systèmes d’exploitation, localement ou dans le cloud.

Cet article récapitule les nouvelles fonctionnalités et améliorations de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Pour obtenir plus d’informations et découvrir les problèmes connus, consultez les [Notes de publication de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](sql-server-ver15-release-notes.md).

**Utilisez les [derniers outils](what-s-new-in-sql-server-ver15-prerelease.md#tools) pour une expérience optimale avec [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].**

>[!NOTE]
>Le contenu est publié pour la version Release Candidate [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. La version Release Candidate est un logiciel en version préliminaire. Les informations peuvent faire l’objet de modification. Pour plus d’informations sur les scénarios de support, consultez [Support](#support).
>
>Cette version comprend des améliorations qui ont été annoncées précédemment dans les versions Community Technology Preview (CTP). Les améliorations ont ajouté des fonctionnalités, corrigé des bogues, améliorent la sécurité et optimisent le niveau de performance. Pour obtenir la liste des fonctionnalités qui ont été ajoutées ou améliorées dans chacune des versions CTP antérieures à la version Release Candidate [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], consultez les précédentes versions [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] des annonces des versions CTP](what-s-new-in-sql-server-ver15-prerelease.md).

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] pour [!INCLUDE[sql-server](../includes/ssnoversion-md.md)]. Il fournit également des capacités supplémentaires et des améliorations pour le moteur de base de données SQL Server, SQL Server Analysis Services, SQL Server Machine Learning Services, SQL Server sur Linux et SQL Server Master Data Services.

Les sections suivantes fournissent une vue d’ensemble de ces fonctionnalités.

## [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| Solution de Big Data scalable | [Déployer des clusters scalables](../big-data-cluster/deploy-get-started.md) de conteneurs SQL Server, Spark et HDFS exécutés sur Kubernetes <br/><br/> Lire, écrire et traiter des Big Data à partir de Transact-SQL ou de Spark<br/><br/> Combiner et analyser facilement des données relationnelles à valeur élevée et un volume élevé de Big Data<br/><br/>Interroger des sources de données externes<br/><br/>Stocker des Big Data dans un système HDFS géré par SQL Server<br/><br/>Interroger les données de plusieurs sources de données externes par le biais du cluster<br/><br/> Utiliser les données pour l’intelligence artificielle, le Machine Learning et d’autres tâches d’analyse<br/><br/> Déployer et exécuter des applications sur [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] <br/><br/> Les bases de données d’instance principale SQL Server utilisent le groupe de disponibilité Always On<br/>|
| &nbsp; | &nbsp; |

Pour plus d’informations, consultez [Que sont les [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]](../big-data-cluster/big-data-cluster-overview.md) SQL Server ?.

La rubrique [Précédentes annonces des versions CTP de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](what-s-new-in-sql-server-ver15-prerelease.md) contient la liste de toutes les fonctionnalités qui ont été annoncées et modifiées dans toutes les versions CTP précédentes.

## <a name="database-engine"></a>Moteur de base de données

### <a name="security"></a>Sécurité

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Indexer les colonnes chiffrées|Créer des index sur des colonnes chiffrées à l’aide d’un chiffrement aléatoire et des clés activées par enclave, afin d’améliorer les performances des requêtes riches (à l’aide de `LIKE` et d’opérateurs de comparaison). Consultez [Always Encrypted avec enclaves sécurisées](../relational-databases/security/encryption/always-encrypted-enclaves.md).
|Suspendre et reprendre l’analyse initiale du chiffrement transparent des données (TDE)|Consultez [Analyse Transparent Data Encryption(TDE) - suspension et reprise](../relational-databases/security/encryption/transparent-data-encryption.md#scan-suspend-resume).|
|Gestion des certificats dans le Gestionnaire de configuration SQL Server|Consultez [Gestion des certificats (Gestionnaire de configuration SQL Server)](../database-engine/configure-windows/manage-certificates.md).|
| &nbsp; | &nbsp; |

### <a name="graph"></a>Graphique

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Actions de suppression en cascade des contraintes d’arête |Définir les actions de suppression en cascade au niveau d’une contrainte d’arête dans une base de données de graphe. Consultez [Contraintes d’arête](../relational-databases/tables/graph-edge-constraints.md). |
|Nouvelle fonction de graphique - `SHORTEST_PATH` | Utilisez `SHORTEST_PATH` à l’intérieur de `MATCH` pour trouver le chemin le plus court entre 2 nœuds dans un graphique ou pour effectuer des traversées de longueur arbitraires.|
|Tables et index de partition| Les données des tables et des index partitionnés sont divisées en unités qui peuvent être réparties sur plusieurs groupes de fichiers d'une base de données de graphe. |
|Utilisation d’alias de tables dérivées ou de vues dans les requêtes de correspondance de graphe |Consultez [Requête de correspondance de graphique](../t-sql/queries/match-sql-graph.md). |
| &nbsp; | &nbsp; |

### <a name="indexes"></a>Index

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|`OPTIMIZE_FOR_SEQUENTIAL_KEY`|Active une optimisation dans le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] qui vous aide à améliorer le débit pour les insertions de haute concurrence dans l’index. Cette option vise les index sujets à contention d’insertion de la dernière page, souvent avec des index comportant une clé séquentielle comme une colonne d’identité, une séquence ou une colonne de date/heure. Pour plus d’informations, consultez [CREATE INDEX](../t-sql/statements/create-index-transact-sql.md#sequential-keys).|
|Générer et régénérer des index columnstore en cluster en ligne | Voir [Exécuter des opérations d’index en ligne](../relational-databases/indexes/perform-index-operations-online.md). |
|Génération d’index rowstore en ligne pouvant être repris | Voir [Exécuter des opérations d’index en ligne](../relational-databases/indexes/perform-index-operations-online.md). |
| &nbsp; | &nbsp; |

### <a name="in-memory-databases"></a>Bases de données en mémoire

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Contrôle DDL pour le pool de tampons hybride |Avec le [pool de mémoires tampons hybride](../database-engine/configure-windows/hybrid-buffer-pool.md), les pages de base de données qui se trouvent sur des fichiers de base de données placés sur un appareil à mémoire persistante (PMEM) sont directement accessibles si nécessaire.|
| &nbsp; | &nbsp; |

### <a name="unicode-support"></a>Prise en charge d’Unicode

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Prise en charge du codage de caractères UTF-8 |Prend en charge le caractère UTF-8 pour l’encodage d’importation et d’exportation, ainsi que le classement au niveau de la base de données ou au niveau des colonnes pour les données de chaîne. Cela prend en charge les applications qui s’étendent à une échelle mondiale, où l’exigence de fournir des applications et des services de base de données multilingues globaux est essentielle pour répondre aux demandes des clients et aux réglementations spécifiques du marché. Consulter [Prise en charge du classement et d’Unicode](../relational-databases/collations/collation-and-unicode-support.md)<br/><br/> La version Release Candidate [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] active la prise en charge d’UTF-8 pour les tables externes Polybase et pour Always Encrypted.|
| &nbsp; | &nbsp; |

### <a name="polybase"></a>PolyBase

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Interroger des tables externes |Les noms des colonnes de table externe sont désormais utilisés pour interroger les sources de données SQL Server, Oracle, Teradata, MongoDB et ODBC. Consultez [Qu’est-ce que PolyBase ?](../relational-databases/polybase/polybase-guide.md).|
|Prise en charge du codage de caractères UTF-8|Prise en charge d’un caractère UTF-8 avec des tables externes. Voir [Prise en charge d’Unicode et du classement](../relational-databases/collations/collation-and-unicode-support.md).|
| &nbsp; | &nbsp; |

### <a name="server-settings"></a>Paramètres du serveur

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Pool de tampons hybride| Une nouvelle fonctionnalité de [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] avec laquelle les pages de base de données qui se trouvent sur des fichiers de base de données placés sur un appareil à mémoire persistante (PMEM) sont directement accessibles si nécessaire. Consultez [Pool de mémoires tampons hybride](../database-engine/configure-windows/hybrid-buffer-pool.md).|
| &nbsp; | &nbsp; |

### <a name="performance-monitoring"></a>analyse des performances.

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|`WAIT_ON_SYNC_STATISTICS_REFRESH` | Nouveau type d’attente dans la vue de gestion dynamique `sys.dm_os_wait_stats`. Il montre le temps, cumulé par instance, consacré aux opérations d’actualisation synchrone des statistiques. Voir [`sys.dm_os_wait_stats`](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|
|Stratégie de capture personnalisée pour le Magasin des requêtes|Quand cette fonctionnalité est activée, vous pouvez affiner la collecte de données dans un serveur spécifique au moyen de configurations supplémentaires du magasin des requêtes, qui sont disponibles sous le nouveau paramètre de stratégie de capture pour le magasin des requêtes. Pour plus d’informations, consultez l’article [Options SET d’ALTER DATABASE](../t-sql/statements/alter-database-transact-sql-set-options.md).|
|`LIGHTWEIGHT_QUERY_PROFILING`|Nouvelle configuration au niveau de la base de données. Voir [`LIGHTWEIGHT_QUERY_PROFILING`](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#lqp). |
|`command` de la colonne `sys.dm_exec_requests` | Affiche `SELECT (STATMAN)` si un `SELECT` attend la fin d’une opération synchrone de mise à jour des statistiques pour poursuivre l’exécution de la requête. Voir [`sys.dm_exec_requests`](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|
|`sys.dm_exec_query_plan_stats` |La nouvelle fonction de gestion dynamique (DMF) retourne l’équivalent du dernier plan d’exécution réel connu pour la plupart des requêtes. Voir [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md).|
|`LAST_QUERY_PLAN_STATS` | Nouvelle configuration au niveau de la base de données pour activer `sys.dm_exec_query_plan_stats`. Consultez la page [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|
|`query_post_execution_plan_profile` | L’événement étendu collecte l’équivalent d’un plan d’exécution réel basé sur le profilage léger, contrairement à `query_post_execution_showplan` qui utilise le profilage standard. Voir [Infrastructure du profilage de requête](../relational-databases/performance/query-profiling-infrastructure.md).|
| &nbsp; | &nbsp; |

### <a name="language-extensions"></a>Extensions de langage

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Nouveau SDK pour le langage Java | Simplifie le développement de programmes Java qui peuvent être exécutés depuis SQL Server. Consultez [Kit de développement logiciel (SDK) d’extensibilité Microsoft pour Java pour SQL Server](../language-extensions/how-to/extensibility-sdk-java-sql-server.md). |
|Le Kit de développement logiciel (SDK) du langage Java est open source |Le [SDK d’extensibilité Microsoft pour Java Microsoft SQL Server](https://docs.microsoft.com/sql/language-extensions/how-to/extensibility-sdk-java-sql-server) est désormais open source et [disponible sur GitHub](https://github.com/microsoft/sql-server-language-extensions).|
|Prise en charge des types de données Java|Consultez [Types de données Java](../language-extensions/how-to/java-to-sql-data-types.md).|
|Nouveau runtime Java par défaut | SQL Server intègre désormais Azul Systems Zulu Embedded pour la prise en charge de Java du produit. Pour plus d’informations, consultez [Free supported Java in SQL Server 2019 is now available](https://cloudblogs.microsoft.com/sqlserver/2019/07/24/free-supported-java-in-sql-server-2019-is-now-available/). |
|Extensions de langage SQL Server| Exécutez le code externe avec l’infrastructure d’extensibilité. Consultez [Extensions de langage SQL Server](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview).
|Inscrire les langages externes|Un nouveau DDL, `CREATE EXTERNAL LANGUAGE`, inscrit les langages externes, tels que Java, dans SQL Server. Consultez [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md). |
| &nbsp; | &nbsp; |

### <a name="spatial"></a>Spatial

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| Nouveaux identificateurs de référence spatiale (SRID) |Le [GDA2020 australien](http://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/datums-projections/gda2020) fournit des données plus robustes et plus précises, mieux alignées avec les systèmes GPS. Les nouveaux SRID sont :<br/><br/> - 7843 pour la 2D géographique<br/> - 7844pour la 3D géographique <br/><br/>La vue [sys.spatial_reference_systems](../relational-databases/system-catalog-views/sys-spatial-reference-systems-transact-sql.md) contient les définitions des nouveaux SRID. |
| &nbsp; | &nbsp; |

### <a name="performance"></a>Performances

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Récupération de base de données accélérée | Activer la récupération accélérée des bases de données pour chaque base de données. Consultez [Récupération accélérée des bases de données](../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#adr).|
|Forcer les curseurs statiques et les curseurs avec avance rapide | Prise en charge de la possibilité de forcer le plan du Magasin des requêtes pour l’avance rapide et les curseurs statiques. Consultez [Planifier la prise en charge du forçage des curseurs statiques et des curseurs avec avance rapide](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md#ctp23).|
|Gouvernance des ressources| La valeur configurable pour l’option `REQUEST_MAX_MEMORY_GRANT_PERCENT` de `CREATE WORKLOAD GROUP` et `ALTER WORKLOAD GROUP` est passée d’un entier à un type de données float, pour permettre un contrôle plus granulaire des limites de la mémoire. Consultez [ALTER WORKLOAD GROUP](../t-sql/statements/alter-workload-group-transact-sql.md) et [CREATE WORKLOAD GROUP](../t-sql/statements/create-workload-group-transact-sql.md).|
|Recompilations réduites pour les charges de travail| Améliore l’utilisation des tables temporaires sur plusieurs étendues. Consultez [Recompilations réduites pour les charges de travail](../relational-databases/tables/tables.md#ctp23) |
|Scalabilité des points de contrôle indirect |Consultez [Amélioration de la scalabilité des points de contrôle indirect](../relational-databases/logs/database-checkpoints-sql-server.md#ctp23).|
|Métadonnée `tempdb` à mémoire optimisée| [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit dans la famille de fonctionnalités [Base de données en mémoire](../relational-databases/in-memory-database.md), une nouvelle fonctionnalité, les métadonnées `tempdb` à mémoire optimisée, qui supprime efficacement ce goulot d’étranglement et déverrouille un nouveau niveau d’extensibilité pour les charges de travail de base de données `tempdb` lourdes. Dans [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], les tables système impliquées dans la gestion des métadonnées de table temporaire peuvent être déplacées dans des tables à mémoire optimisée non durables dépourvues de verrous. Consultez [Métadonnée `tempdb` à mémoire optimisée](../relational-databases/databases/tempdb-database.md#memory-optimized-tempdb-metadata).|
|Mises à jour PFS simultanées|Les [pages PFS](https://techcommunity.microsoft.com/t5/SQL-Server/Under-the-covers-GAM-SGAM-and-PFS-pages/ba-p/383125) sont des pages spéciales dans un fichier de base de données que SQL Server utilise pour localiser l’espace libre lors de l’allocation d’espace d’un objet. La contention de verrous de page sur les pages PFS est une fonctionnalité couramment associée à [`tempdb`](https://support.microsoft.com/en-us/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d), mais elle peut également se produire sur des bases de données utilisateur lorsqu’il existe de nombreux threads d’allocation d’objets simultanés. Cette amélioration modifie la façon dont la concurrence est managée avec les mises à jour PFS afin qu’elles puissent être mises à jour sous un verrou partagé, plutôt qu’avec un verrou exclusif. Ce comportement est activé par défaut dans toutes les bases de données (y compris `tempdb`) en commençant par [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].|
|Rétroaction d’allocation de mémoire en mode ligne |Développe la fonctionnalité de commentaires d’allocation de mémoire en mode batch en ajustant les tailles d’allocation de mémoire pour les opérateurs du mode batch et du mode ligne. Cela peut automatiquement corriger les octrois excessifs qui entraînent une perte de mémoire et une concurrence réduite, et corriger les allocations de mémoire insuffisantes qui entraînent des dépassements de capacité coûteux sur le disque. Consultez [Commentaires d’allocation de mémoire en mode ligne](../relational-databases/performance/intelligent-query-processing.md#row-mode-memory-grant-feedback). |
|Compilation différée de variable de table|Améliore la qualité du plan et le niveau de performance global pour les requêtes faisant référence à des variables de tables. Pendant l’optimisation et la compilation initiale, cette fonctionnalité propage les estimations de cardinalité basées sur le nombre réel de lignes de la variable de table. Ces informations précises sur le nombre de lignes optimisent les opérations de plan en aval. Consultez [Compilation différée de variables de tables](../relational-databases/performance/intelligent-query-processing.md#table-variable-deferred-compilation). |
|`APPROX_COUNT_DISTINCT `|Pour les scénarios dans lesquels la précision absolue n’est pas importante, mais la réactivité est essentielle, les agrégats `APPROX_COUNT_DISTINCT` entre les jeux de données volumineux utilisent moins de ressources que `COUNT(DISTINCT())` pour une concurrence supérieure. Consultez [Traitement des requêtes approximatif](../relational-databases/performance/intelligent-query-processing.md#approximate-query-processing).|
|Mode Batch sur rowstore|Le mode batch sur rowstore permet l’exécution en mode batch sans avoir besoin d’index columnstore. L’exécution en mode batch utilise l’UC plus efficacement pendant les charges de travail analytiques, mais avant [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] on ne l’utilisait uniquement lorsqu’une requête incluait des opérations avec des index columnstore. Toutefois, certaines applications peuvent utiliser des fonctionnalités qui ne sont pas prises en charge avec les index columnstore, et ne peuvent donc pas tirer parti du mode batch. À compter de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], le mode batch est activé sur les charges de travail analytiques éligibles dont les requêtes incluent des opérations avec n’importe quel type d’index (rowstore ou columnstore). Consultez [Mode Batch sur rowstore](../relational-databases/performance/intelligent-query-processing.md#batch-mode-on-rowstore). |
|Incorporation des fonctions UDF scalaires|Transforme automatiquement les fonctions scalaires définies par l’utilisateur en expressions relationnelles, et les incorpore à la requête SQL d’appel. Cette transformation améliore les performances des charges de travail qui tirent parti des fonctions UDF scalaires. Voir [Incorporation (inlining) des fonctions UDF scalaires](../relational-databases/performance/intelligent-query-processing.md#scalar-udf-inlining).|
| &nbsp; | &nbsp; |

### <a name="availability-groups"></a>Groupes de disponibilité

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Jusqu’à cinq réplicas synchrones|[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] augmente le nombre maximal de réplicas synchrones à 5, contre 3 dans [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Vous pouvez configurer ce groupe de cinq réplicas de manière à instaurer le basculement automatique en son sein. Il existe un seul réplica principal, plus quatre réplicas secondaires synchrones.|
|Redirection de la connexion entre un réplica secondaire et un réplica principal| Elle permet de rediriger les connexions d’applications clientes vers le réplica principal, quel que soit le serveur cible spécifié dans la chaîne de connexion. Pour plus d’informations, consultez [Redirection de connexion en lecture/écriture depuis un réplica secondaire vers le réplica principal (groupes de disponibilité Always On)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md).|
| &nbsp; | &nbsp; |

### <a name="setup"></a>Programme d’installation 

|Nouvelle fonctionnalité ou mise à jour | Détails | 
|:---|:---| 
|Nouvelles options de configuration de la mémoire | Définit les configurations de serveur *min server memory (Mo)* et *max server memory (Mo)* au cours de l’installation. Pour plus d’informations, consultez la [page de configuration du moteur de base de données - Mémoire](https://docs.microsoft.com/sql/sql-server/install/instance-configuration?view=sql-server-ver15#memory) ainsi que les paramètres `USESQLRECOMMENDEDMEMORYLIMITS`, `SQLMINMEMORY` et `SQLMAXMEMORY` dans [Installer SQL Server depuis l’invite de commandes](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#Install). La valeur proposée s’aligne sur les lignes directrices de configuration de la mémoire dans les [options de configuration de la mémoire du serveur](../database-engine/configure-windows/server-memory-server-configuration-options.md#setting-the-memory-options-manually).| 
|Nouvelles options d’installation du parallélisme | Définit la configuration du serveur de *degré maximal de parallélisme* pendant l’installation. Pour plus d’informations, consultez la [page de configuration du moteur de base de données - MaxDOP](https://docs.microsoft.com/sql/sql-server/install/instance-configuration?view=sql-server-ver15#maxdop) ainsi que le paramètre `SQLMAXDOP` dans [Installer SQL Server depuis l’invite de commandes](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#Install). La valeur par défaut s’aligne aux lignes directrices du degré maximal de parallélisme dans [Configurer l’option de configuration du serveur de degré maximal de parallélisme](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines).| 
| &nbsp; | &nbsp; |

### <a name="error-messages"></a>Messages d’erreur

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Avertissements détaillés sur la troncation | Le message d’erreur de troncation inclut par défaut les noms de tables et de colonnes, ainsi que la valeur tronquée. Voir [VERBOSE_TRUNCATION_WARNINGS](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#verbose-truncation).|
| &nbsp; | &nbsp; |

## <a name="sql-server-on-linux"></a>SQL Server sur Linux

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Nouveau registre de conteneurs|[Prise en main des conteneurs SQL Server sur Docker](../linux/quickstart-install-connect-docker.md) |
|Prise en charge de la réplication |[Réplication SQL Server sur Linux](../linux/sql-server-linux-replication.md)
|Prise en charge de MSDTC (Microsoft Distributed Transaction Coordinator) |[Comment configurer MSDTC sur Linux](../linux/sql-server-linux-configure-msdtc.md) |
|Prise en charge d’OpenLDAP pour les fournisseurs AD tiers |[Tutoriel : Utiliser l’authentification Active Directory avec SQL Server sur Linux](../linux/sql-server-linux-active-directory-authentication.md) |
|Machine learning sur Linux |[Configurer le Machine Learning sur Linux](../linux/sql-server-linux-setup-machine-learning.md) |
|Améliorations `tempdb` | Par défaut, une nouvelle installation de SQL Server sur Linux crée plusieurs fichiers de données `tempdb` en fonction du nombre de cœurs logiques (avec jusqu’à 8 fichiers de données). Cela ne s’applique pas aux mises à niveau de versions mineures ou majeures sur place. Chaque fichier `tempdb` fait 8 Mo avec une croissance automatique de 64 Mo. Ce comportement est similaire à l’installation de SQL Server par défaut sur Windows. |
| PolyBase sur Linux | [Installer PolyBase](../relational-databases/polybase/polybase-linux-setup.md) sur Linux pour les connecteurs non-Hadoop.<br/><br/>[Mappage de type PolyBase](../relational-databases/polybase/polybase-type-mapping.md). |
| Prise en charge de la capture des changements de données (CDC) | La capture des changements de données (CDC) est désormais prise en charge sur Linux pour SQL Server 2019. |
| &nbsp; | &nbsp; |

## <a id="ml"></a> SQL Server Machine Learning Services

|Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Modélisation basée sur une partition|traitez les scripts externes par partition des données en utilisant les nouveaux paramètres ajoutés à `sp_execute_external_script`. Cette fonctionnalité prend en charge l’entraînement de nombreux petits modèles (un modèle par partition de données) au lieu d’un grand modèle. Voir [Créer des modèles basés sur une partition](../advanced-analytics/tutorials/r-tutorial-create-models-per-partition.md)|
|Cluster de basculement Windows Server| configurez la haute disponibilité pour Machine Learning Services sur un cluster de basculement Windows Server.|
| &nbsp; | &nbsp; |

## [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Prend en charge les bases de données à instance managée Azure SQL Database.| Hébergement de [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] sur une instance managée. Consultez [Installation et configuration de [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]](../master-data-services/master-data-services-installation-and-configuration.md#SetUpWeb).|
|Nouveaux contrôles HTML| Les contrôles HTML remplacent tous les anciens composants Silverlight. La dépendance à Silverlight a été supprimée.|
| &nbsp; | &nbsp; |

## <a name="analysis-services"></a>Analysis Services

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Entrelacement de requêtes| Consulter [Entrelacement de requêtes](https://docs.microsoft.com/analysis-services/tabular-models/query-interleaving) |
|Prise en charge des requêtes MDX pour les modèles tabulaires avec des groupes de calcul. | Consultez [Groupes de calcul](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24). |
|Groupes de calcul dans le modèle tabulaire| [Groupes de calcul dans le modèle tabulaire](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24) |
|Prise en charge des requêtes MDX pour les modèles tabulaires avec des groupes de calcul. | Consultez [Groupes de calcul](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24). |
|Mise en forme dynamique des mesures à l’aide de groupes de calcul |Cette fonctionnalité vous permet de changer conditionnellement des chaînes de format pour les mesures avec des [groupes de calcul](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24). Par exemple, avec la conversion monétaire, une mesure peut être affichée à l’aide de différents formats de devises étrangères.|
|Relations plusieurs-à-plusieurs dans les modèles tabulaires|[Relations plusieurs-à-plusieurs dans les modèles tabulaires](what-s-new-in-sql-server-ver15-prerelease.md#many-to-many-ctp24)|
|Paramètres de propriété pour la gouvernance des ressources|[Paramètres de propriété pour la gouvernance des ressources](what-s-new-in-sql-server-ver15-prerelease.md#property-ctp24)|
| Paramètre de gouvernance pour les actualisations du cache Power BI.  | Le service Power BI met en cache les données de vignettes du tableau de bord et les données de rapport dans le cadre d’un premier chargement du rapport Live Connect, ce qui provoque l’envoi d’un trop grand nombre de requêtes de cache vers SSAS et, dans les cas extrêmes, la surcharge du serveur. Cette version comprend la propriété **ClientCacheRefreshPolicy**. Cette propriété vous permet de substituer ce comportement au niveau du serveur. Pour plus d’informations, consultez [Propriétés générales](https://docs.microsoft.com/analysis-services/server-properties/general-properties). |
| Attachement en ligne  | Cette fonctionnalité offre la possibilité d’attacher un modèle tabulaire dans le cadre d’une opération en ligne. L’attachement en ligne peut être utilisé pour la synchronisation des réplicas en lecture seule dans les environnements locaux de scale-out des requêtes. Pour plus d’informations, consultez [Attachement en ligne](what-s-new-in-sql-server-ver15-prerelease.md#online-attach-ctp32). |
| &nbsp; | &nbsp; |

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

Pour connaître des fonctionnalités spécifiques exclues de la prise en charge, consultez les [notes de publication](sql-server-ver15-release-notes.md).

De plus, les fonctionnalités suivantes ont été ajoutées ou améliorées dans [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 3.2.

## <a name="see-also"></a>Voir aussi

- [`SqlServer` Module PowerShell](https://www.powershellgallery.com/packages/Sqlserver)
- [Documentation SQL Server PowerShell](../powershell/sql-server-powershell.md)

## <a name="next-steps"></a>Étapes suivantes

- Notes de publication d’[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)](sql-server-ver15-release-notes.md).

- [Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] : Livre blanc technique](http://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Publié en septembre 2018. S’applique à Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 pour conteneurs Docker, Linux et Windows.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
