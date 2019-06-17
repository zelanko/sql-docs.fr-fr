---
title: Nouveautés de SQL Server 2019 | Microsoft Docs
ms.date: 05/28/2019
ms.prod: sql-server-2019
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d165900617723fcd91a88c17db630b2d4ac29c1c
ms.sourcegitcommit: d44fa4170c2f586f264e31906c7916a74d080aef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66810284"
---
# <a name="whats-new-in-includesql-server-2019includessssqlv15-mdmd"></a>Nouveautés de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] s’appuie sur les versions précédentes pour faire de SQL Server une plateforme compatible avec de nombreux langages de développement, types de données et systèmes d’exploitation, localement ou dans le cloud. Cet article résume les nouveautés de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Cet article récapitule les fonctionnalités de chaque version et redirige vers plus de détails pour chacune d’entre elles. La section [Détails](#details) fournit des détails techniques concernant les fonctionnalités qui peuvent ne pas être disponibles dans la documentation de base. Les autres sections de cet article fournissent des informations sur toutes les fonctionnalités publiées à ce jour pour cette préversion [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Pour obtenir plus d’informations et découvrir les problèmes connus, consultez les [Notes de publication de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](sql-server-ver15-release-notes.md).

**Utilisez les [derniers outils](#tools) pour une expérience optimale avec [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].**

## <a name="ctp-30-may-2019"></a>CTP 3.0 mai 2019

CTP (Community Technology Preview) 3.0 est la dernière version publique de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. Cette version inclut des améliorations des versions précédentes de CTP qui corrigent des bogues, renforcent la sécurité et optimisent les performances.

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

Pour connaître des fonctionnalités spécifiques exclues de la prise en charge, consultez les [notes de publication](sql-server-ver15-release-notes.md).

De plus, les fonctionnalités suivantes sont ajoutées ou améliorées pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 3.0.

### <a name="big-data-clusters"></a>Clusters Big Data

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| Mises à jour de **mssqlctl** | Plusieurs [mises à jour de commande et de paramètre](../big-data-cluster/reference-mssqlctl.md) **mssqlctl**. Ces dernières incluent une mise à jour de la commande **mssqlctl login**, qui cible désormais le nom d’utilisateur et le point de terminaison du contrôleur. |
| Améliorations du stockage | Prise en charge de différentes configurations de stockage pour les journaux et les données. En outre, le nombre de revendications de volume persistant pour un cluster Big Data a été réduit. |
| Plusieurs instances de pool de calcul | Prise en charge de plusieurs instances de pool de calcul. |
| Nouveaux comportement et fonctionnalités pour les pools | Le pool de calcul est maintenant utilisé par défaut pour les opérations de pool de données et de pool de stockage dans une distribution **ROUND_ROBIN** uniquement. Le pool de données peut désormais utiliser un nouveau type de distribution **REPLICATED**, ce qui signifie que les mêmes données sont présentes sur toutes les instances de pool de données. |
| Améliorations des tables externes | Les tables externes de type de source de données HADOOP prennent maintenant en charge la lecture des lignes d’une taille maximale de 1 Mo. Dans les tables externes (ODBC, pool de stockage, pool de données), les lignes peuvent désormais être aussi larges que dans une table SQL Server. |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Moteur de base de données

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Extensions de langage SQL Server - [Extension de langage Java](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview)|Le [SDK d’extensibilité Microsoft pour Java pour Microsoft SQL Server](https://docs.microsoft.com/sql/language-extensions/how-to/extensibility-sdk-java-sql-server) est désormais open source et [disponible sur GitHub](https://github.com/microsoft/sql-server-language-extensions).|
|Inscrire les langages externes|Un nouveau DDL, `CREATE EXTERNAL LANGUAGE`, inscrit les langages externes, tels que Java, dans SQL Server. Consultez [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md). |
|Davantage de types de données pris en charge pour Java|Consultez [Types de données Java](../language-extensions/how-to/java-to-sql-data-types.md).|
|Stratégie de capture personnalisée pour le Magasin des requêtes|Quand cette fonctionnalité est activée, vous pouvez affiner la collecte de données dans un serveur spécifique au moyen de configurations supplémentaires du Magasin des requêtes disponibles sous un nouveau paramètre de stratégie de capture pour le Magasin des requêtes. Pour plus d’informations, consultez l’article [Options SET d’ALTER DATABASE](../t-sql/statements/alter-database-transact-sql-set-options.md).|
|La fonctionnalité de [base de données en mémoire](../relational-databases/in-memory-database.md) introduit une nouvelle syntaxe DDL pour le contrôle du pool de mémoires tampons hybride. <sup>2</sup>|Avec le [pool de mémoires tampons hybride](../database-engine/configure-windows/hybrid-buffer-pool.md), les pages de base de données qui se trouvent sur des fichiers de base de données placés sur un appareil à mémoire persistante (PMEM) sont directement accessibles si nécessaire.|
|Nouvelle fonctionnalité de base de données en mémoire, ajout de métadonnées tempdb à mémoire optimisée.|Consultez [Métadonnées tempdb à mémoire optimisée](../relational-databases/databases/tempdb-database.md#memory-optimized-tempdb-metadata).|
|Les serveurs liés prennent en charge le codage de caractères UTF-8. |[Prise en charge d'Unicode et du classement](../relational-databases/collations/collation-and-unicode-support.md) |
|Le programme d’installation de SQL Server inclut des recommandations relatives à MaxDOP qui suivent les instructions documentées. |[Configurer l'option de configuration du serveur Degré maximal de parallélisme](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines)|
|`sys.dm_exec_query_plan_stats` retourne plus d’informations sur le degré de parallélisme et les allocations de mémoire pour les plans de requête. |[sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
| &nbsp; | &nbsp; |

><sup>1</sup> Il s’agit d’une fonctionnalité à activer qui nécessite l’activation de l’[indicateur de trace](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451.
>
><sup>2</sup> Un indicateur de trace n’est plus nécessaire pour activer le pool de mémoires tampons hybride.

### [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] prend en charge les bases de données à instance managée Azure SQL Database.| Hébergement de [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] sur une instance managée. Consultez [Installation et configuration de [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]](../master-data-services/master-data-services-installation-and-configuration.md#SetUpWeb).
| &nbsp; | &nbsp; |

### <a name="analysis-services"></a>Analysis Services

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
|Prise en charge des requêtes MDX pour les modèles tabulaires avec des groupes de calcul. |Cette version supprime une limitation antérieure dans les [groupes de calcul](#calc-ctp24). |
|Mise en forme dynamique des mesures à l’aide de groupes de calcul. |Cette fonctionnalité vous permet de changer conditionnellement des chaînes de format pour les mesures avec des [groupes de calcul](#calc-ctp24). Par exemple, avec la conversion monétaire, une mesure peut être affichée à l’aide de différents formats de devises étrangères.|

## <a name="ctp-25-april-2019"></a>CTP 2.5 avril 2019

### <a name="big-data-clusters"></a>Clusters Big Data

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| Profils de déploiement | Utilisent des [fichiers JSON de configuration du déploiement](../big-data-cluster/deployment-guidance.md#configfile) par défaut et personnalisés pour les déploiements de clusters big data au lieu de variables d’environnement. |
| Déploiements demandés | `mssqlctl cluster create` demande désormais à l’utilisateur de saisir les paramètres requis pour les déploiements par défaut. |
| Changements de point de terminaison de service et de nom de pod | Pour plus d’informations, consultez les [Notes de publication concernant les clusters Big Data](../big-data-cluster/release-notes-big-data-cluster.md). |
| Améliorations **mssqlctl** | Utilisez **mssqlctl** pour [faire la liste des points de terminaison externes](../big-data-cluster/deployment-guidance.md#endpoints) et vérifiez la version de **mssqlctl** avec le paramètre `--version`. |
| Installation hors connexion | [Conseils pour les déploiements de cluster Big Data hors connexion](../big-data-cluster/deploy-offline.md). |
| Améliorations concernant la hiérarchisation HDFS | Hiérarchisation HDFS vs. stockage d’Amazon S3. Prise en charge d’OAuth pour ADLS Gen2. Fonctionnalité de mise en cache pour améliorer les performances. Pour plus d’informations, consultez [Hiérarchisation HDFS](../big-data-cluster/hdfs-tiering.md) |
| Spark vers connecteur SQL Server | [Comment lire et écrire dans SQL Server à partir de Spark à l’aide du connecteur Spark MSSQL](../big-data-cluster/spark-mssql-connector.md) |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Moteur de base de données

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| PolyBase sur Linux. | [Installer PolyBase](../relational-databases/polybase/polybase-linux-setup.md) sur Linux pour les connecteurs non-Hadoop.<br/><br/>[Mappage de type PolyBase](../relational-databases/polybase/polybase-type-mapping.md). |
| Nouveau kit de développement logiciel en Java pour SQL Server. | Simplifie le développement de programmes Java qui peuvent être exécutés depuis SQL Server. Consultez [Nouveautés de SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md). |
| Extension de la portée des plans disponibles dans DMF `sys.dm_exec_query_plan_stats`. |Consultez [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
| Nouvelle configuration basée sur les bases de données `LAST_QUERY_PLAN_STATS` pour activer `sys.dm_exec_query_plan_stats`. |Consultez la page [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)|
| Nouveaux identificateurs de référence spatiale (SRID). |Le [GDA2020 australien](http://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/datums-projections/gda2020) fournit des données plus robustes et plus précises, mieux alignées avec les systèmes GPS. Les nouveaux SRID sont :<br/><br/> - 7843 - 2D géographique<br/> - 7844 - 3D géographique <br/><br/>La vue [sys.spatial_reference_systems](../relational-databases/system-catalog-views/sys-spatial-reference-systems-transact-sql.md) contient les définitions des nouveaux SRID. |
| &nbsp; | &nbsp; |

><sup>1</sup> Il s’agit d’une fonctionnalité à activer qui nécessite que l’[indicateur de trace](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 soit activé ou que la configuration au niveau de la base de données `LAST_QUERY_PLAN_STATS` ait la valeur ON.

## <a name="ctp-24-march-2019"></a>CTP 2.4 mars 2019

### <a name="big-data-clusters"></a>Clusters Big Data

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:---|:---|
| Conseils sur la prise en charge de GPU pour l’exécution de Deep Learning avec TensorFlow dans Spark. | [Déploie un cluster de Big Data avec prise en charge du GPU et exécute TensorFlow](../big-data-cluster/spark-gpu-tensorflow.md). |
| Les sources de données **SqlDataPool** et **SqlStoragePool** ne sont plus créées par défaut. | Créez-les manuellement si besoin. Passer en revue les [problèmes connus](../big-data-cluster/release-notes-big-data-cluster.md#externaltablesctp24). |
| Prise en charge d’`INSERT INTO SELECT` pour le pool de données. | Pour obtenir un exemple, consultez [Tutoriel : Recevoir des données dans un pool de données SQL Server avec Transact-SQL](../big-data-cluster/tutorial-data-pool-ingest-sql.md). |
| Options `FORCE SCALEOUTEXECUTION` et `DISABLE SCALEOUTEXECUTION`. | Consultez les [Notes de publication pour les clusters de Big data](../big-data-cluster/release-notes-big-data-cluster.md#whats-new).|
| Recommandations pour le déploiement d’AKS mises à jour. | Lorsque vous évaluez les clusters de Big Data sur AKS, nous recommandons à présent d’utiliser un seul nœud de taille **Standard_L8s**. |
| Mise à niveau du runtime Spark vers Spark 2.4. | |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Moteur de base de données

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Le message d’erreur de troncation inclut par défaut les noms de tables et de colonnes, ainsi que la valeur tronquée.|[VERBOSE_TRUNCATION_WARNINGS](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#verbose-truncation)|
|La nouvelle fonctions de gestion dynamique (DMF) `sys.dm_exec_query_plan_stats` retourne l’équivalent du dernier plan d’exécution réel connu pour la plupart des requêtes. |[sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
|Le nouvel événement étendu `query_post_execution_plan_profile` collecte l’équivalent d’un plan d’exécution réel basé sur le profilage léger, contrairement à `query_post_execution_showplan` qui utilise le profilage standard. |[Infrastructure du profilage de requête](../relational-databases/performance/query-profiling-infrastructure.md)|
|Analyse (suspension et reprise) TDE (Transparent Data Encryption).|[Analyse (suspension et reprise) TDE (Transparent Data Encryption)](../relational-databases/security/encryption/transparent-data-encryption.md#scan-suspend-resume)|
| &nbsp; | &nbsp; |

><sup>1</sup> Il s’agit d’une fonctionnalité à activer qui nécessite l’activation de l’[indicateur de trace](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451.

### <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS)

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Relations plusieurs-à-plusieurs dans les modèles tabulaires.|[Relations plusieurs-à-plusieurs dans les modèles tabulaires](#many-to-many-ctp24)|
|Paramètres de propriété pour la gouvernance des ressources.|[Paramètres de propriété pour la gouvernance des ressources](#property-ctp24)|
| &nbsp; | &nbsp; |

## <a name="ctp-23-february-2019"></a>CTP 2.3 février 2019

### <a name="big-data-clusters"></a>Clusters Big Data

| Nouvelle fonctionnalité ou mise à jour | Détails |
| :---------- | :------ |
| Envoyer des travaux Spark sur des clusters Big Data dans IntelliJ. | [Envoie des travaux Spark sur des clusters Big Data SQL Server dans IntelliJ](../big-data-cluster/spark-submit-job-intellij-tool-plugin.md) |
| CLI courantes pour la gestion des clusters et le déploiement des applications. | [Comment déployer une application sur un cluster Big Data de SQL Server 2019 (préversion)](../big-data-cluster/big-data-cluster-create-apps.md) |
| Extension de VS Code pour déployer des applications sur un cluster de Big Data. | [Comment utiliser VS Code pour déployer des applications sur les clusters Big Data de SQL Server](../big-data-cluster/app-deployment-extension.md) |
| Modifications apportées à l’utilisation des commandes de l’outil **mssqlctl**. | Pour plus d’informations, consultez les [problèmes connus pour mssqlctl](../big-data-cluster/release-notes-big-data-cluster.md#mssqlctlctp23). |
| Utilisation de Sparklyr dans les clusters Big Data. | [Utiliser Sparklyr dans des clusters Big Data SQL Server 2019](../big-data-cluster/sparklyr-from-RStudio.md) |
| Monter un stockage compatible HDFS externe dans le cluster Big Data avec une **hiérarchisation HDFS**. | Consultez [Hiérarchisation HDFS](../big-data-cluster/hdfs-tiering.md). |
| Nouvelle expérience de connexion unifiée pour l’instance principale de SQL Server et la passerelle HDFS/Spark. | Consultez [Instance principale de SQL Server et passerelle HDFS/Spark](../big-data-cluster/connect-to-big-data-cluster.md). |
| La suppression d’un cluster avec **mssqlctl cluster delete** supprime désormais uniquement les objets dans l’espace de noms qui faisaient partie du cluster Big Data. | L’espace de noms n’est pas supprimé. Toutefois, dans les versions antérieures, cette commande supprimait l’espace de noms dans son intégralité. |
| Les noms de point de terminaison de _Sécurité_ ont été modifiés et consolidés. | **service-security-lb** et **service-security-nodeport** ont été consolidés dans le point de terminaison **endpoint-security**. |
| Les noms de point de terminaison de _Proxy_ ont été modifiés et consolidés. | **service-proxy-lb** et **service-proxy-nodeport** ont été consolidés dans le point de terminaison **endpoint-service-proxy**. |
| Les noms de point de terminaison de _Contrôleur_ ont été modifiés et consolidés. | **service-mssql-controller-lb** et **service-mssql-controller-nodeport** ont été consolidés dans le point de terminaison **endpoint-controller**. |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Moteur de base de données

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Activer la récupération accélérée de la base de données peut être activé par base de données.| [Récupération de base de données accélérée](../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#adr)|
|Prise en charge de la possibilité de forcer le plan du Magasin des requêtes pour l’avance rapide et les curseurs statiques.|[Prise en charge de la possibilité de forcer le plan pour l’avance rapide et les curseurs statiques](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md#ctp23) |
|Recompilations réduites pour les charges de travail qui utilisent des tables temporaires sur plusieurs étendues. |[Recompilations réduites pour les charges de travail](../relational-databases/tables/tables.md#ctp23) |
|Scalabilité du point de contrôle indirect améliorée. |[Scalabilité du point de contrôle indirect améliorée](../relational-databases/logs/database-checkpoints-sql-server.md#ctp23)|
|il est maintenant possible d’utiliser l’encodage de caractères UTF-8 avec le classement BIN2 (`UTF8_BIN2`). |[Prise en charge d'Unicode et du classement](../relational-databases/collations/collation-and-unicode-support.md) |
|Définir les actions de suppression en cascade au niveau d’une contrainte d’arête dans une base de données de graphe. |[Contraintes d’arête](../relational-databases/tables/graph-edge-constraints.md) |
|Activer ou désactiver `LIGHTWEIGHT_QUERY_PROFILING` avec la nouvelle configuration étendue aux bases de données. |[`LIGHTWEIGHT_QUERY_PROFILING`](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#lqp) |
| &nbsp; | &nbsp; |

### <a name="tools"></a>Outils

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Azure Data Studio prend en charge Azure Active Directory. |[Azure Data Studio](../azure-data-studio/what-is.md) |
|Déplacement de l’interface utilisateur du mode Notebook vers le noyau Azure Data Studio. |[Comment gérer des notebooks dans Azure Data Studio](../big-data-cluster/notebooks-how-to-manage.md) |
|Ajout d’un nouvel Assistant pour créer des sources de données externes à partir du système de fichiers DFS Hadoop (HDFS) dans un cluster Big Data de SQL Server. | [Outils](#tools-ctp23)|
|Amélioration de l’interface utilisateur de la visionneuse Notebook. | [Outils](#tools-ctp23) |
|Ajout de nouvelles API Notebook.| [Outils](#tools-ctp23) |
|Ajout de la commande « Réinstaller des dépendances Notebook » pour faciliter les mises à jour de package Python. | [Outils](#tools-ctp23) |
|Lancement d’Azure Data Studio à partir de SSMS.| [Outils](#tools-ctp23) |
| &nbsp; | &nbsp; |

### <a name="analysis-services"></a>Analysis Services

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Groupes de calcul dans le modèle tabulaire.| [Groupes de calcul dans le modèle tabulaire](#calc-ctp24) |
| &nbsp; | &nbsp; |

## <a name="ctp-22-december-2018"></a>CTP 2.2, décembre 2018

### <a name="big-data-clusters"></a>Clusters Big Data

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Utiliser SparkR à partir d’Azure Data Studio sur un cluster Big Data. | |
|Déployer des applications Python et R.|[Déployer des applications à l’aide de mssqlctl](../big-data-cluster/big-data-cluster-create-apps.md) |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Moteur de base de données

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Il est maintenant possible d’utiliser l’encodage de caractères UTF-8 avec la réplication SQL Server. |[Prise en charge d'Unicode et du classement](../relational-databases/collations/collation-and-unicode-support.md#ctp23) |
| &nbsp; | &nbsp; |


### <a name="sql-server-on-linux"></a>SQL Server sur Linux

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Groupe de disponibilité Always On sur des conteneurs Docker avec Kubernetes. |[Groupes de disponibilité AlwaysOn pour les conteneurs](../linux/sql-server-ag-kubernetes.md) |
| &nbsp; | &nbsp; |

## <a name="ctp-21-november-2018"></a>CTP 2.1, novembre 2018

### <a name="database-engine"></a>Moteur de base de données

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Il est maintenant possible de sélectionner le classement UTF-8 par défaut lors de l’installation de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. |[Prise en charge d'Unicode et du classement](../relational-databases/collations/collation-and-unicode-support.md#ctp23) |
|L’inlining de fonctions UDF scalaires transforme des fonctions scalaires définies par l’utilisateur (UDF) en expressions relationnelles et les incorpore à la requête SQL d’appel. |[Incorporation (inlining) des fonctions UDF scalaires](../relational-databases/user-defined-functions/scalar-udf-inlining.md) |
|La colonne `command` de la vue de gestion dynamique `sys.dm_exec_requests` indique `SELECT (STATMAN)` si une instruction `SELECT` attend la fin d’une opération de mise à jour synchrone des statistiques pour poursuivre l’exécution de la requête. | [`sys.dm_exec_requests`](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) |
|Le nouveau type d’attente `WAIT_ON_SYNC_STATISTICS_REFRESH` est exposé dans la vue de gestion dynamique `sys.dm_os_wait_stats`. Il montre le temps, cumulé par instance, consacré aux opérations d’actualisation synchrone des statistiques.|[`sys.dm_os_wait_stats`](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md) |
|Le pool de mémoires tampons hybride est une nouvelle fonctionnalité du Moteur de base de données SQL Server selon laquelle les pages de base de données qui se trouvent sur des fichiers de base de données placés sur un appareil à mémoire persistante (PMEM) sont directement accessibles si nécessaire.|[Pool de mémoires tampons hybride](../database-engine/configure-windows/hybrid-buffer-pool.md) |
|[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit le masquage statique des données. Vous pouvez l’utiliser pour nettoyer les données sensibles dans des copies de bases de données SQL Server.|[Masquage statique des données](../relational-databases/security/static-data-masking.md) |
|Utilisation d’alias de tables dérivées ou de vues dans les requêtes de correspondance de graphe |[Contraintes d’arête de graphe](../relational-databases/tables/graph-edge-constraints.md) |
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>SQL Server sur Linux

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Nouveau registre de conteneurs pour SQL Server. |[Prise en main des conteneurs SQL Server sur Docker](../linux/quickstart-install-connect-docker.md) |
| &nbsp; | &nbsp; |

### <a name="tools"></a>Outils

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|[Azure Data Studio](../azure-data-studio/what-is.md) prend en charge la connexion et la gestion des clusters Big Data [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. | |
| &nbsp; | &nbsp; |

## <a name="ctp-20-october-2018"></a>CTP 2.0, octobre 2018

### <a name="big-data-clusters"></a>Clusters Big Data

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Déployer un cluster Big Data avec des conteneurs [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et Spark Linux sur Kubernetes. | |
|Accéder à votre Big Data à partir du système HDFS. | |
|Exécuter l’analytique avancée et le Machine Learning avec Spark. | |
|Utiliser Spark Streaming pour envoyer des données aux pools de données SQL. | |
|Exécuter des livres de requêtes qui procurent une expérience de bloc-notes dans **Azure Data Studio**.|[Engineering données](../azure-data-studio/what-is.md#data-engineering)|
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Moteur de base de données

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Le niveau de compatibilité **COMPATIBILITY_LEVEL 150** de base de données a été ajouté. |[Niveau de compatibilité ALTER DATABASE (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) |
|Création d’index en ligne pouvant être reprise.|[CREATE INDEX (Transact-SQL)](../t-sql/statements/create-index-transact-sql.md#resumable-indexes) |
|Rétroaction d’allocation de mémoire en mode ligne. |[Rétroaction d’allocation de mémoire en mode ligne](../relational-databases/performance/intelligent-query-processing.md#row-mode-memory-grant-feedback) |
|`COUNT DISTINCT` approximatif.|[Traitement des requêtes approximatif](../relational-databases/performance/intelligent-query-processing.md#approximate-query-processing)|
|Mode Batch sur rowstore.|[Mode Batch sur rowstore](../relational-databases/performance/intelligent-query-processing.md#batch-mode-on-rowstore) |
|Compilation différée de variable de table.|[Compilation différée de variable de table](../relational-databases/performance/intelligent-query-processing.md#table-variable-deferred-compilation) |
|Extension pour langage Java.|[Extension pour langage Java](../advanced-analytics/java/extension-java.md) |
|Fusionnez vos données de graphe actuelles à partir des tables de nœuds ou d’arêtes avec de nouvelles données à l’aide des prédicats `MATCH` dans l’instruction `MERGE`. | |
|Contraintes d’arête.|[Contraintes d’arête de graphe](../relational-databases/tables/graph-edge-constraints.md) |
|Paramétrage par défaut au niveau de la base de données pour les opérations DDL en ligne et pouvant être reprises.| |
|Les groupes de disponibilité prennent en charge jusqu’à 5 réplicas secondaires synchrones.|[Groupes de disponibilité](../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) |
|Redirection de la connexion en lecture/écriture depuis un réplica secondaire vers le réplica principal|[Redirection de connexion en lecture/écriture depuis un réplica secondaire vers le réplica principal (groupes de disponibilité Always On)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md) |
|Découverte et classification des données SQL.| [Découverte et classification des données SQL](../relational-databases/security/sql-data-discovery-and-classification.md) |
|Prise en charge étendue des appareils de mémoire persistante.|[Pool de mémoires tampons hybride](../database-engine/configure-windows/hybrid-buffer-pool.md) |
|Prise en charge des statistiques de columnstore dans `DBCC CLONEDATABASE`|[Objets blob de statistiques pour les index columnstore](../t-sql/database-console-commands/dbcc-clonedatabase-transact-sql.md#ctp23)|
|`sp_estimate_data_compression_savings` introduit `COLUMNSTORE` et `COLUMNSTORE_ARCHIVE`.|[Remarques pour les index columnstore](../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md#considerations-for-columnstore-indexes)|
|Azure Machine Learning services est pris en charge sur les Clusters de basculement Windows Server. |[Nouveautés - SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)|
|Prise en charge du Machine Learning pour la modélisation basée sur les partitions.|[Nouveautés - SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md) |
|Infrastructure du profilage de requête léger activée par défaut |[Infrastructure légère de profilage des statistiques sur l’exécution des requêtes v3](../relational-databases/performance/query-profiling-infrastructure.md#lightweight-query-execution-statistics-profiling-infrastructure-v3) |
|Nouveaux connecteurs de PolyBase pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata et MongoDB. |[Qu’est-ce que PolyBase ?](../relational-databases/polybase/polybase-guide.md) |
|`sys.dm_db_page_info(database_id, file_id, page_id, mode)` retourne des informations sur une page dans une base de données. |[sys.dm_db_page_info (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)|
|Always Encrypted avec enclaves sécurisées. |[Always Encrypted avec enclaves sécurisées](../relational-databases/security/encryption/always-encrypted-enclaves.md) |
|Générer et regénérer des index en ligne columnstore en cluster. |[Exécuter des opérations en ligne sur les index](../relational-databases/indexes/perform-index-operations-online.md) |
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>SQL Server sur Linux

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Prise en charge de la réplication |[Réplication SQL Server sur Linux](../linux/sql-server-linux-replication.md)
|Prise en charge de MSDTC (Microsoft Distributed Transaction Coordinator) |[Comment configurer MSDTC sur Linux](../linux/sql-server-linux-configure-msdtc.md) |
|Prise en charge d’OpenLDAP pour les fournisseurs AD tiers |[Tutoriel : Utiliser l’authentification Active Directory avec SQL Server sur Linux](../linux/sql-server-linux-active-directory-authentication.md) |
|Machine learning sur Linux |[Configurer le Machine Learning sur Linux](../linux/sql-server-linux-setup-machine-learning.md) |
| &nbsp; | &nbsp; |

### <a name="master-data-services"></a>Master Data Services

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|le portail Master Data Services (MDS) ne dépend plus de Silverlight.| Tous les anciens composants Silverlight ont été remplacés par des contrôles HTML.|
| &nbsp; | &nbsp; |

### <a name="security"></a>Sécurité

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|Gestion des certificats dans le Gestionnaire de configuration SQL Server|[Gestion des certificats (Gestionnaire de configuration SQL Server)](../database-engine/configure-windows/manage-certificates.md)
| &nbsp; | &nbsp; |

### <a name="tools"></a>Outils

| Nouvelle fonctionnalité ou mise à jour | Détails |
|:-----|:-----|
|[Azure Data Studio](../azure-data-studio/what-is.md) prend en charge la connexion et la gestion des clusters Big Data [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. |[Qu’est-ce qu’Azure Data Studio](../azure-data-studio/what-is.md)|
|Prend en charge des scénarios utilisant des clusters Big Data SQL Server. |[Extension de SQL Server 2019 (préversion)](../azure-data-studio/sql-server-2019-extension.md)|
|[**SQL Server Management Studio (SSMS) 18.0 (préversion)**](../ssms/sql-server-management-studio-ssms.md) : Prise en charge de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].| |
|Prise en charge d’Always Encrypted avec enclaves sécurisées. |[Always Encrypted avec enclaves sécurisées](../relational-databases/security/encryption/always-encrypted-enclaves.md)|
| &nbsp; | &nbsp; |


## <a name="other-services"></a>Autres services

À compter de la version CTP 2.4, [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] n’introduit pas de nouvelles fonctionnalités pour les services suivants :

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS)

## <a name="details"></a>Détails

### <a id="bigdatacluster"></a>Clusters Big Data

Les [clusters Big Data](../big-data-cluster/big-data-cluster-overview.md) [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] permettent de nouveaux scénarios, notamment les suivants :

- [Prise en charge de GPU pour l’exécution de Deep Learning avec TensorFlow dans Spark](../big-data-cluster/spark-gpu-tensorflow.md). (CTP 2.4)
- Mise à niveau du runtime Spark vers Spark 2.4. (CTP 2.4)
- Prise en charge de `INSERT INTO SELECT` pour le pool de données. (CTP 2.4)
- Clause des options `FORCE SCALEOUTEXECUTION` et `DISABLE SCALEOUTEXECUTION` pour les requêtes de table externe. (CTP 2.4)
- [Envoyer des travaux Spark sur des clusters Big Data [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] dans IntelliJ](../big-data-cluster/spark-submit-job-intellij-tool-plugin.md). (CTP 2.3)
- [Expérience de déploiement et de gestion d’applications](../big-data-cluster/big-data-cluster-create-apps.md) pour diverses applications liées aux données, notamment l’opérationnalisation de modèles Machine Learning à l’aide de R et Python, l’exécution de tâches SQL Server Integration Services (SSIS), et plus encore. (CTP 2.3)
- [Utilisation de Sparklyr dans les clusters Big Data de la [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](../big-data-cluster/sparklyr-from-RStudio.md). (CTP 2.3)
- Monter un stockage compatible HDFS externe dans le cluster Big Data avec une [hiérarchisation HDFS](../big-data-cluster/hdfs-tiering.md). (CTP 2.3)
- Utiliser SparkR à partir d’Azure Data Studio sur un cluster Big Data. (CTP 2.2)
- [Déployer des applications Python et R](../big-data-cluster/big-data-cluster-create-apps.md) (CTP 2.2)
- Déployer un cluster Big Data avec des conteneurs [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et Spark Linux sur Kubernetes. (CTP 2.0)
- Accéder à votre Big Data à partir du système HDFS. (CTP 2.0)
- Exécuter l’analytique avancée et le Machine Learning avec Spark. (CTP 2.0)
- Utiliser Spark Streaming pour envoyer des données aux pools de données SQL. (CTP 2.0)
- Exécuter des livres de requêtes qui procurent une expérience de bloc-notes dans [**Azure Data Studio**](../sql-operations-studio/what-is.md). (CTP 2.0)
 
[!INCLUDE [Big data clusters preview](../includes/big-data-cluster-preview-note.md)]

### <a id="databaseengine"></a> Moteur de base de données

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit ou améliore les nouvelles fonctionnalités suivantes pour le [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].

#### <a name="new-querypostexecutionplanprofile-extended-event-ctp-24"></a>Nouvel événement étendu query_post_execution_plan_profile (CTP 2.4)

Le nouvel événement étendu `query_post_execution_plan_profile` collecte l’équivalent d’un plan d’exécution réel basé sur le profilage léger, contrairement à `query_post_execution_showplan` qui utilise le profilage standard. Pour plus d’informations, consultez [Infrastructure du profilage de requête](../relational-databases/performance/query-profiling-infrastructure.md).

##### <a name="example-1---extended-event-session-using-standard-profiling"></a>Exemple 1 - Session d’événements étendus utilisant le profilage standard

```sql
CREATE EVENT SESSION [QueryPlanOld] ON SERVER 
ADD EVENT sqlserver.query_post_execution_showplan(
    ACTION(sqlos.task_time, sqlserver.database_id, 
    sqlserver.database_name, sqlserver.query_hash_signed, 
    sqlserver.query_plan_hash_signed, sqlserver.sql_text))
ADD TARGET package0.event_file(SET filename = N'C:\Temp\QueryPlanStd.xel')
WITH (MAX_MEMORY=4096 KB, EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS, 
    MAX_DISPATCH_LATENCY=30 SECONDS, MAX_EVENT_SIZE=0 KB, 
    MEMORY_PARTITION_MODE=NONE, TRACK_CAUSALITY=OFF, STARTUP_STATE=OFF);
```

##### <a name="example-2---extended-event-session-using-lightweight-profiling"></a>Exemple 2 - Session d’événements étendus utilisant le profilage léger

```sql
CREATE EVENT SESSION [QueryPlanLWP] ON SERVER 
ADD EVENT sqlserver.query_post_execution_plan_profile(
    ACTION(sqlos.task_time, sqlserver.database_id, 
    sqlserver.database_name, sqlserver.query_hash_signed, 
    sqlserver.query_plan_hash_signed, sqlserver.sql_text))
ADD TARGET package0.event_file(SET filename=N'C:\Temp\QueryPlanLWP.xel')
WITH (MAX_MEMORY=4096 KB, EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS, 
    MAX_DISPATCH_LATENCY=30 SECONDS, MAX_EVENT_SIZE=0 KB, 
    MEMORY_PARTITION_MODE=NONE, TRACK_CAUSALITY=OFF, STARTUP_STATE=OFF);
```

#### <a name="new-dmf-sysdmexecqueryplanstats-ctp-24"></a>Nouvelle fonction de gestion dynamique (DMF) sys.dm_exec_query_plan_stats (CTP 2.4) 

La nouvelle fonction de gestion dynamique (DMF) `sys.dm_exec_query_plan_stats` retourne l’équivalent du dernier plan d’exécution réel connu pour la plupart des requêtes, basé sur le profilage léger. Pour plus d’informations, consultez [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md) et [Infrastructure du profilage de requête](../relational-databases/performance/query-profiling-infrastructure.md). En guise d’exemple, consultez le script suivant :

```sql
SELECT *
FROM sys.dm_exec_cached_plans
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle)
WHERE objtype ='Trigger';
GO
```

Il s’agit d’une fonctionnalité d’activation qui nécessite l’activation de l’[indicateur de trace](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451.

#### <a name="transparent-data-encryption-tde-scan---suspend-and-resume-ctp-24"></a>Analyse (suspension et reprise) TDE (Transparent Data Encryption) - (CTP 2.4)

Afin d’activer [Transparent Data Encryption (TDE)](../relational-databases/security/encryption/transparent-data-encryption.md) sur une base de données, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] doit effectuer une analyse de chiffrement qui lit chaque page du ou des fichiers de données dans le pool de mémoires tampons, puis écrit les pages chiffrées sur un disque. Pour fournir aux utilisateurs un contrôle accru sur l’analyse du chiffrement, [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit la syntaxe d’analyse (suspension et reprise) TDE afin que vous puissiez suspendre l’analyse alors que la charge de travail sur le système est lourde ou pendant les heures vitales pour l’entreprise, puis reprendre l’analyse ultérieurement.

Pour suspendre l’analyse du chiffrement TDE, utilisez la syntaxe suivante :

```sql
ALTER DATABASE <db_name> SET ENCRYPTION SUSPEND;
```

De même, pour reprendre l’analyse du chiffrement TDE, utilisez la syntaxe suivante :

```sql
ALTER DATABASE <db_name> SET ENCRYPTION RESUME;
```

Pour afficher l’état actuel de l’analyse du chiffrement, `encryption_scan_state` a été ajouté à la vue de gestion dynamique `sys.dm_database_encryption_keys`. Il existe également une nouvelle colonne appelée `encryption_scan_modify_date` qui contient la date et l’heure du dernier changement d’état de l’analyse du chiffrement. Notez également que si l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] redémarre pendant l’analyse du chiffrement est dans un état suspendu, un message est consigné dans le journal des erreurs au démarrage, indiquant qu’une analyse existante a été suspendue.

#### <a name="accelerated-database-recovery-ctp-23"></a>Récupération de base de données accélérée (CTP 2.3)

La [récupération de base de données accélérée](/azure/sql-database/sql-database-accelerated-database-recovery/) améliore considérablement la disponibilité des bases de données, notamment en présence de transactions durables, en redéfinissant le processus de récupération du moteur de base de données SQL Server. La [récupération de base de données](../relational-databases/logs/the-transaction-log-sql-server.md?#recovery-of-all-incomplete-transactions-when--is-started) est le processus que SQL Server utilise pour chaque base de données pour démarrer dans un état cohérent (ou propre) en termes de transaction. Une base de données, pour laquelle la récupération de base de données est accélérée, termine la récupération beaucoup plus rapidement après un basculement ou tout autre arrêt qui n’est pas propre. À partir de CTP 2.3, la récupération de base de données accélérée peut être activé par base de données à l’aide de la syntaxe suivante :

```sql
ALTER DATABASE <db_name> SET ACCELERATED_DATABASE_RECOVERY = {ON | OFF}
```

> [!NOTE]
> Cette syntaxe n’est pas obligatoire pour tirer parti de cette fonctionnalité dans Azure SQL DB, où elle est [activée sur demande lors de la préversion publique](/azure/sql-database/sql-database-accelerated-database-recovery). Une fois activée, la fonctionnalité est active par défaut.

Si vous avez des bases de données critiques enclines à des transactions volumineuses, essayez cette fonctionnalité dans la préversion. Envoyez vos commentaires à l’[équipe [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]](<https://aka.ms/sqlfeedback>).

#### <a name="query-store-plan-forcing-support-for-fast-forward-and-static-cursors-ctp-23"></a>Prise en charge de la possibilité de forcer le plan du Magasin des requêtes pour l’avance rapide et les curseurs statiques (CTP 2.3)

Le Magasin des requêtes prend désormais en charge la possibilité de forcer des plans d’exécution de requêtes pour l’avance rapide et les curseurs T-SQL et d’API statiques. Ce forçage est à présent pris en charge par le biais de `sp_query_store_force_plan` ou des rapports du Magasin des requêtes SQL Server Management Studio.

#### <a name="reduced-recompilations-for-workloads-using-temporary-tables-across-multiple-scopes-ctp-23"></a>Recompilations réduites pour les charges de travail qui utilisent des tables temporaires sur plusieurs étendues (CTP 2.3)

Avant cette fonctionnalité, quand vous référenciez une table temporaire avec une instruction de langage de manipulation de données (DML) (`SELECT`, `INSERT`, `UPDATE`, `DELETE`), si la table temporaire était créée par un lot d’étendue externe, une recompilation de l’instruction DML se produisait à chacune de ses exécutions. Avec cette amélioration, SQL Server effectue de légères vérifications supplémentaires pour éviter les recompilations inutiles :

- Vérifiez si le module d’étendue externe utilisé pour la création de la table temporaire au moment de la compilation est le même que celui utilisé pour les exécutions consécutives. 
- Gardez une trace de toutes les modifications de langage de définition de données (DDL) apportées au moment de la compilation initiale et comparez-les aux opérations DDL des exécutions consécutives. 

Le résultat final est une réduction des recompilations superflues et du temps processeur.

#### <a name="improved-indirect-checkpoint-scalability-ctp-23"></a>Scalabilité du point de contrôle indirect améliorée (CTP 2.3)

Dans les versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], les utilisateurs peuvent rencontrer des erreurs de planificateur improductives lorsqu’il existe une base de données qui génère un grand nombre de pages de modifications, comme tempdb. [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit une scalabilité améliorée pour le point de contrôle indirect, qui permet d’éviter ces erreurs sur les bases de données dont la charge de travail de mise à jour/insertion est importante.

#### <a name="utf-8-support-ctp-23"></a>Prise en charge d’UTF-8 (CTP 2.3)

Prise en charge complète du codage de caractères UTF-8 courant en tant qu’encodage d’importation ou d’exportation ou que classement de données texte au niveau de la base de données ou des colonnes. UTF-8 est autorisé dans les types de données `CHAR` et `VARCHAR`, et est activé pendant la création du classement d’un objet ou sa modification en un classement avec le suffixe `UTF8`. 

Par exemple,`LATIN1_GENERAL_100_CI_AS_SC` en `LATIN1_GENERAL_100_CI_AS_SC_UTF8`. UTF-8 est uniquement disponible pour les classements Windows qui prennent en charge les caractères supplémentaires, comme introduit dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]. `NCHAR` et `NVARCHAR` autorisent uniquement l’encodage UTF-16 et restent inchangés.

Cette fonctionnalité peut engendrer des économies de stockage importantes, selon le jeu de caractères utilisé. Par exemple, le fait de changer un type de données de colonne existant comportant des chaînes ASCII (Latin) de `NCHAR(10)` en `CHAR(10)` avec un classement prenant en charge UTF-8 se traduit par une réduction de 50 % des besoins en stockage. En effet, `NCHAR(10)` nécessite 20 octets pour le stockage, tandis que `CHAR(10)` nécessite 10 octets pour la même chaîne Unicode.

Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../relational-databases/collations/collation-and-unicode-support.md).

Avec **CTP 2.1**, il est maintenant possible de sélectionner le classement UTF-8 par défaut lors de à l’installation de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Avec **CTP 2.2**, il est maintenant possible d’utiliser l’encodage de caractères UTF-8 avec la réplication SQL Server.

Avec **CTP 2.3**, il est maintenant possible d’utiliser l’encodage de caractères UTF-8 avec le classement BIN2 (UTF8_BIN2).

#### <a name="scalar-udf-inlining-ctp-21"></a>Inlining de fonctions UDF scalaires (CTP 2.1)

L’inlining de fonctions UDF scalaires transforme des fonctions scalaires définies par l’utilisateur (UDF) en expressions relationnelles et les incorpore à la requête SQL d’appel, ce qui améliore les performances des charges de travail qui tirent parti des fonctions UDF scalaires. L’inlining de fonctions UDF scalaires facilite l’optimisation du coût des opérations au sein des fonctions UDF et aboutit à des plans d’exécution efficaces, orientés ensembles et parallèles, par opposition à des plans inefficaces, itératifs et en série. Cette fonctionnalité est activée par défaut sous le niveau de compatibilité de base de données 150.

Pour plus d’informations, consultez [Incorporation des fonctions UDF scalaires](../relational-databases/user-defined-functions/scalar-udf-inlining.md).

#### <a name="a-nametruncation-truncation-error-message-improved-to-include-table-and-column-names-and-truncated-value-ctp-21"></a><a name="truncation" />Amélioration du message d’erreur de troncation, qui inclut les noms de tables et de colonnes, ainsi que la valeur tronquée (CTP 2.1)

Le message d’erreur ID 8152 `String or binary data would be truncated`, connu par de nombreux développeurs et administrateurs [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui développent ou gèrent des charges de travail de déplacement des données, est généré lors des transferts de données entre une source et une destination avec des schémas différents, si la source de données est trop grande pour tenir dans le type de données de destination. La résolution de ce problème peut prendre du temps. [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit un nouveau message d’erreur (2628), plus spécifique, dans ce scénario :  

`String or binary data would be truncated in table '%.*ls', column '%.*ls'. Truncated value: '%.*ls'.`

Le nouveau message d’erreur 2628 apporte davantage de contexte au problème de troncation de données, ce qui simplifie le processus de dépannage. 

**CTP 2.1 et CTP 2.2** Il s’agit d’un message d’erreur d’activation qui nécessite l’activation de l’[indicateur de trace](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 460.

**CTP 2.4** Le message d’erreur 2628 devient le message de troncation par défaut et remplace le message d’erreur 8152 sous le niveau de compatibilité de base de données 150. Une nouvelle de configuration délimitée à la base de données `VERBOSE_TRUNCATION_WARNINGS` est introduite pour basculer entre le message d’erreur 2628 et le message d’erreur 8152 quand le niveau de compatibilité de base de données est 150. Pour plus d’informations, consultez [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).
Pour un niveau de compatibilité de la base de données égal ou inférieur à 140, le message d’erreur 2628 reste un message d’erreur d’activation qui nécessite l’activation de l’[indicateur de trace](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 460.

#### <a name="improved-diagnostic-data-for-stats-blocking-ctp-21"></a>Amélioration des données de diagnostic pour le blocage des statistiques (CTP 2.1)

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] fournit des données de diagnostic améliorées pour les requêtes longues qui attendent des opérations de mise à jour synchrone des statistiques. La colonne `command` de la vue de gestion dynamique `sys.dm_exec_requests` indique `SELECT (STATMAN)` si une instruction `SELECT` attend la fin d’une opération de mise à jour synchrone des statistiques pour poursuivre l’exécution de la requête. Par ailleurs, le nouveau type d’attente `WAIT_ON_SYNC_STATISTICS_REFRESH` est exposé dans la vue de gestion dynamique `sys.dm_os_wait_stats`. Il montre le temps, cumulé par instance, consacré aux opérations d’actualisation synchrone des statistiques.

#### <a name="hybrid-buffer-pool-ctp-21"></a>Pool de mémoires tampons hybride (CTP 2.1)

Le pool de mémoires tampons hybride est une nouvelle fonctionnalité du Moteur de base de données SQL Server selon laquelle les pages de base de données qui se trouvent sur des fichiers de base de données placés sur un appareil à mémoire persistante (PMEM) sont directement accessibles si nécessaire. Compte tenu de la très faible latence des appareils PMEM pour l’accès aux données, le moteur peut renoncer à effectuer une copie des données dans une zone de « pages nettoyées » du pool de mémoires tampons pour simplement accéder directement à la page sur PMEM. L’accès est effectué à l’aide d’E/S mappées en mémoire, comme c’est le cas avec l’état d'éveil à la présence d'un environnement virtualisé. Il en résulte des avantages en matière de performances : sont évitées la copie de la page dans la mémoire DRAM ainsi que la pile d’E/S du système d’exploitation permettant d’accéder à la page sur un stockage persistant. Cette fonctionnalité est disponible sur SQL Server sur Windows et sur SQL Server sur Linux.

Pour plus d’informations, voir [Pool de mémoires tampons hybride](../database-engine/configure-windows/hybrid-buffer-pool.md).

#### <a name="static-data-masking-ctp-21"></a>Masquage statique des données (CTP 2.1)

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit le masquage statique des données. Vous pouvez l’utiliser pour nettoyer les données sensibles dans des copies de bases de données SQL Server. Le masquage statique des données permet de créer une copie expurgée de bases de données, dans laquelle toutes les informations sensibles ont été modifiées d’une manière qui rend la copie partageable avec des utilisateurs hors production. Il peut être utilisé à des fins de développement, de test, d’analyse et de rapports professionnels, de conformité, de dépannage et pour tout autre scénario dans lequel certaines données ne doivent pas être copiées dans différents environnements.

Le masquage statique des données fonctionne au niveau des colonnes. Sélectionnez les colonnes à masquer, puis, pour chaque colonne sélectionnée, spécifiez une fonction de masquage. Le masquage statique des données copie la base de données, puis applique les fonctions de masquage spécifiées aux colonnes.

##### <a name="static-data-masking-vs-dynamic-data-masking"></a>Comparaison entre le masquage statique des données et le masquage dynamique des données

Le masquage des données est le processus qui consiste à appliquer un masque sur une base de données pour masquer des informations sensibles et les remplacer par de nouvelles données ou des données nettoyées. Microsoft propose deux options de masquage : le masquage statique et le masquage dynamique des données. Le masquage dynamique des données a été introduit dans [!INCLUDE[ssSQL16](../includes/sssql16-md.md)]. Le tableau suivant compare ces deux solutions :

|Masquage statique des données |Masquage dynamique des données|
|:----|:----|
|Le masquage se produit sur une copie de la base de données <br/><br/>Les données d’origine ne sont pas récupérables<br/><br/>Le masque s’applique au niveau du stockage<br/><br/>Tous les utilisateurs ont accès aux mêmes données masquées<br/><br/>Destiné à un accès continu pour toute l’équipe|Le masquage se produit sur la base de données d'origine<br/><br/>Les données d'origine sont intactes<br/><br/>Le masque s’applique à la volée au moment de la requête<br/><br/>Le masque varie en fonction de l’autorisation de l’utilisateur <br/><br/>Destiné à un accès ponctuel pour un utilisateur donné|

#### <a name="database-compatibility-level-ctp-20"></a>Niveau de compatibilité de la base de données (CTP 2.0)

Le niveau de compatibilité **COMPATIBILITY_LEVEL 150** de base de données a été ajouté. Pour activer une base de données utilisateur spécifique, exécutez :

   ```sql
   ALTER DATABASE database_name SET COMPATIBILITY_LEVEL =  150;
   ```

#### <a name="resumable-online-index-create-ctp-20"></a>Création d’index en ligne pouvant être reprise (CTP 2.0)

La **création d’index en ligne pouvant être reprise** permet à une opération de création d’index de s’interrompre, puis de reprendre au niveau auquel elle avait été suspendue ou auquel elle avait échoué, au lieu de redémarrer à partir du début.

La création d’index en ligne pouvant être reprise prend en charge les scénarios suivants :
- Reprendre une opération de création d’index après l’échec d’une création d’index, comme après un basculement de base de données ou un manque d’espace disque.
- Interrompre une opération de création d’index puis la reprendre, ce qui permet de libérer temporairement des ressources système en fonction des besoins avant de reprendre l’opération.
- Créer de grands index sans utiliser d’espace journal conséquent ou de transaction à long terme qui bloque les autres activités de maintenance, tout en autorisant la troncation du journal.

Sans cette fonctionnalité, si une opération de création d’index en ligne échoue, elle doit être réexécutée et redémarrée.

Avec cette version, nous étendons les fonctionnalités pouvant être reprises en ajoutant cette fonctionnalité à la [reconstruction d’index en ligne pouvant être reprise](http://azure.microsoft.com/blog/modernize-index-maintenance-with-resumable-online-index-rebuild/).

En outre, vous pouvez définir cette fonctionnalité comme fonctionnalité par défaut pour une base de données spécifique à l’aide du [paramétrage par défaut au niveau de la base de données pour les opérations DDL en ligne et pouvant être reprises](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

Pour plus d’informations, consultez [Création d’index en ligne pouvant être reprise](../t-sql/statements/create-index-transact-sql.md#resumable-indexes).

#### <a name="build-and-rebuild-clustered-columnstore-indexes-online-ctp-20"></a>Génération et regénération d’index columnstore cluster en ligne (CTP 2.0)

Convertissez des tables rowstore au format columnstore. Dans les versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la création d’index cluster columnstore (CCI) était un processus hors connexion durant lequel toutes les modifications devaient être arrêtées. Avec [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] et [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)], vous pouvez créer ou recréer un CCI en ligne. La charge de travail n’est pas bloquée et toutes les modifications effectuées sur les données sous-jacentes sont ajoutées de manière transparente à la table columnstore cible. Voici quelques exemples de nouvelles instructions [!INCLUDE[tsql](../includes/tsql-md.md)] qui peuvent être utilisées :

  ```sql
  CREATE CLUSTERED COLUMNSTORE INDEX cci
    ON <tableName>
    WITH (ONLINE = ON);
  ```

  ```sql
  ALTER INDEX cci
    ON <tableName>
    REBUILD WITH (ONLINE = ON);
  ```

#### <a name="always-encrypted-with-secure-enclaves-ctp-20"></a>Always Encrypted avec enclaves sécurisées (CTP 2.0)

Always Encrypted est étendu avec un chiffrement sur place et des calculs avancés. En effet, il est désormais possible d’effectuer des calculs sur des données en texte clair, à l’intérieur d’une enclave sécurisée côté serveur.

Les opérations de chiffrement incluent le chiffrement des colonnes et la permutation des clés de chiffrement de colonne. Ces opérations peuvent maintenant être émises à l’aide de [!INCLUDE[tsql](../includes/tsql-md.md)] et ne nécessitent pas que les données soient déplacées hors de la base de données. Les enclaves sécurisées permettent d’utiliser Always Encrypted dans un ensemble plus vaste de scénarios qui satisfont aux deux exigences suivantes :  

- Les données sensibles doivent être protégées contre les utilisateurs dotés de privilèges élevés, mais néanmoins non autorisés, y compris les administrateurs de base de données, les administrateurs système, les opérateurs de cloud, ou contre les programmes malveillants.
- Les calculs avancés sur des données protégées doivent être pris en charge au sein du système de base de données.

Pour plus d’informations, consultez [Always Encrypted avec enclaves sécurisées](../relational-databases/security/encryption/always-encrypted-enclaves.md).

> [!NOTE]
> Always Encrypted avec enclaves sécurisés est uniquement disponible sur le système d’exploitation Windows.

#### <a name="intelligent-query-processing-ctp-20"></a>Traitement de requêtes intelligent (CTP 2.0)

- La **rétroaction d’allocation de mémoire en mode ligne** étend la fonctionnalité de rétroaction d’allocation de mémoire introduite dans [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] en ajustant les tailles d’allocation de mémoire pour les opérateurs du mode batch et du mode ligne. Dans le cas d’une allocation de mémoire excessive, si la mémoire allouée est plus de deux fois supérieure à la taille de la mémoire réelle utilisée, la rétroaction d’allocation de mémoire recalcule l’allocation de mémoire. Des exécutions consécutives demandent alors moins de mémoire. Pour une allocation de mémoire dont la taille est insuffisante et qui entraîne un dépassement de capacité sur le disque, la rétroaction d’allocation de mémoire déclenche un nouveau calcul de l’allocation de mémoire. Des exécutions consécutives demandent alors plus de mémoire. Cette fonctionnalité est activée par défaut sous le niveau de compatibilité de base de données 150.

- Le comptage de valeurs approximatif (**APPROX_COUNT_DISTINCT**) retourne le nombre approximatif de valeurs non NULL uniques dans un groupe. Cette fonction est conçue pour une utilisation dans les scénarios Big Data. Elle est optimisée pour les requêtes où toutes les conditions suivantes sont remplies :
   - Accède à des jeux de données comportant au moins des millions de lignes.
   - Agrège une ou plusieurs colonnes qui ont un nombre élevé de valeurs distinctes.
   - Le temps de réponse est plus important que la précision absolue.
      - `APPROX_COUNT_DISTINCT` retourne des résultats qui présentent généralement un écart maximal de 2 % par rapport à la réponse précise.
      - Et il retourne la réponse approximative en beaucoup moins de temps qu’il faudrait pour obtenir la réponse précise.

- La fonctionnalité **mode batch sur les tables rowstore** rend superflue l’utilisation d’un index columnstore pour le traitement d’une requête en mode batch. Le mode batch permet aux opérateurs de requête de travailler sur un ensemble de lignes, plutôt que sur une seule ligne à la fois. Cette fonctionnalité est activée par défaut sous le niveau de compatibilité de base de données 150. Quand toutes les conditions suivantes sont remplies, le mode batch améliore la vitesse des requêtes qui accèdent à des tables rowstore :
   - La requête utilise des opérateurs analytiques tels que les jointures ou des opérateurs d’agrégation.
   - La requête implique au moins 100 000 lignes.
   - La requête dépend davantage de l’UC que des données.
   - La création et l’utilisation d’un index columnstore auraient un des inconvénients suivants :
      - Une surcharge trop importante serait ajoutée à la requête.
      - Ou bien, ces opérations seraient impossibles, car votre application dépend d’une fonctionnalité qui n’est pas encore prise en charge avec les index columnstore.

- La **compilation différée de variable de table** améliore la qualité du plan et les performances globales pour les requêtes faisant référence à des variables de table. Pendant l’optimisation et la compilation initiale, cette fonctionnalité va propager les estimations de cardinalité basées sur le nombre réel de lignes de la variable de table. Ces informations précises sur le nombre de lignes seront utilisées afin d’optimiser les opérations de plan en aval. Cette fonctionnalité est activée par défaut sous le niveau de compatibilité de base de données 150.

Pour utiliser les fonctionnalités de traitement de requête intelligent, définissez le niveau de compatibilité de base de données `COMPATIBILITY_LEVEL = 150`.

#### <a id="programmability"></a> Extensions de programmabilité du langage Java (CTP 2.0)

- **Extension du langage Java (préversion)** : utilisez l’extension du langage Java pour exécuter du code Java dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Dans [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], cette extension est installée quand vous ajoutez la fonctionnalité « Machine Learning Services (en base de données) » à votre instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

#### <a id="sqlgraph"></a> Fonctionnalités Graph SQL (CTP 2.3)

- **Utilisation d’alias de tables dérivées ou de vues dans les requêtes de correspondance de graphe (CTP 2.1)**  : les requêtes de graphe de la préversion de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] prennent en charge les alias de tables dérivées et de vues dans la syntaxe `MATCH`. Les vues et les tables dérivées doivent être créées sur un jeu de tables de nœuds ou d’arêtes avec l’opérateur `UNION ALL` pour que les alias puissent être utilisés dans `MATCH`. Les tables de nœuds ou d’arêtes peuvent comporter des filtres, mais ce n’est pas obligatoire. La possibilité d’utiliser des alias de tables dérivées et de vues dans les requêtes `MATCH` peut se révéler très utile dans les scénarios où la requête porte sur des entités hétérogènes ou des connexions hétérogènes entre deux ou plusieurs entités du graphe.

- **Prise en charge des correspondances dans l’instruction DML `MERGE` (CTP 2.0)** : cette prise en charge permet de spécifier des relations de graphe en une seule instruction, plutôt qu’avec des instructions `INSERT`, `UPDATE` ou `DELETE` distinctes. Fusionnez vos données de graphe actuelles à partir des tables de nœuds ou d’arêtes avec de nouvelles données à l’aide des prédicats `MATCH` dans l’instruction `MERGE`. Cette fonctionnalité autorise les scénarios `UPSERT` sur les tables d’arêtes. Les utilisateurs peuvent désormais utiliser une instruction de fusion unique pour insérer une arête ou mettre à jour une arête entre deux nœuds.

- Les **Contraintes d’arête (CTP 2.0)** sont introduites pour les tables d’arêtes dans Graph SQL. Les tables d’arêtes peuvent connecter n’importe quel nœud à n’importe quel autre nœud dans la base de données. Avec l’introduction des contraintes d’arête, vous pouvez maintenant appliquer certaines restrictions à ce comportement. La nouvelle contrainte `CONNECTION` permet de spécifier le type de nœuds auxquels une table d’arêtes donnée est autorisée à se connecter dans le schéma. 

  **(CTP 2.3) ** En étendant cette fonctionnalité, vous pouvez définir des actions de suppression en cascade sur une contrainte d’arête. Vous pouvez définir les actions effectuées par le moteur de base de données lorsqu’un utilisateur supprime les nœuds, qu’une arête donnée connecte.

#### <a name="database-scoped-default-setting-for-online-and-resumable-ddl-operations-ctp-20"></a>Paramètre par défaut au niveau de la base de données pour les opérations DDL en ligne et pouvant être reprises (CTP 2.0)

- Le **paramétrage par défaut au niveau de la base de données pour les opérations DDL en ligne et pouvant être reprises** permet un paramétrage de comportement par défaut pour les opérations d’index `ONLINE` et `RESUMABLE` au niveau de la base de données, plutôt que la définition de ces options pour chaque instruction DDL d’index telle que la création ou la regénération d’index.

- Définissez ces valeurs par défaut à l’aide des options de configuration de niveau base de données `ELEVATE_ONLINE` et `ELEVATE_RESUMABLE`. Les deux options forcent le moteur à élever automatiquement les opérations prises en charge à une exécution d’index en ligne ou pouvant être reprise. Vous pouvez activer les comportements suivants à l’aide de ces options :

  - L’option `FAIL_UNSUPPORTED` autorise toutes les opérations d’index en ligne ou pouvant être reprises et fait échouer les opérations d’index qui ne sont pas prises en charge dans le cadre d’une utilisation en ligne ou qui ne peuvent pas être reprises.
  - L’option `WHEN_SUPPPORTED` autorise les opérations prises en charge en ligne ou pouvant être reprises et exécute les opérations d’index non prises en charge hors connexion ou ne pouvant pas être reprises.
  - L’option `OFF` autorise le comportement actuel consistant à exécuter toutes les opérations d’index hors connexion et ne pouvant pas être reprises sauf spécification explicite dans l’instruction DDL.

Pour remplacer le paramétrage par défaut, incluez l’option `ONLINE` ou `RESUMABLE` dans les commandes de création ou de regénération d’index. 

Sans cette fonctionnalité, vous devez spécifier les options ONLINE et RESUMABLE directement dans l’instruction DDL telle que la création et la regénération d’index.

Pour plus d’informations sur les opérations d’index pouvant être reprises, consultez [Création d’index en ligne pouvant être reprise](https://azure.microsoft.com/blog/resumable-online-index-create-is-in-public-preview-for-azure-sql-db/).

#### <a id="ha"></a>Groupes de disponibilité Always On - Augmentation du nombre de réplicas synchrones (CTP 2.0)

- **Jusqu’à cinq réplicas synchrones** : dans [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], le nombre maximal de réplicas synchrones est de 5, contre 3 dans [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Vous pouvez configurer ce groupe de cinq réplicas de manière à instaurer le basculement automatique en son sein. Il existe un seul réplica principal, plus quatre réplicas secondaires synchrones.

- **Redirection de la connexion depuis un réplica secondaire vers le réplica principal** : Elle permet de rediriger les connexions d’applications clientes vers le réplica principal, quel que soit le serveur cible spécifié dans la chaîne de connexion. Cette fonctionnalité autorise la redirection d’une connexion sans écouteur. Utilisez la redirection de la connexion depuis un réplica secondaire vers le réplica principal dans les cas suivants :

  - La technologie cluster n’offre pas de fonctionnalité d’écouteur.
  - Configuration de sous-réseaux multiples où la redirection devient complexe.
  - Scénarios d’échelle lecture ou de reprise d’activité où le type de cluster est `NONE`.

Pour plus d’informations, consultez [Redirection de connexion en lecture/écriture depuis un réplica secondaire vers le réplica principal (groupes de disponibilité Always On)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md).

#### <a name="data-discovery-and-classification-ctp-20"></a>Découverte et classification des données (CTP 2.0)

La découverte et la classification des données fournissent des fonctionnalités avancées qui sont intégrées de manière native à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La classification et l’étiquetage de vos données les plus sensibles offrent les avantages suivants :
- Elles aident à répondre aux standards de confidentialité des données et aux exigences de conformité réglementaires.
- Elles prennent en charge les scénarios de sécurité, tels que la supervision (audit) et l’alerte en cas d’accès anormal à des données sensibles.
- Elles facilitent l’identification des emplacements des données sensibles dans l’entreprise, afin que les administrateurs puissent prendre les bonnes mesures pour sécuriser la base de données.

Pour plus d’informations, consultez [Découverte et classification des données SQL](../relational-databases/security/sql-data-discovery-and-classification.md).

[L’audit](../relational-databases/security/auditing/sql-server-audit-database-engine.md) a également été amélioré pour inclure un nouveau champ dans le journal d’audit appelé `data_sensitivity_information`, qui journalise les classifications de sensibilité (étiquettes) des données réelles retournées par la requête. Pour plus d’informations et des exemples, consultez [ADD SENSITIVITY CLASSIFICATION](../t-sql/statements/add-sensitivity-classification-transact-sql.md).

>[!NOTE]
>La façon dont l’audit est activé n’a fait l’objet d’aucune modification. Un nouveau champ a été ajouté aux enregistrements, `data_sensitivity_information`, qui journalise les classifications de sensibilité (étiquettes) des données réelles retournées par la requête. Consultez [Audit de l’accès aux données sensibles](/azure/sql-database/sql-database-data-discovery-and-classification/#subheading-3).

#### <a name="expanded-support-for-persistent-memory-devices-ctp-20"></a>Prise en charge étendue des appareils à mémoire persistante (CTP 2.0)

Tout fichier [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] placé sur un appareil de mémoire persistante peut maintenant fonctionner en mode *compatible*. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] accède directement à l’appareil, en contournant la pile de stockage du système d’exploitation à l’aide d’opérations memcpy efficace. Ce mode améliore les performances, car il permet une faible latence d’entrée/sortie par rapport à ces appareils.
    - Voici quelques exemples de fichiers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] concernés :
        - fichiers de la base de données ;
        - Fichiers journaux de transactions
        - Fichiers de point de contrôle OLTP en mémoire
    - La mémoire persistante est également appelée mémoire de classe de stockage.
    - La mémoire persistante est parfois appelée de manière informelle *pmem* sur certains sites web non-Microsoft.

> [!NOTE]
> Pour cette préversion, la mise en compatibilité des fichiers sur des appareils de mémoire persistante est uniquement disponible sur Linux. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur Windows prend en charge les appareils de mémoire persistante à compter de [!INCLUDE[ssSQL15](../includes/sssql15-md.md)].

#### <a name="support-for-columnstore-statistics-in-dbcc-clonedatabase-ctp-20"></a>Prise en charge des statistiques columnstore dans DBCC CLONEDATABASE (CTP 2.0)

`DBCC CLONEDATABASE` crée une copie de schéma uniquement d’une base de données qui inclut tous les éléments nécessaires pour résoudre les problèmes de performances de requête sans copier les données. Dans les versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la commande ne copiait pas les statistiques permettant de résoudre avec précision les problèmes des requêtes d’index columnstore, ce qui obligeait l’utilisateur à effectuer des étapes manuelles pour capturer ces informations. Maintenant, dans [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], `DBCC CLONEDATABASE` capture automatiquement les objets blob de statistiques pour les index columnstore ; aucune étape manuelle n’est donc requise.

#### <a name="new-options-added-to-spestimatedatacompressionsavings-ctp-20"></a>Ajout d’options à sp_estimate_data_compression_savings (CTP 2.0)

`sp_estimate_data_compression_savings` retourne la taille actuelle de l’objet demandé et estime la taille de l’objet pour l’état de compression demandé. Cette procédure prend en charge trois options : `NONE`, `ROW` et `PAGE`. [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit deux nouvelles options : `COLUMNSTORE` et `COLUMNSTORE_ARCHIVE`. Ces nouvelles options vous permettent d’estimer les économies d’espace si un index columnstore est créé sur la table à l’aide de la compression de columnstore standard ou d’archive.

#### <a id="ml"></a> Clusters de basculement SQL Server Machine Learning Services et modélisation par partitions (CTP 2.0)

- **Modélisation basée sur une partition** : traitez les scripts externes par partition des données en utilisant les nouveaux paramètres ajoutés à `sp_execute_external_script`. Cette fonctionnalité prend en charge l’entraînement de nombreux petits modèles (un modèle par partition de données) au lieu d’un grand modèle.

- **Cluster de basculement Windows Server** : configurez la haute disponibilité pour Machine Learning Services sur un cluster de basculement Windows Server.

Pour des informations détaillées, consultez [Nouveautés de SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

#### <a name="lightweight-query-profiling-infrastructure-enabled-by-default-ctp-20"></a>Infrastructure légère de profilage de requêtes activée par défaut (CTP 2.0)

L’infrastructure du profilage de requête léger fournit les données de performances de requête plus efficacement que les mécanismes de profilage standard. Le profilage léger est maintenant activé par défaut. Il a été introduit dans [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1. Le profilage léger offre un mécanisme de collecte des statistiques d’exécution des requêtes avec une surcharge attendue de 2 % pour l’UC, par rapport à une surcharge pouvant atteindre 75 % pour l’UC dans le cadre du mécanisme de profilage de requête standard. Sur les versions précédentes, il était désactivé (OFF) par défaut. Les administrateurs de base de données peuvent l’activer avec [l’indicateur de trace 7412](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). 

Pour plus d’informations sur le profilage léger, consultez [Infrastructure du profilage de requête](../relational-databases/performance/query-profiling-infrastructure.md).

Avec **CTP 2.3**, une nouvelle configuration étendue à la base de données `LIGHTWEIGHT_QUERY_PROFILING` est introduite pour activer ou désactiver l’infrastructure de profilage de requête légère.

#### <a id="polybase"></a>Nouveaux connecteurs PolyBase

- **Nouveaux connecteurs pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata et MongoDB** : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit de nouveaux connecteurs aux données externes pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata et MongoDB.

#### <a name="new-sysdmdbpageinfo-system-function-returns-page-information-ctp-20"></a>Nouvelle fonction système sys.dm_db_page_info retournant des informations sur une page (CTP 2.0)

`sys.dm_db_page_info(database_id, file_id, page_id, mode)` retourne des informations sur une page dans une base de données. La fonction retourne une ligne qui contient les informations d’en-tête de la page, notamment les `object_id`, `index_id` et `partition_id`. Cette fonction rend superflue l’utilisation de `DBCC PAGE` dans la plupart des cas. 

Afin de faciliter la résolution des problèmes d’attentes liées à une page, une nouvelle colonne nommée page_resource a également été ajoutée à `sys.dm_exec_requests` et `sys.sysprocesses`. Cette nouvelle colonne vous permet de joindre `sys.dm_db_page_info` à ces vues par le biais d’une autre nouvelle fonction : `sys.fn_PageResCracker`. En guise d’exemple, consultez le script suivant :

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d 
  CROSS APPLY sys.fn_PageResCracker(d.page_resource) AS r
  CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id,'DETAILED')
    AS page_info;
```

### <a id="sqllinux"></a> SQL Server sur Linux

- **Groupe de disponibilité Always On sur des conteneurs Docker avec Kubernetes (CTP 2.2)** : Kubernetes peut orchestrer les conteneurs exécutant des instances [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour fournir un ensemble hautement disponible de bases de données avec des groupes de disponibilité SQL Server Always On. Un opérateur Kubernetes déploie une ressource StatefulSet incluant un **conteneur mssql-server** et un moniteur d’intégrité.

- **Nouveau registre de conteneurs (CTP 2.1)** : toutes les images conteneur pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ainsi que pour [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] se trouvent désormais dans le Registre de conteneurs Microsoft. Le Registre de conteneurs Microsoft est le registre de conteneurs officiel pour la distribution de conteneurs de produits Microsoft. De plus, des images basées sur RHEL certifiées sont maintenant publiées.

  - Registre de conteneurs Microsoft : `mcr.microsoft.com/mssql/server:vNext-CTP2.0`
  - Images conteneur basées sur RHEL certifiées : `mcr.microsoft.com/mssql/rhel/server:vNext-CTP2.0`

- **Prise en charge de la réplication (CTP 2.0)**  : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] prend en charge la réplication SQL Server sur Linux. Une machine virtuelle Linux avec l’Agent SQL peut être un serveur de publication, un serveur de distribution ou un abonné. 

  Créez les types de publications suivants :
  - Transactionnelle
  - Snapshot
  - Fusion

  Configurez la réplication avec [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou utilisez des [procédures stockées de réplication](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

- **Prise en charge de MSDTC (Microsoft Distributed Transaction Coordinator) (CTP 2.0)**  : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] sur Linux prend en charge MSDTC (Microsoft Distributed Transaction Coordinator). Pour plus d’informations, consultez [Guide pratique pour configurer MSDTC sur Linux](../linux/sql-server-linux-configure-msdtc.md).

- **Prise en charge d’OpenLDAP pour les fournisseurs AD tiers (CTP 2.0)**  : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] sur Linux prend en charge OpenLDAP, ce qui permet aux fournisseurs tiers de joindre Active Directory.

- **Machine learning sur Linux (CTP 2.0)** : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Machine Learning Services (en base de données) est maintenant pris en charge sur Linux. La prise en charge inclut la procédure stockée `sp_execute_external_script`. Pour obtenir des instructions sur l’installation de Machine Learning Services sur Linux, consultez [Installer la prise en charge en R et Python de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Machine Learning Services sur Linux](../linux/sql-server-linux-setup-machine-learning.md).

### <a id="mds"></a> Master Data Services 

- **Contrôles Silverlight remplacés par des contrôles HTML (CTP 2.0)**  : le portail Master Data Services (MDS) ne dépend plus de Silverlight. Tous les anciens composants Silverlight ont été remplacés par des contrôles HTML.

### <a id="security"></a>Sécurité

- **Gestion des certificats dans le Gestionnaire de configuration SQL Server (CTP 2.0)**  : Les certificats SSL/TLS sont largement utilisés pour accéder à des instances SQL Server. La gestion des certificats est maintenant intégrée au Gestionnaire de configuration SQL Server, ce qui simplifie les tâches courantes telles que les suivantes :

  - Affichage et validation des certificats installés dans une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 
  - Affichage des certificats arrivant à expiration.
  - Déploiement de certificats sur plusieurs machines participant à des groupes de disponibilité Always On (à partir du nœud contenant le réplica principal).
  - Déploiement de certificats sur plusieurs machines participant à une instance de cluster de basculement (à partir du nœud actif).

  > [!NOTE]
  > L’utilisateur doit disposer des autorisations d’administrateur sur tous les nœuds de cluster.

### <a id="tools"></a>Outils

- [**Azure Data Studio**](../azure-data-studio/what-is.md) : précédemment publié sous le nom de préversion SQL Operations Studio, Azure Data Studio est un outil de bureau léger, moderne, open source et multiplateforme pour la réalisation de tâches courantes liées au développement et à l’administration de données. Avec Azure Data Studio et l’[extension de préversion de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](../azure-data-studio/sql-server-2019-extension.md), vous pouvez vous connecter à SQL Server en local et dans le cloud sur Windows, macOS et Linux. Azure Data Studio vous permet d’effectuer les opérations suivantes :

<a name = "tools-ctp23"></a>

  - AAD est désormais pris en charge. (CTP 2.3)
  - Déplacement de l’interface utilisateur du mode Notebook vers le noyau Azure Data Studio. (CTP 2.3)
  - Ajout d’un nouvel Assistant pour créer des sources de données externes à partir du système de fichiers DFS Hadoop (HDFS) dans un cluster Big Data de SQL Server. (CTP 2.3)
  - Amélioration de l’interface utilisateur de la visionneuse Notebook. (CTP 2.3)
  - Ajout de nouvelles API Notebook. (CTP 2.3)
  - Ajout de la commande « Réinstaller des dépendances Notebook » pour faciliter les mises à jour de package Python. (CTP 2.3)
  - Connecter et gérer des clusters Big Data de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. (CTP 2.1)
  - Modifier et exécuter des requêtes dans un environnement de développement moderne avec intégration rapide de contrôles de code source, d’extraits de code et d’Intellisense. (CTP 2.0) 
  - Visualiser rapidement les données grâce à l’intégration de graphiques à vos jeux de résultats. (CTP 2.0)
  - Créer des tableaux de bord personnalisés pour vos serveurs et bases de données à l’aide de widgets personnalisables. (CTP 2.0)  
  - Gérer facilement votre environnement élargi avec le terminal intégré. (CTP 2.0)
  - Analyser les données par le biais d’une expérience de bloc-notes intégrée basée sur Jupyter. (CTP 2.0)
  - Améliorer votre expérience des thèmes et extensions personnalisés. (CTP 2.0)
  - Explorer vos ressources Azure avec un explorateur de ressources et d’abonnements intégré. (CTP 2.0)
  - Prend en charge des scénarios utilisant un cluster Big Data SQL Server. (CTP 2.0)
  
  > [!TIP]
  > Pour connaître les dernières améliorations apportées à Azure Data Studio, consultez les [notes de publication Azure Data Studio](../azure-data-studio/release-notes-azure-data-studio.md).

- [**SQL Server Management Studio (SSMS) 18.0 (préversion)**](../ssms/sql-server-management-studio-ssms.md) : Prise en charge de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

  - Lancement d’Azure Data Studio à partir de SSMS. (CTP 2.3)
  - Prise en charge d’Always Encrypted avec enclaves sécurisées. (CTP 2.0)
  - Taille de téléchargement inférieure. (CTP 2.0)
  - Désormais basé sur le shell isolé Visual Studio 2017. (CTP 2.0)
  - Pour obtenir la liste complète, consultez le [journal des modifications de SSMS](../ssms/release-notes-ssms.md). (CTP 2.0)

- [**Module SQL Server PowerShell**](http://www.powershellgallery.com/packages/SqlServer/21.1.18080) : Le module PowerShell SqlServer permet aux développeurs SQL Server, administrateurs et professionnels de l’informatique décisionnelle d’automatiser l’administration de serveurs et le déploiement de bases de données.

  - Effectuez la mise à niveau de 21.0 vers 21.1 pour prendre en charge SMO v150.
  - Mise à jour du fournisseur SQL Server (SQLRegistration) pour afficher les groupes AS/IS/RS.
  - Correction du problème de l’applet de commande `New-SqlAvailabilityGroup` lors du ciblage de SQL Server 2014.
  - Ajout du paramètre `–LoadBalancedReadOnlyRoutingList` à `Set-SqlAvailabilityReplica` et `New-SqlAvailabilityReplica`.
  - Mise à jour de l’applet de commande `AnalysisService` pour utiliser le jeton de connexion mis en cache à partir de `Login-AzureAsAccount` pour Azure Analysis Services.

### <a id="ssas"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services (SSAS) 

#### <a name="many-to-many-ctp24"></a>Relations plusieurs-à-plusieurs dans les modèles tabulaires (CTP 2.4)

Cette fonctionnalité autorise les relations plusieurs-à-plusieurs entre les tables où les deux colonnes ne sont pas uniques. Une relation peut être définie entre une table de dimension et une table de faits à un niveau de précision supérieur à celui de la colonne clé de la dimension. Cela évite d’avoir à normaliser les tables de dimension et peut améliorer l’expérience utilisateur, car le modèle résultant a un plus petit nombre de tables avec des colonnes regroupées logiquement. Pour cette version CTP 2.4, les relations plusieurs-à-plusieurs sont des fonctionnalités de moteur uniquement. 

Les relations plusieurs-à-plusieurs exigent que les modèles soient au niveau de compatibilité 1470, qui est actuellement pris en charge uniquement dans [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP version 2.3 et ultérieure. Pour cette version CTP 2.4, les relations plusieurs-à-plusieurs peuvent être créées en utilisant l’API de modèle d’objet tabulaire (TOM), le langage TMSL (Tabular Model Scripting Language) et l’outil Éditeur tabulaire open source. Une prise en charge dans SQL Server Data Tools (SSDT) sera incluse dans une version ultérieure, ainsi que sa documentation. Vous trouverez des informations supplémentaires à ce sujet et sur d’autres versions du composant CTP dans le blog Analysis Services.

#### <a name="property-ctp24"></a>Paramètres de mémoire pour la gouvernance des ressources (CTP 2.4)

Les paramètres de mémoire décrits ici sont déjà disponibles dans Azure Analysis Services. À compter de CTP 2.4, ils sont maintenant aussi pris en charge par [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Analysis Services. 

- **Memory\QueryMemoryLimit** : cette propriété de mémoire peut être utilisée pour limiter les spools de mémoire générés par les requêtes DAX soumises au modèle. 
- **DbpropMsmdRequestMemoryLimit** : cette propriété XMLA peut être utilisée pour remplacer la valeur de propriété de serveur Memory\QueryMemoryLimit pour une connexion.
- **OLAP\Query\RowsetSerializationLimit** : cette propriété de serveur limite le nombre de lignes retournées dans un ensemble de lignes, ce qui protège les ressources serveur contre une utilisation de l’exportation des données extensives. Cette propriété s’applique à la fois aux requêtes DAX et aux requêtes MDX.

Ces propriétés peuvent être définies en installant la dernière version de SQL Server Management Studio (SSMS). Vous trouverez des informations supplémentaires concernant cette fonctionnalité dans le blog Analysis Services.

#### <a name="calc-ctp24"></a>Groupes de calcul dans les modèles tabulaires (CTP 2.3) 

Les groupes de calcul traitent un problème courant dans les modèles complexes où des mesures qui utilisent les mêmes calculs peuvent proliférer. Les groupes de calcul apparaissent dans les rapports de clients sous forme de table avec une seule colonne. Chaque valeur incluse dans la colonne représente un calcul réutilisable, ou un élément de calcul, applicable à l’une des mesures.  

Un groupe de calcul peut comporter n’importe quel nombre d’éléments de calcul. Chaque élément de calcul est défini par une expression DAX. Trois nouvelles fonctions DAX sont introduites pour utiliser des groupes de calcul : 

- `SELECTEDMEASURE()` : Retourne une référence à la mesure actuellement dans le contexte.  

- `SELECTEDMEASURENAME()` : Retourne une chaîne contenant le nom de la mesure actuellement dans le contexte.  

- `ISSELECTEDMEASURE(M1, M2, …)` : Retourne une valeur booléenne indiquant si la mesure actuellement dans le contexte est l’une de celles spécifiées en tant qu’argument.

En plus des nouvelles fonctions DAX, deux nouvelles vues de gestion dynamique sont introduites :

- `TMSCHEMA_CALCULATION_GROUPS`  
- `TMSCHEMA_CALCULATION_ITEMS`  

##### <a name="limitations-in-this-release"></a>Limitations dans cette version :

- La fonction `ALLSELECTED DAX` n’est pas encore prise en charge.
- La sécurité au niveau des lignes définie sur la table du groupe de calcul n’est pas encore prise en charge.
- La sécurité au niveau des objets définie sur la table du groupe de calcul n’est pas encore prise en charge.
- Les expressions DetailsRows faisant référence à des éléments de calcul ne sont pas encore prises en charge.
- MDX n’est pas encore pris en charge.

##### <a name="known-issues-in-this-release"></a>Problèmes connus dans cette version :

- Si des groupes de calcul sont présents dans un modèle, les mesures peuvent retourner des types de données Variant, ce qui peut entraîner des échecs de l’actualisation pour les colonnes et les tables calculées qui font référence aux mesures.

##### <a name="compatibility-level"></a>Niveau de compatibilité

Les groupes de calcul exigent que les modèles soient au niveau de compatibilité 1470, qui est actuellement pris en charge uniquement dans [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP version 2.3 et ultérieure. À ce stade, les groupes de calcul peuvent être créés en utilisant l’API TOM (Tabular Object Model), TMSL (Tabular Model Scripting Language) et l’outil Éditeur tabulaire open source. Une prise en charge dans SQL Server Data Tools (SSDT) sera incluse dans une version ultérieure, ainsi que sa documentation. Vous trouverez des informations supplémentaires à ce sujet et sur d’autres versions du composant CTP dans le blog Analysis Services.

## <a name="see-also"></a>Voir aussi

- [`SqlServer` Module PowerShell](https://www.powershellgallery.com/packages/Sqlserver)
- [Documentation SQL Server PowerShell](../powershell/sql-server-powershell.md)

## <a name="next-steps"></a>Étapes suivantes

- [Notes de publication de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](sql-server-ver15-release-notes.md).

- [Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] : Livre blanc technique](http://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Publié en septembre 2018. S’applique à Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 pour conteneurs Docker, Linux et Windows.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
