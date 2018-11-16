---
title: Nouveautés de SQL Server 2019 | Microsoft Docs
ms.date: 11/06/2018
ms.prod: sql-server-2018
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 55cf8c1bc9a7a74928ebe2f5c0c7060c94068e48
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703907"
---
# <a name="whats-new-in-sql-server-2019"></a>Nouveautés de SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)] s’appuie sur les versions précédentes pour faire de SQL Server une plateforme compatible avec de nombreux langages de développement, types de données et systèmes d’exploitation, localement ou sur le cloud. Cet article résume les nouveautés de SQL Server 2019. Pour obtenir plus d’informations et découvrir les problèmes connus, consultez les [Notes de publication de SQL Server 2019](sql-server-ver15-release-notes.md).

**Essayez SQL Server 2019 !**
- [![Télécharger à partir du Centre d’évaluation](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?LinkID=862101) [Télécharger SQL Server 2019 en vue de l’installer sur Windows](https://go.microsoft.com/fwlink/?LinkID=862101)
- Installer sur Linux pour [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) et [Ubuntu](../linux/quickstart-install-connect-ubuntu.md).
- [Exécuter SQL Server 2019 sur Docker](../linux/quickstart-install-connect-docker.md).

## <a name="ctp-21"></a>CTP 2.1

Community Technology Preview (CTP) 2.1 est la première version publique de [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)]. Les fonctionnalités suivantes sont ajoutées ou améliorées pour [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)] CTP 2.1.

- [Clusters Big Data](#bigdatacluster)
  - Déployer des applications Python et R
- [Moteur de base de données](#databaseengine)
  - Traitement de requêtes intelligent avec inlining de fonctions UDF
  - Amélioration du message d’erreur de troncation, qui inclut les noms de tables et de colonnes, ainsi que la valeur tronquée
  - Prise en charge de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] par les classements UTF-8 à l’installation
  - Utilisation d’alias de tables dérivées ou de vues dans les requêtes de correspondance de graphe
  - Amélioration des données de diagnostic pour le blocage des statistiques
  - Pool de mémoires tampons hybride
  - Masquage statique des données
- [Outils](#tools)
  - Azure Data Studio

## <a name="ctp-20"></a>CTP 2.0 

Community Technology Preview (CTP) 2.0 est la première version publique de [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)]. Les fonctionnalités suivantes sont ajoutées ou améliorées pour [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)] CTP 2.0.

- [Clusters Big Data](#bigdatacluster)
  - Déployer un cluster Big Data avec des conteneurs SQL et Spark Linux sur Kubernetes
  - Accéder à votre Big Data à partir de HDFS
  - Exécuter l’analytique avancée et le machine learning avec Spark
  - Utiliser Spark Streaming pour envoyer des données aux pools de données SQL
  - Utiliser Azure Data Studio pour exécuter des livres de requêtes qui procurent une expérience de bloc-notes

- [Moteur de base de données](#databaseengine)
  - Prise en charge d’UTF-8
  - La création d’index en ligne pouvant être reprise permet la reprise de la création d’index après une interruption
  - Génération et regénération d’index en ligne columnstore en cluster
  - Always Encrypted avec enclaves sécurisées
  - Traitement de requêtes intelligent
  - Extension de la programmabilité du langage Java
  - fonctionnalités Graph SQL
  - Paramétrage de la configuration au niveau de la base de données pour les opérations DDL en ligne et pouvant être reprises
  - Groupes de disponibilité Always On : redirection de la connexion de réplica secondaire
  - Découverte et classification des données intégrées nativement à SQL Server
  - Prise en charge étendue des appareils de mémoire persistante
  - Prise en charge des statistiques de columnstore dans `DBCC CLONEDATABASE`
  - Nouvelles options ajoutées à `sp_estimate_data_compression_savings`
  - Clusters de basculement SQL Server Machine Learning Services
  - Infrastructure du profilage de requête léger activée par défaut
  - Nouveaux connecteurs PolyBase
  - Nouvelle fonction système `sys.dm_db_page_info` retournant des informations de page

- [SQL Server sur Linux](#sqllinux)
  - Prise en charge de la réplication
  - Prise en charge de MSDTC (Microsoft Distributed Transaction Coordinator)
  - Groupe de disponibilité Always On sur des conteneurs Docker avec Kubernetes
  - Prise en charge d’OpenLDAP pour les fournisseurs AD tiers
  - Machine learning sur Linux
  - Nouveau registre de conteneurs
  - Nouvelles images conteneur basées sur RHEL
  - Notification de sollicitation de la mémoire

- [Master Data Services](#mds)
  - Contrôles Silverlight remplacés

- [Sécurité](#security)
  - Gestion des certificats dans le Gestionnaire de configuration SQL Server

- [Outils](#tools)
  - SQL Server Management Studio (SSMS) 18.0 (préversion)
  - Azure Data Studio

Poursuivez votre lecture pour obtenir plus d’informations sur ces fonctionnalités.

## <a id="bigdatacluster"></a>Clusters Big Data

Les [clusters Big Data](../big-data-cluster/big-data-cluster-overview.md) [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] permettent de nouveaux scénarios, notamment les suivants :

- [Déployer des applications Python et R](../big-data-cluster/big-data-cluster-create-apps.md) (CTP 2.1)
- Déployer un cluster Big Data avec des conteneurs [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et Spark Linux sur Kubernetes (CTP 2.0)
- Accéder à des données Big Data à partir de HDFS (CTP 2.0)
- Exécuter des analyses avancées et du Machine Learning avec Spark (CTP 2.0)
- Utiliser Spark Streaming pour envoyer des données à des pools de données SQL (CTP 2.0)
- Exécuter des livres de requêtes qui procurent une expérience de bloc-notes dans [**Azure Data Studio**](../sql-operations-studio/what-is.md). (CTP 2.0)
 
[!INCLUDE [Big Data Clusters preview](../includes/big-data-cluster-preview-note.md)]

## <a id="databaseengine"></a> Moteur de base de données

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit ou améliore les nouvelles fonctionnalités suivantes pour le Moteur de base de données :

### <a name="scalar-udf-inlining-ctp-21"></a>Inlining de fonctions UDF scalaires (CTP 2.1)

L’inlining de fonctions UDF scalaires transforme des fonctions scalaires définies par l’utilisateur (UDF) en expressions relationnelles et les incorpore à la requête SQL d’appel, ce qui améliore les performances des charges de travail qui tirent parti des fonctions UDF scalaires. L’inlining de fonctions UDF scalaires facilite l’optimisation du coût des opérations au sein des fonctions UDF et aboutit à des plans d’exécution efficaces, orientés ensembles et parallèles, par opposition à des plans inefficaces, itératifs et en série. Cette fonctionnalité est activée par défaut sous le niveau de compatibilité de base de données 150.

Pour plus d’informations, voir [Inlining de fonctions UDF scalaires](../relational-databases/user-defined-functions/scalar-udf-inlining.md).

### <a name="truncation-error-message-improved-to-include-table-and-column-names-and-truncated-value-ctp-21"></a>Amélioration du message d’erreur de troncation, qui inclut les noms de tables et de colonnes, ainsi que la valeur tronquée (CTP 2.1)

Le message d’erreur ID 8152 `String or binary data would be truncated`, connu par de nombreux développeurs et administrateurs [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui développent ou gèrent des charges de travail de déplacement des données, est généré lors des transferts de données entre une source et une destination avec des schémas différents, si la source de données est trop grande pour tenir dans le type de données de destination. La résolution de ce problème peut prendre du temps. [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit un nouveau message d’erreur (2628), plus spécifique, dans ce scénario :  

`String or binary data would be truncated in table '%.*ls', column '%.*ls'. Truncated value: '%.*ls'.`

Le nouveau message d’erreur 2628 apporte davantage de contexte au problème de troncation de données, ce qui simplifie le processus de dépannage. Pour CTP 2.1, il s’agit d’un message d’erreur de type opt-in pour lequel [l’indicateur de trace](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 460 doit être activé.

### <a name="utf-8-support-ctp-21"></a>Prise en charge d’UTF-8 (CTP 2.1)

Il est maintenant possible de sélectionner par défaut le classement UTF-8 à l’installation de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

### <a name="improved-diagnostic-data-for-stats-blocking-ctp-21"></a>Amélioration des données de diagnostic pour le blocage des statistiques (CTP 2.1)

La préversion de SQL Server 2019 fournit des données de diagnostic améliorées pour les requêtes longues qui attendent des opérations de mise à jour synchrone des statistiques. La colonne `command` de la vue de gestion dynamique `sys.dm_exec_requests` indique `SELECT (STATMAN)` si une instruction `SELECT` attend la fin d’une opération de mise à jour synchrone des statistiques pour poursuivre l’exécution de la requête.  Par ailleurs, le nouveau type d’attente `WAIT_ON_SYNC_STATISTICS_REFRESH` est exposé dans la vue de gestion dynamique `sys.dm_os_wait_stats`. Il montre le temps, cumulé par instance, consacré aux opérations d’actualisation synchrone des statistiques.

### <a name="static-data-masking-ctp-21"></a>Masquage statique des données (CTP 2.1)

La préversion de SQL Server 2019 introduit le masquage statique des données. Vous pouvez l’utiliser pour nettoyer les données sensibles dans des copies de bases de données SQL Server. Le masquage statique des données permet de créer une copie expurgée de bases de données, dans laquelle toutes les informations sensibles ont été modifiées d’une manière qui rend la copie partageable avec des utilisateurs hors production. Il peut être utilisé à des fins de développement, de test, d’analyse et de rapports professionnels, de conformité, de dépannage et pour tout autre scénario dans lequel certaines données ne doivent pas être copiées dans différents environnements.

Le masquage statique des données fonctionne au niveau des colonnes. Sélectionnez les colonnes à masquer, puis, pour chaque colonne sélectionnée, spécifiez une fonction de masquage. Le masquage statique des données copie la base de données, puis applique les fonctions de masquage spécifiées aux colonnes.

#### <a name="static-data-masking-vs-dynamic-data-masking"></a>Comparaison entre le masquage statique des données et le masquage dynamique des données

Le masquage des données est le processus qui consiste à appliquer un masque sur une base de données pour masquer des informations sensibles et les remplacer par de nouvelles données ou des données nettoyées. Microsoft propose deux options de masquage : le masquage statique et le masquage dynamique des données. Le masquage dynamique des données a été introduit dans SQL Server 2017. Le tableau suivant compare ces deux solutions :

|Masquage statique des données |Masquage dynamique des données
|:----|:----
|Le masquage se produit sur une copie de la base de données <br/><br/>Les données d’origine ne sont pas récupérables<br/><br/>Le masque s’applique au niveau du stockage<br/><br/>Tous les utilisateurs ont accès aux mêmes données masquées<br/><br/>Destiné à un accès continu pour toute l’équipe|Le masquage se produit sur la base de données d'origine<br/><br/>Les données d'origine sont intactes<br/><br/>Le masque s’applique à la volée au moment de la requête<br/><br/>Le masque varie en fonction de l’autorisation de l’utilisateur <br/><br/>Destiné à un accès ponctuel pour un utilisateur donné

### <a name="database-compatibility-level-ctp-20"></a>Niveau de compatibilité de la base de données (CTP 2.0)

Le niveau de compatibilité **COMPATIBILITY_LEVEL 150** de base de données a été ajouté. Pour activer une base de données utilisateur spécifique, exécutez :

   ```sql
   ALTER DATABASE database_name SET COMPATIBILITY_LEVEL =  150;
   ```

### <a name="utf-8-support-ctp-20"></a>Prise en charge d’UTF-8 (CTP 2.0)

Prise en charge complète du codage de caractères UTF-8 courant en tant qu’encodage d’importation ou d’exportation ou que classement de données texte au niveau de la base de données ou des colonnes. UTF-8 est autorisé dans les types de données `CHAR` et `VARCHAR`, et est activé pendant la création du classement d’un objet ou sa modification en un classement avec le suffixe `UTF8`. 

Par exemple,`LATIN1_GENERAL_100_CI_AS_SC` en `LATIN1_GENERAL_100_CI_AS_SC_UTF8`. UTF-8 est uniquement disponible pour les classements Windows qui prennent en charge les caractères supplémentaires, comme introduit dans SQL Server 2012. `NCHAR` et `NVARCHAR` autorisent uniquement l’encodage UTF-16 et restent inchangés.

Cette fonctionnalité peut engendrer des économies de stockage importantes, selon le jeu de caractères utilisé. Par exemple, le fait de changer un type de données de colonne comportant des chaînes Latin de `NCHAR(10)` en `CHAR(10)` avec un classement compatible UTF-8 se traduit par une réduction de près de 50 % des besoins en stockage. En effet, `NCHAR(10)` nécessite 22 octets pour le stockage, tandis que `CHAR(10)` nécessite 12 octets pour la même chaîne Unicode.

### <a name="resumable-online-index-create-ctp-20"></a>Création d’index en ligne pouvant être reprise (CTP 2.0)

- La **création d’index en ligne pouvant être reprise** permet à une opération de création d’index de s’interrompre, puis de reprendre au niveau auquel elle avait été suspendue ou auquel elle avait échoué, au lieu de redémarrer à partir du début.

  La création d’index en ligne pouvant être reprise prend en charge les scénarios suivants :
  - Reprendre une opération de création d’index après l’échec d’une création d’index, comme après un basculement de base de données ou un manque d’espace disque.
  - Interrompre une opération de création d’index puis la reprendre, ce qui permet de libérer temporairement des ressources système en fonction des besoins avant de reprendre l’opération.
  - Créer de grands index sans utiliser d’espace journal conséquent ou de transaction à long terme qui bloque les autres activités de maintenance, tout en autorisant la troncation du journal.

  Sans cette fonctionnalité, si une opération de création d’index en ligne échoue, elle doit être réexécutée et redémarrée.

Avec cette version, nous étendons les fonctionnalités pouvant être reprises en ajoutant cette fonctionnalité à la [reconstruction d’index en ligne pouvant être reprise](https://azure.microsoft.com/blog/modernize-index-maintenance-with-resumable-online-index-rebuild/).

En outre, vous pouvez définir cette fonctionnalité comme fonctionnalité par défaut pour une base de données spécifique à l’aide du [paramétrage par défaut au niveau de la base de données pour les opérations DDL en ligne et pouvant être reprises](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

Pour plus d’informations, consultez [Création d’index en ligne pouvant être reprise](../t-sql/statements/create-index-transact-sql.md#resumable-indexes).

### <a name="build-and-rebuild-clustered-columnstore-indexes-online-ctp-20"></a>Génération et regénération d’index columnstore cluster en ligne (CTP 2.0)

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

### <a name="always-encrypted-with-secure-enclaves-ctp-20"></a>Always Encrypted avec enclaves sécurisées (CTP 2.0)

Always Encrypted est étendu avec un chiffrement sur place et des calculs avancés. En effet, il est désormais possible d’effectuer des calculs sur des données en texte clair, à l’intérieur d’une enclave sécurisée côté serveur.

Les opérations de chiffrement incluent le chiffrement des colonnes et la permutation des clés de chiffrement de colonne. Ces opérations peuvent maintenant être émises à l’aide de [!INCLUDE[tsql](../includes/tsql-md.md)] et ne nécessitent pas que les données soient déplacées hors de la base de données. Les enclaves sécurisées permettent d’utiliser Always Encrypted dans un ensemble plus vaste de scénarios qui satisfont aux deux exigences suivantes :  

- Les données sensibles doivent être protégées contre les utilisateurs dotés de privilèges élevés, mais néanmoins non autorisés, y compris les administrateurs de base de données, les administrateurs système, les opérateurs de cloud, ou contre les programmes malveillants.
- Les calculs avancés sur des données protégées doivent être pris en charge au sein du système de base de données.

Pour plus d’informations, consultez [Always Encrypted avec enclaves sécurisées](../relational-databases/security/encryption/always-encrypted-enclaves.md).

> [!NOTE]
> Always Encrypted avec enclaves sécurisés est uniquement disponible sur le système d’exploitation Windows.

### <a name="intelligent-query-processing-ctp-20"></a>Traitement de requêtes intelligent (CTP 2.0)

- La **rétroaction d’allocation de mémoire en mode ligne** étend la fonctionnalité de rétroaction d’allocation de mémoire introduite dans [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] en ajustant les tailles d’allocation de mémoire pour les opérateurs du mode batch et du mode ligne.  Dans le cas d’une allocation de mémoire excessive, si la mémoire allouée est plus de deux fois supérieure à la taille de la mémoire réelle utilisée, la rétroaction d’allocation de mémoire recalcule l’allocation de mémoire. Des exécutions consécutives demandent alors moins de mémoire. Pour une allocation de mémoire dont la taille est insuffisante et qui entraîne un dépassement de capacité sur le disque, la rétroaction d’allocation de mémoire déclenche un nouveau calcul de l’allocation de mémoire. Des exécutions consécutives demandent alors plus de mémoire. Cette fonctionnalité est activée par défaut sous le niveau de compatibilité de base de données 150.

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

- La **compilation différée de variable de table** améliore la qualité du plan et les performances globales pour les requêtes faisant référence à des variables de table. Pendant l’optimisation et la compilation initiale, cette fonctionnalité va propager les estimations de cardinalité basées sur le nombre réel de lignes de la variable de table.  Ces informations précises sur le nombre de lignes seront utilisées afin d’optimiser les opérations de plan en aval. Cette fonctionnalité est activée par défaut sous le niveau de compatibilité de base de données 150.

Pour utiliser les fonctionnalités de traitement de requête intelligent, définissez le niveau de compatibilité de base de données `COMPATIBILITY_LEVEL = 150`.

### <a id="programmability"></a> Extensions de programmabilité du langage Java (CTP 2.0)

- **Extension du langage Java (préversion)**  : utilisez l’extension du langage Java pour exécuter du code Java dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Dans [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], cette extension est installée quand vous ajoutez la fonctionnalité « Machine Learning Services (en base de données) » à votre instance SQL Server.

### <a id="sqlgraph"></a> fonctionnalités Graph SQL

- **Utilisation d’alias de tables dérivées ou de vues dans les requêtes de correspondance de graphe (CTP 2.1)** : les requêtes de graphe de la préversion de SQL Server 2019 prennent en charge les alias de tables dérivées et de vues dans la syntaxe `MATCH`. Les vues et les tables dérivées doivent être créées sur un jeu de tables de nœuds ou d’arêtes avec l’opérateur `UNION ALL` pour que les alias puissent être utilisés dans `MATCH`. Les tables de nœuds ou d’arêtes peuvent comporter des filtres, mais ce n’est pas obligatoire. La possibilité d’utiliser des alias de tables dérivées et de vues dans les requêtes `MATCH` peut se révéler très utile dans les scénarios où la requête porte sur des entités hétérogènes ou des connexions hétérogènes entre deux ou plusieurs entités du graphe.


- **Prise en charge des correspondances dans l’instruction DML `MERGE` (CTP 2.0)** : cette prise en charge permet de spécifier des relations de graphe en une seule instruction, plutôt qu’avec des instructions `INSERT`, `UPDATE` ou `DELETE` distinctes. Fusionnez vos données de graphe actuelles à partir des tables de nœuds ou d’arêtes avec de nouvelles données à l’aide des prédicats `MATCH` dans l’instruction `MERGE`. Cette fonctionnalité autorise les scénarios `UPSERT` sur les tables d’arêtes. Les utilisateurs peuvent désormais utiliser une instruction de fusion unique pour insérer une arête ou mettre à jour une arête entre deux nœuds.

- **Contraintes d’arête (CTP 2.0)** : elles sont introduites pour les tables d’arêtes dans Graph SQL. Les tables d’arêtes peuvent connecter n’importe quel nœud à n’importe quel autre nœud dans la base de données. Avec l’introduction des contraintes d’arête, vous pouvez maintenant appliquer certaines restrictions à ce comportement. La nouvelle contrainte `CONNECTION` permet de spécifier le type de nœuds auxquels une table d’arêtes donnée est autorisée à se connecter dans le schéma.

### <a name="database-scoped-default-setting-for-online-and-resumable-ddl-operations--ctp-20"></a>Paramétrage par défaut au niveau de la base de données pour les opérations DDL en ligne pouvant être reprises (CTP 2.0)

- Le **paramétrage par défaut au niveau de la base de données pour les opérations DDL en ligne et pouvant être reprises** permet un paramétrage de comportement par défaut pour les opérations d’index `ONLINE` et `RESUMABLE` au niveau de la base de données, plutôt que la définition de ces options pour chaque instruction DDL d’index telle que la création ou la regénération d’index.

- Définissez ces valeurs par défaut à l’aide des options de configuration de niveau base de données `ELEVATE_ONLINE` et `ELEVATE_RESUMABLE`. Les deux options forcent le moteur à élever automatiquement les opérations prises en charge à une exécution d’index en ligne ou pouvant être reprise. Vous pouvez activer les comportements suivants à l’aide de ces options :

  - L’option `FAIL_UNSUPPORTED` autorise toutes les opérations d’index en ligne ou pouvant être reprises et fait échouer les opérations d’index qui ne sont pas prises en charge dans le cadre d’une utilisation en ligne ou qui ne peuvent pas être reprises.
  - L’option `WHEN_SUPPPORTED` autorise les opérations prises en charge en ligne ou pouvant être reprises et exécute les opérations d’index non prises en charge hors connexion ou ne pouvant pas être reprises.
  - L’option `OFF` autorise le comportement actuel consistant à exécuter toutes les opérations d’index hors connexion et ne pouvant pas être reprises sauf spécification explicite dans l’instruction DDL.

Pour remplacer le paramétrage par défaut, incluez l’option ONLINE ou RESUMABLE dans les commandes de création ou de regénération d’index.  

Sans cette fonctionnalité, vous devez spécifier les options ONLINE et RESUMABLE directement dans l’instruction DDL telle que la création et la regénération d’index.

Pour plus d’informations sur les opérations d’index pouvant être reprises, consultez [Création d’index en ligne pouvant être reprise](https://azure.microsoft.com/blog/resumable-online-index-create-is-in-public-preview-for-azure-sql-db/).

### <a id="ha"></a>Groupes de disponibilité Always On : augmentation du nombre de réplicas synchrones (CTP 2.0)

- **Jusqu’à cinq réplicas synchrones** : dans [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], le nombre maximal de réplicas synchrones est de 5, contre 3 dans [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Vous pouvez configurer ce groupe de 5 réplicas de manière à instaurer le basculement automatique en son sein. Il y a 1 réplica principal et 4 réplicas secondaires synchrones.

- La **redirection de la connexion depuis un réplica secondaire vers le réplica principal** permet de rediriger les connexions d’applications clientes vers le réplica principal, quel que soit le serveur cible spécifié dans la chaîne de connexion. Cette fonctionnalité autorise la redirection d’une connexion sans écouteur. Utilisez la redirection de la connexion depuis un réplica secondaire vers le réplica principal dans les cas suivants :

  - La technologie cluster n’offre pas de fonctionnalité d’écouteur.
  - Configuration de sous-réseaux multiples où la redirection devient complexe.
  - Scénarios d’échelle lecture ou de reprise d’activité où le type de cluster est `NONE`.

Pour plus d’informations, consultez [Redirection de connexion en lecture/écriture depuis un réplica secondaire vers le réplica principal (groupes de disponibilité Always On)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md).

### <a name="data-discovery-and-classification-ctp-20"></a>Découverte et classification des données (CTP 2.0)

La découverte et la classification des données fournissent des fonctionnalités avancées qui sont intégrées de manière native à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La classification et l’étiquetage de vos données les plus sensibles offrent les avantages suivants :
- Elles aident à répondre aux standards de confidentialité des données et aux exigences de conformité réglementaires.
- Elles prennent en charge les scénarios de sécurité, tels que la supervision (audit) et l’alerte en cas d’accès anormal à des données sensibles.
- Elles facilitent l’identification des emplacements des données sensibles dans l’entreprise, afin que les administrateurs puissent prendre les bonnes mesures pour sécuriser la base de données.

Pour plus d’informations, consultez [Découverte et classification des données SQL](../relational-databases/security/sql-data-discovery-and-classification.md).

[L’audit](../relational-databases/security/auditing/sql-server-audit-database-engine.md) a également été amélioré pour inclure un nouveau champ dans le journal d’audit appelé `data_sensitivity_information`, qui journalise les classifications de sensibilité (étiquettes) des données réelles retournées par la requête. Pour plus d’informations et des exemples, consultez [ADD SENSITIVITY CLASSIFICATION](../t-sql/statements/add-sensitivity-classification-transact-sql.md).

>[!NOTE]
>La façon dont l’audit est activé n’a fait l’objet d’aucune modification. Un nouveau champ a été ajouté aux enregistrements, `data_sensitivity_information`, qui journalise les classifications de sensibilité (étiquettes) des données réelles retournées par la requête. Consultez [Audit de l’accès aux données sensibles](https://docs.microsoft.com/azure/sql-database/sql-database-data-discovery-and-classification#subheading-3).

### <a name="expanded-support-for-persistent-memory-devices-ctp-20"></a>Prise en charge étendue des appareils à mémoire persistante (CTP 2.0)

Tout fichier [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] placé sur un appareil de mémoire persistante peut maintenant fonctionner en mode *compatible*. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] accède directement à l’appareil, en contournant la pile de stockage du système d’exploitation à l’aide d’opérations memcpy efficace. Ce mode améliore les performances, car il permet une faible latence d’entrée/sortie par rapport à ces appareils.
    - Voici quelques exemples de fichiers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] concernés :
        - fichiers de la base de données ;
        - Fichiers journaux de transactions
        - Fichiers de point de contrôle OLTP en mémoire
    - La mémoire persistante est également appelée mémoire de classe de stockage.
    - La mémoire persistante est parfois appelée de manière informelle *pmem* sur certains sites web non-Microsoft.

> [!NOTE]
> Pour cette préversion, la mise en compatibilité des fichiers sur des appareils de mémoire persistante est uniquement disponible sur Linux. SQL Server sur Windows prend en charge les appareils de mémoire persistante à compter de SQL Server 2016.

### <a name="hybrid-buffer-pool-ctp-21"></a>Pool de mémoires tampons hybride (CTP 2.1)

Le pool de mémoires tampons hybride est une nouvelle fonctionnalité du Moteur de base de données SQL Server selon laquelle les pages de base de données qui se trouvent sur des fichiers de base de données placés sur un appareil à mémoire persistante (PMEM) sont directement accessibles si nécessaire. Compte tenu de la très faible latence des appareils PMEM pour l’accès aux données, le moteur peut renoncer à effectuer une copie des données dans une zone de « pages nettoyées » du pool de mémoires tampons pour simplement accéder directement à la page sur PMEM. L’accès est effectué à l’aide d’E/S mappées en mémoire, comme c’est le cas avec l’état d'éveil à la présence d'un environnement virtualisé. Il en résulte des avantages en matière de performances : sont évitées la copie de la page dans la mémoire DRAM ainsi que la pile d’E/S du système d’exploitation permettant d’accéder à la page sur un stockage persistant. Cette fonctionnalité est disponible sur SQL Server sur Windows et sur SQL Server sur Linux.

Pour plus d’informations, voir [Pool de mémoires tampons hybride](../database-engine/configure-windows/hybrid-buffer-pool.md).

### <a name="support-for-columnstore-statistics-in-dbcc-clonedatabase-ctp-20"></a>Prise en charge des statistiques columnstore dans DBCC CLONEDATABASE (CTP 2.0)

`DBCC CLONEDATABASE` crée une copie de schéma uniquement d’une base de données qui inclut tous les éléments nécessaires pour résoudre les problèmes de performances de requête sans copier les données.  Dans les versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la commande ne copiait pas les statistiques permettant de résoudre avec précision les problèmes des requêtes d’index columnstore, ce qui obligeait l’utilisateur à effectuer des étapes manuelles pour capturer ces informations. Maintenant, dans [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)], DBCC CLONEDATABASE capture automatiquement les objets blob de statistiques pour les index columnstore ; aucune étape manuelle n’est donc requise.

### <a name="new-options-added-to-spestimatedatacompressionsavings-ctp-20"></a>Ajout d’options à sp_estimate_data_compression_savings (CTP 2.0)

`sp_estimate_data_compression_savings` retourne la taille actuelle de l’objet demandé et estime la taille de l’objet pour l’état de compression demandé.  Cette procédure prend en charge trois options : `NONE`, `ROW` et `PAGE`. SQL Server 2019 introduit deux nouvelles options : `COLUMNSTORE` et `COLUMNSTORE_ARCHIVE`. Ces nouvelles options vous permettent d’estimer les économies d’espace si un index columnstore est créé sur la table à l’aide de la compression de columnstore standard ou d’archive.

### <a id="ml"></a> Clusters de basculement SQL Server Machine Learning Services et modélisation par partitions (CTP 2.0)

- **Modélisation basée sur les partitions** : traitez les scripts externes par partition des données en utilisant les nouveaux paramètres ajoutés à `sp_execute_external_script`. Cette fonctionnalité prend en charge l’entraînement de nombreux petits modèles (un modèle par partition de données) au lieu d’un grand modèle.

- **Cluster de basculement Windows Server** : configurez la haute disponibilité pour Machine Learning Services sur un cluster de basculement Windows Server.

Pour des informations détaillées, consultez [Nouveautés de SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

### <a name="lightweight-query-profiling-infrastructure-enabled-by-default-ctp-20"></a>Infrastructure légère de profilage de requêtes activée par défaut (CTP 2.0)

L’infrastructure du profilage de requête léger fournit les données de performances de requête plus efficacement que les technologies de profilage standard. Le profilage léger est maintenant activé par défaut. Il a été introduit dans [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1. Le profilage léger offre un mécanisme de collecte des statistiques d’exécution des requêtes avec une surcharge attendue de 2 % pour l’UC, par rapport à une surcharge pouvant atteindre 75 % pour l’UC dans le cadre du mécanisme de profilage de requête standard. Sur les versions précédentes, il était désactivé (OFF) par défaut. Les administrateurs de base de données peuvent l’activer avec [l’indicateur de trace 7412](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). 

Pour plus d’informations sur le profilage léger, consultez le billet de blog [Developers Choice: Query progress – anytime, anywhere](https://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/).

### <a id="polybase"></a>Nouveaux connecteurs PolyBase

- **Nouveaux connecteurs pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata et MongoDB** : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] introduit de nouveaux connecteurs aux données externes pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata et MongoDB.

### <a name="new-sysdmdbpageinfo-system-function-returns-page-information-ctp-20"></a>Nouvelle fonction système sys.dm_db_page_info retournant des informations sur une page (CTP 2.0)

`sys.dm_db_page_info(database_id, file_id, page_id, mode)` retourne des informations sur une page dans une base de données. La fonction retourne une ligne qui contient les informations d’en-tête de la page, notamment les `object_id`, `index_id` et `partition_id`. Cette fonction rend superflue l’utilisation de `DBCC PAGE` dans la plupart des cas.  

Afin de faciliter la résolution des problèmes d’attentes liées à une page, une nouvelle colonne nommée page_resource a également été ajoutée à `sys.dm_exec_requests` et `sys.sysprocesses`. Cette nouvelle colonne vous permet de joindre `sys.dm_db_page_info` à ces vues par le biais d’une autre nouvelle fonction : `sys.fn_PageResCracker`. En guise d’exemple, consultez le script suivant :

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d 
  CROSS APPLY sys.fn_PageResCracker(d.page_resource) AS r
  CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id,'DETAILED')
    AS page_info;
```

## <a id="sqllinux"></a> SQL Server sur Linux

### <a name="ctp-20"></a>CTP 2.0 

- **Prise en charge de la réplication** : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] prend en charge la réplication SQL Server sur Linux. Une machine virtuelle Linux avec l’Agent SQL peut être un serveur de publication, un serveur de distribution ou un abonné. 

  Créez les types de publications suivants :
  - Transactionnelle
  - Snapshot
  - Fusion

  Configurez la réplication avec [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou utilisez des [procédures stockées de réplication](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

- **Prise en charge de MSDTC (Microsoft Distributed Transaction Coordinator)**  : SQL Server 2019 sur Linux prend en charge MSDTC (Microsoft Distributed Transaction Coordinator). Pour plus d’informations, consultez [Guide pratique pour configurer MSDTC sur Linux](../linux/sql-server-linux-configure-msdtc.md).

- **Groupe de disponibilité Always On sur des conteneurs Docker avec Kubernetes** : Kubernetes peut orchestrer les conteneurs exécutant des instances [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour fournir un ensemble hautement disponible de bases de données avec des groupes de disponibilité SQL Server Always On. Un opérateur Kubernetes déploie une ressource StatefulSet incluant un **conteneur mssql-server** et un moniteur d’intégrité.

- **Prise en charge d’OpenLDAP pour les fournisseurs AD tiers**  : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] sur Linux prend en charge OpenLDAP, ce qui permet aux fournisseurs tiers de joindre Active Directory.

- **Machine learning sur Linux** : SQL Server 2019 Machine Learning Services (en base de données) est maintenant pris en charge sur Linux. La prise en charge inclut la procédure stockée `sp_execute_external_script`. Pour obtenir des instructions sur l’installation de Machine Learning Services sur Linux, consultez [Installer la prise en charge en R et Python de SQL Server 2019 Machine Learning Services sur Linux](../linux/sql-server-linux-setup-machine-learning.md).

- **Nouveau registre de conteneurs** : toutes les images conteneur pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ainsi que pour [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] se trouvent désormais dans le Registre de conteneurs Microsoft. Le Registre de conteneurs Microsoft est le registre de conteneurs officiel pour la distribution de conteneurs de produits Microsoft. De plus, des images basées sur RHEL certifiées sont maintenant publiées.

  - Registre de conteneurs Microsoft : `mcr.microsoft.com/mssql/server:vNext-CTP2.0`
  - Images conteneur basées sur RHEL certifiées : `mcr.microsoft.com/mssql/rhel/server:vNext-CTP2.0`

## <a id="mds"></a>Master Data Services (CTP 2.0) 

- **Contrôles Silverlight remplacés par des contrôles HTML** : le portail Master Data Services (MDS) ne dépend plus de Silverlight. Tous les anciens composants Silverlight ont été remplacés par des contrôles HTML.

## <a id="security"></a>Sécurité (CTP 2.0)

- **Gestion des certificats dans le Gestionnaire de configuration SQL Server** : les certificats SSL/TLS sont couramment utilisés pour sécuriser l’accès aux instances SQL Server. La gestion des certificats est maintenant intégrée au Gestionnaire de configuration SQL Server, ce qui simplifie les tâches courantes telles que les suivantes :

  - Affichage et validation des certificats installés dans une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 
  - Affichage des certificats arrivant à expiration.
  - Déploiement de certificats sur plusieurs machines participant à des groupes de disponibilité Always On (à partir du nœud contenant le réplica principal).
  - Déploiement de certificats sur plusieurs machines participant à une instance de cluster de basculement (à partir du nœud actif).

  > [!NOTE]
  > L’utilisateur doit disposer des autorisations d’administrateur sur tous les nœuds de cluster.

## <a id="tools"></a>Outils

- [**Azure Data Studio**](../azure-data-studio/what-is.md) : précédemment publié sous le nom de préversion SQL Operations Studio, Azure Data Studio est un outil de bureau léger, moderne, open source et multiplateforme pour la réalisation de tâches courantes liées au développement et à l’administration de données. Avec Azure Data Studio, vous pouvez vous connecter à SQL Server en local et dans le cloud sur Windows, macOS et Linux. Azure Data Studio vous permet d’effectuer les opérations suivantes :

  - Faire une mise à jour vers [l’extension SQL Server 2019 (préversion)](../azure-data-studio/sql-server-2019-extension.md). (CTP 2.1)
  - Modifier et exécuter des requêtes dans un environnement de développement moderne avec intégration rapide de contrôles de code source, d’extraits de code et d’Intellisense. (CTP 2.0) 
  - Visualiser rapidement les données grâce à l’intégration de graphiques à vos jeux de résultats. (CTP 2.0)
  - Créer des tableaux de bord personnalisés pour vos serveurs et bases de données à l’aide de widgets personnalisables. (CTP 2.0)  
  - Gérer facilement votre environnement élargi avec le terminal intégré. (CTP 2.0)
  - Analyser les données par le biais d’une expérience de bloc-notes intégrée basée sur Jupyter. (CTP 2.0)
  - Améliorer votre expérience des thèmes et extensions personnalisés. (CTP 2.0)
  - Explorer vos ressources Azure avec un explorateur de ressources et d’abonnements intégré. (CTP 2.0)
  - Prendre en charge des scénarios utilisant un cluster Big Data SQL Server (CTP 2.0)

- [**SQL Server Management Studio (SSMS) 18.0 (préversion)**](../ssms/sql-server-management-studio-ssms.md)

  - Prise en charge de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. (CTP 2.0)
  - Prise en charge d’Always Encrypted avec enclaves sécurisées. (CTP 2.0)
  - Taille de téléchargement inférieure. (CTP 2.0)
  - Désormais basé sur l’interpréteur de commandes isolé Visual Studio 2017. (CTP 2.0)
  - Pour obtenir la liste complète, voir le [journal des modifications de SSMS](../ssms/sql-server-management-studio-changelog-ssms.md). (CTP 2.0)

## <a name="other-services"></a>Autres services

À partir de CTP 2.1, [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] n’introduit pas de nouvelles fonctionnalités pour les services suivants :

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services (SSAS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS)

## <a name="next-steps"></a>Étapes suivantes

- [Notes de publication de SQL Server 2019](sql-server-ver15-release-notes.md)

- [Microsoft SQL Server 2019 : Livre blanc technique](https://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Publié en septembre 2018. S’applique à Microsoft SQL Server 2019 CTP 2.0 pour conteneurs Docker, Linux et Windows.


[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
