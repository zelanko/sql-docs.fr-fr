---
title: Nouveautés
description: Découvrez les nouveautés de Microsoft Analytics Platform System, un appareil de mise à l’échelle sur place qui héberge l’entrepôt de données parallèles MPP SQL Server.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: faf3bd1f487fb5c850759fdde3ddecd32bdd3b1f
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625538"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Quoi de neuf dans Analytics Platform System, un entrepôt de données MPP à grande échelle
Découvrez les nouveautés des dernières mises à jour d’appareils pour Microsoft Analytics Platform System (APS). APS est un appareil de mise à l’échelle sur place qui héberge L’entrepôt de données parallèles MPP SQL Server. 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"
<a name="h2-aps-cu7.6"></a>
## <a name="aps-cu76"></a>APS CU7.6
Date de sortie - Avril 2020

### <a name="rename-column"></a>Renommer une colonne
Après la mise à niveau vers CU7.6, les clients pourront renommer une colonne d’une table créée par l’utilisateur. Voir [RENAME (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/rename-transact-sql) pour la syntaxe, des exemples, des limitations et plus d’informations.

### <a name="alter-view"></a>Afficher alter
Les clients pourront désormais modifier les vues. Voir [ALTER VIEW (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-view-transact-sql) pour plus d’informations.

<a name="h2-aps-cu7.5"></a>
## <a name="aps-cu75"></a>APS CU7.5
Date de sortie - Septembre 2019

### <a name="alter-external-data-source"></a>Modifier la source de données externes
Les clients seront en mesure de modifier la définition externe de source de données avec la mise à jour CU7.5. Les clients avec le nœud de nom Hadoop haute disponibilité peuvent maintenant modifier la source de données pour changer les arguments quand une défaillance se produit. Pour APS, seul le LOCATION, RESOURCE_MANAGER_LOCATION et CREDENTIAL peuvent être modifiés. Voir [modifier la source de données externes](https://docs.microsoft.com/sql/t-sql/statements/alter-external-data-source-transact-sql?view=sql-server-2017) pour plus d’informations.

### <a name="cdh-515-and-516-support-with-polybase"></a>CDH 5.15 et 5.16 support avec PolyBase
PolyBase sur APS avec la mise à jour CU7.5 prend désormais en charge les versions CDH 5.15 et 5.16 de la distribution Hadoop de Cloudera. Utilisez l’option 6 pour les versions CDH 5.x. 

### <a name="try_convert-and-try_cast-support"></a>soutien Try_Convert et Try_Cast
CU7.5 APS prend désormais en charge les fonctions [TRY_CAST](https://docs.microsoft.com/sql/t-sql/functions/try-cast-transact-sql?view=sql-server-2017) et [TRY_CONVERT](https://docs.microsoft.com/sql/t-sql/functions/try-convert-transact-sql?view=sql-server-2017) tsql. Ces deux fonctions renvoient une valeur convertie au type de données spécifié si le converti réussit; autrement, les retours nuls.

<a name="h2-aps-cu7.4"></a>
## <a name="aps-cu74"></a>APS CU7.4
Date de sortie - mai 2019

### <a name="loading-large-rows-with-dwloader"></a>Chargement de grandes rangées avec chargeur
À partir d’APS CU7.4, les clients pourront utiliser un nouveau chargeur pour charger des rangées dans des tables supérieures à 32 KB (32 768 octets). Le nouveau chargeur prend en charge l’interrupteur -l qui prend une valeur d’intégrateur entre 32768 et 33554432 (dans les octets) pour charger des rangées supérieures à 32 KB. Utilisez cette option uniquement lors du chargement de grandes rangées (plus de 32 KB) car ce commutateur allouera plus de mémoire sur le client et le serveur et peut ralentir les charges. Vous pouvez télécharger le nouveau chargeur à partir du site de [téléchargement](https://www.microsoft.com/download/details.aspx?id=57472).  

### <a name="hdp-30-and-31-support-with-polybase"></a>HDP 3.0 et 3.1 support avec PolyBase
PolyBase sur APS prend désormais en charge HDP 3.0 et 3.1 avec cette mise à jour. Utilisez l’option 7 pour les versions HDP 3.x. Pour plus d’informations, consultez la page [de connectivité PolyBase.](https://docs.microsoft.com/sql/database-engine/configure-windows/polybase-connectivity-configuration-transact-sql)

### <a name="utf16-file-support-with-polybase"></a>Prise en charge de fichiers UTF16 avec PolyBase
PolyBase supporte désormais la lecture de fichiers texte délimités qui sont dans l’encodage UTF16 (LE). Voir [créer un format de fichier externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-file-format-transact-sql) pour les détails de configuration. 

<a name="h2-aps-cu7.3"></a>
## <a name="aps-cu73"></a>APS CU7.3
Date de sortie - Décembre 2018

### <a name="common-subexpression-elimination"></a>Élimination des sous-expressions communes
APS CU7.3 améliore les performances de requête avec l’élimination commune de sous-expression dans l’optimiseur de requête SQL. L’amélioration améliore les requêtes de deux façons. Le premier avantage est la capacité d’identifier et d’éliminer de telles expressions aider à réduire le temps de compilation SQL. Le deuxième avantage et le plus important est que les opérations de mouvement de données pour ces sous-exprès redondantes sont éliminées, de ce qui permet aux requêtes de devenir plus rapides. Explication détaillée de cette fonctionnalité peut être trouvée [ici](common-sub-expression-elimination.md).

### <a name="aps-informatica-connector-for-informatica-1020-published"></a>APS Informatica connecteur pour Informatica 10.2.0 publié
Nous avons publié une nouvelle version des connecteurs Informatica pour APS qui fonctionne avec la version Informatica 10.2.0 et 10.2.0 Hotfix 1. Les nouveaux connecteurs peuvent être téléchargés à partir du site de [téléchargement](https://www.microsoft.com/download/details.aspx?id=57472).

#### <a name="supported-versions"></a>Versions prises en charge

| APS Version | Informatica PowerCenter | Pilote |
|:---|:---|:---|
| APS 2016 | 9.6.1 | SQL Server Client autochtone 11.x |
| APS 2016 et plus tard | 10.2.0, 10.2.0 Hotfix 1 | SQL Server Client autochtone 11.x |

<a name="h2-aps-cu7.2"></a>
## <a name="aps-cu72"></a>APS CU7.2
Date de sortie - Octobre 2018

### <a name="support-for-tls-12"></a>Prise en charge de TLS 1.2
APS CU7.2 prend en charge TLS 1.2. La machine cliente à APS et APS intra-nœuds de communication peut maintenant être réglée pour communiquer seulement sur TLS1.2. Des outils comme SSDT, SSIS et Dwloader installés sur des machines client qui sont configurées pour communiquer uniquement sur TLS 1.2 peuvent désormais se connecter à APS à l’aide de TLS 1.2. Par défaut, APS prendra en charge toutes les versions TLS (1.0, 1.1 et 1.2) pour la compatibilité vers l’arrière. Si vous souhaitez configurer votre appareil APS pour utiliser strictement TLS 1.2, vous pouvez le faire en changeant les paramètres du registre. 

Pour plus d’informations, voir [configurer TLS1.2 sur APS](configure-tls12-aps.md).

### <a name="hadoop-encryption-zone-support-for-polybase"></a>Soutien de zone de chiffrement Hadoop pour PolyBase
PolyBase peut désormais communiquer avec les zones de cryptage Hadoop. Voir les modifications de configuration APS qui sont nécessaires dans [la configuration de la sécurité Hadoop](polybase-configure-hadoop-security.md#encryptionzone).

### <a name="insert-select-maxdop-options"></a>Options maxdop Insert-Select
Nous avons ajouté un [commutateur de fonctionnalité](appliance-feature-switch.md) qui vous permet de sélectionner des paramètres maxdop supérieurs à 1 pour les opérations d’insertion. Vous pouvez maintenant définir le réglage maxdop à 0, 1, 2 ou 4. La valeur par défaut est 1.

> [!IMPORTANT]  
> L’augmentation du maxdop peut parfois entraîner des opérations plus lentes ou des erreurs d’impasse. Si cela se produit, changez le réglage en maxdop 1 et réessayez l’opération.

### <a name="columnstore-index-health-dmv"></a>ColumnStore indice santé DMV
Vous pouvez afficher les informations sur la santé de l’indice de magasin de colonnes à **l’aide de dm_pdw_nodes_db_column_store_row_group_physical_stats** dmv. Utilisez la vue suivante pour déterminer la fragmentation et décider quand reconstruire ou réorganiser un indice de magasin de colonnes.

```sql
create view dbo.vCS_rg_physical_stats
as 
with cte
as
(
select   tb.[name]                    AS [logical_table_name]
,        rg.[row_group_id]            AS [row_group_id]
,        rg.[state]                   AS [state]
,        rg.[state_desc]              AS [state_desc]
,        rg.[total_rows]              AS [total_rows]
,        rg.[trim_reason_desc]        AS trim_reason_desc
,        mp.[physical_name]           AS physical_name
FROM    sys.[schemas] sm
JOIN    sys.[tables] tb               ON  sm.[schema_id]          = tb.[schema_id]                             
JOIN    sys.[pdw_table_mappings] mp   ON  tb.[object_id]          = mp.[object_id]
JOIN    sys.[pdw_nodes_tables] nt     ON  nt.[name]               = mp.[physical_name]
JOIN    sys.[dm_pdw_nodes_db_column_store_row_group_physical_stats] rg      ON  rg.[object_id]     = nt.[object_id]
                                                                            AND rg.[pdw_node_id]   = nt.[pdw_node_id]
                                        AND rg.[pdw_node_id]    = nt.[pdw_node_id]                                          
)
select *
from cte;
```

### <a name="polybase-date-range-increase-for-orc-and-parquet-files"></a>Augmentation de la plage de dates PolyBase pour les fichiers ORC et Parquet
La lecture, l’importation et l’exportation de types de données de date à l’aide de PolyBase prend maintenant en charge les dates avant 1970-01-01 et après 2038-01-20 pour les types de fichiers ORC et Parquet.

### <a name="ssis-destination-adapter-for-sql-server-2017-as-target"></a>Adaptateur de destination SSIS pour SQL Server 2017 comme cible
Nouvel adaptateur de destination APS SSIS qui prend en charge SQL Server 2017 comme cible de déploiement peut être téléchargé à partir du site de [téléchargement](https://www.microsoft.com/download/details.aspx?id=57472).

<a name="h2-aps-cu7.1"></a>
## <a name="aps-cu71"></a>APS CU7.1
Date de sortie - Juillet 2018

### <a name="dbcc-commands-do-not-consume-concurrency-slots-behavior-change"></a>Les commandes DBCC ne consomment pas de fentes de concurrence (changement de comportement)
APS prend en charge un sous-ensemble des commandes T-SQL [DBCC](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-transact-sql) telles que [DBCC DROPCLEANBUFFERS](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql). Auparavant, ces commandes consommaient un [emplacement d’accès concurrentiel](https://docs.microsoft.com/sql/analytics-platform-system/workload-management?view=aps-pdw-2016-au7#concurrency-slots), réduisant ainsi le nombre de chargements/requêtes utilisateur qui pouvaient être exécutés. Les `DBCC` commandes sont maintenant exécutées dans une file d’attente locale qui ne consomment pas une fente de concurrence utilisateur améliorant les performances globales d’exécution de requête.

### <a name="replaces-some-metadata-calls-with-catalog-objects"></a>Remplace certains appels de métadonnées par des objets de catalogue
L’utilisation d’objets de catalogue pour les appels de métadonnées au lieu d’utiliser SMO a montré une amélioration des performances d’APS. À partir de CU7.1, certains de ces appels de métadonnées utilisent maintenant des objets de catalogue par défaut. Ce comportement peut être désactivé par [commutateur de fonctionnalité](appliance-feature-switch.md) si les clients utilisant des requêtes de métadonnées rencontrent des problèmes.

### <a name="bug-fixes"></a>Résolution des bogues
Nous avons mis à niveau vers SQL Server 2016 SP2 CU2 avec APS CU7.1. La mise à niveau corrige certains problèmes décrits ci-dessous.

| Intitulé | Description |
|:---|:---|
| **Impasse potentielle tuple mover** |La mise à niveau corrige une possibilité de longue date d’impasse dans une transaction distribuée et le fil d’arrière-plan de tuple mover. Après l’installation de CU7.1, les clients qui ont utilisé TF634 pour arrêter le déménageur de tuple comme paramètre de démarrage SQL Server ou drapeau à trace globale peuvent l’enlever en toute sécurité. | 
| **Certaines requêtes en retard/plomb échouent** |Certaines requêtes sur les tables de l’ICC avec des fonctions de décalage/plomb imbriquées qui seraient erronées sont maintenant corrigées avec cette mise à niveau. | 


<a name="h2-aps-au7"></a>
## <a name="aps-au7"></a>APS AU7
Date de sortie - mai 2018

APS 2016 est une condition préalable à la mise à niveau vers AU7. Voici de nouvelles fonctionnalités dans APS AU7 :

### <a name="auto-create-and-auto-update-statistics"></a>Statistiques de création automatique et de mise à jour automatique
APS AU7 crée et met à jour automatiquement les statistiques, par défaut. Pour mettre à jour les paramètres statistiques, les administrateurs peuvent utiliser un nouvel élément de menu de commutation de fonctionnalités dans le [gestionnaire de configuration](appliance-configuration.md#CMTasks). Le [commutateur de fonctionnalité](appliance-feature-switch.md) contrôle le comportement de mise à jour automatique, auto-mise à jour et asynchrone des statistiques. Vous pouvez également mettre à jour les paramètres statistiques avec l’instruction [ALTER DATABASE (Parallel Data Warehouse).](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)

### <a name="t-sql"></a>T-SQL
Select @var est maintenant pris en charge. Pour plus d’informations, voir [sélectionner la variable locale](/sql/t-sql/language-elements/select-local-variable-transact-sql) 

Les indices de requête hassH et ORDER GROUP sont maintenant pris en charge. Pour plus d’informations, voir [Conseils (Transact-SQL) - Requête](/sql/t-sql/queries/hints-transact-sql-query)

### <a name="feature-switch"></a>Commutateur de fonctionnalité
APS AU7 introduit Feature Switch in [Configuration Manager](launch-the-configuration-manager.md). AutoStatsEnabled et DmsProcessStopMessageTimeoutInSeconds sont maintenant des options configurables qui peuvent être modifiées par les administrateurs.

### <a name="known-issues"></a>Problèmes connus
Avec le logiciel APS AU7, une mise à jour Intel BIOS est fournie qui résout un problème décrit comme *des attaques de canal latéral d’exécution spéculative*. Les attaques visent à exploiter ce qu’on appelle *les vulnérabilités Spectre et Meltdown*. Bien qu’emballée avec APS, la mise à jour BIOS est installée manuellement, et non dans le cadre de l’installation du logiciel APS AU7.

Microsoft conseille à tous les clients d’installer le BIOS mis à jour. Microsoft a mesuré l’effet de Kernel Virtual Address Shadowing (KVAS), Kernel Page Table Indirection (KPTI) et Indirect Branch Prediction mitigation (IBP) sur diverses charges de travail SQL dans divers environnements. Les mesures ont révélé une dégradation importante de certaines charges de travail. Sur la base des résultats, la recommandation est que vous testiez l’effet de performance d’activation de la mise à jour BIOS avant de les déployer dans un environnement de production. Voir les conseils SQL Server [ici](https://support.microsoft.com/help/4073225/guidance-protect-sql-server-against-spectre-meltdown).

::: moniker-end
::: moniker range=">= aps-pdw-2016 || = sqlallproducts-allversions"
<a name="h2-aps-au6"></a>
## <a name="aps-2016"></a>APS 2016
Cette section décrit les nouvelles fonctionnalités de l’APS 2016-AU6.

### <a name="sql-server-2016"></a>SQL Server 2016

APS AU6 fonctionne sur la dernière version SQL Server 2016, et utilise le niveau de compatibilité de base de données par défaut 130. SQL Server 2016 permet de prendre en charge de nouvelles fonctionnalités telles que :

- Indices secondaires pour les indices groupés de magasin de colonnes.
- Kerberos pour PolyBase.

### <a name="t-sql"></a>T-SQL
APS AU6 prend en charge ces améliorations de compatibilité T-SQL.  Ces éléments linguistiques supplémentaires facilitent la migration à partir de SQL Server et d’autres sources de données. 

- [Les collations SQL au niveau des colonnes][] sont désormais prises en charge, en plus des collations Windows.
- [Les index non isolés des indices groupés des magasins][] de colonnes améliorent les performances des requêtes qui recherchent des valeurs spécifiques dans l’indice clustered columnstore. 
- [Sélectionnez... Dans][] 
- [sp_spaceused)affiche l’espace][] disque utilisé ou réservé dans une table ou une base de données.
- Le support [des tables larges][] est le même que SQL Server 2016. La limite précédente de 32 K pour la taille de la ligne n’existe plus. 

**Types de données**

- [VARCHAR(MAX)][], [NVARCHAR (MAX)][] et [VARBINARY (MAX)][]. Ces types de données LOB ont une taille maximale de 2 Go. Pour charger ces objets utiliser [bcp Utility][]. PolyBase et dwloader ne prennent actuellement pas en charge ces types de données. 
- [SYSNAME][]
- [Uniqueidentifier][]
- [Types de][] données NUMERIC et DECIMAL.

**Fonctions Windows**

- [ROWS ou RANGE][] dans la clause OVER de la déclaration SELECT.
- [FIRST_VALUE][]
- [LAST_VALUE][]
- [CUME_DIST][]
- [PERCENT_RANK][]

**Fonctions de sécurité**

- [CHECKSUM()][] et [BINARY_CHECKSUM()][]
- [HAS_PERMS_BY_NAME()][]

**Fonctions supplémentaires**

- [NEWID()][]
- [RAND()][]

### <a name="polybasehadoop-enhancements"></a>Améliorations PolyBase/Hadoop

- Compatibilité avec Hortonworks HDP 2.4 et HDP 2.5
- Soutien Kerberos via des informations d’identification étendues de base de données
- Support d’identification avec Azure Storage Blobs

### <a name="install-and-upgrade-enhancements"></a>Installer et mettre à niveau des améliorations

**Mises à jour de l’architecture d’entreprise** La mise à niveau de votre appareil existant vers APS AU6 installe les dernières mises à jour du firmware et du pilote, qui comprennent des correctifs de sécurité. 

Un nouvel appareil de HPE ou DELL inclut toutes les dernières mises à jour plus :

- Soutien processeur de dernière génération (Broadwell)
- Mise à jour sur les DIMM DDR4
- Débit DIMM amélioré

**Intégration**

- Le support entièrement qualifié de nom de domaine (FQDN) permet de configurer une fiducie de domaine à l’appareil. 
- Pour utiliser FQDN, vous devez effectuer une mise à niveau complète et vous y mettre au service pendant la mise à niveau. 

**Réduction des temps d’arrêt** L’installation ou la mise à niveau vers APS AU6 est plus rapide et nécessite moins de temps d’arrêt que les versions précédentes. Pour réduire les temps d’arrêt, l’installation ou la mise à niveau : 

 - Simplifie l’application des mises à jour WSUS en utilisant une image qui contient toutes les mises à jour jusqu’en juin 2016
 - Applique les mises à jour de sécurité avec les mises à jour du conducteur et du firmware
 - Place les derniers hotfixes et l’utilitaire de vérification de l’appareil (PAV) sur votre appareil afin qu’ils soient prêts à installer sans avoir besoin de les télécharger.

::: moniker-end

<!--
Link references to other articles in this same GitHub repo.

The link format that starts with '/sql/what-ever/my-artlcle' is not appropriate for common links within the same repo (as most of these link are).  The first couple links have been edited to show the proper syntax, but all other links in this article need to be similarly edited.
The proper formats have at least two big advantages.  One big advantage is that the proper formats enable the OPS Build system to detect broken links at Pull Request build time, instead of only later during run time.
-->
[database compatibility level 130]: ../t-sql/statements/alter-database-transact-sql-compatibility-level.md
[Collations SQL au niveau des colonnes]: ~/relational-databases/collations/collation-and-unicode-support.md

[Index non isolés sur les indices groupés de magasin de colonnes]:/sql/t-sql/statements/create-index-transact-sql
[VARCHAR(MAX)]:/sql/t-sql/data-types/char-and-varchar-transact-sql
[NVARCHAR(MAX)]:/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql
[VARBINARY (MAX)]:/sql/t-sql/data-types/binary-and-varbinary-transact-sql
[SYSNAME]:/sql/relational-databases/system-catalog-views/sys-types-transact-sql
[Sélectionnez... Dans]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[Tables larges]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[Utilitaire bcp]:/sql/tools/bcp-utility
[Uniqueidentifier]:/sql/t-sql/data-types/uniqueidentifier-transact-sql
[Numérique]:/sql/t-sql/data-types/decimal-and-numeric-transact-sql
[ROWS ou RANGE]:/sql/t-sql/queries/select-over-clause-transact-sql
[FIRST_VALUE]:/sql/t-sql/functions/first-value-transact-sql
[LAST_VALUE]:/sql/t-sql/functions/last-value-transact-sql
[CUME_DIST]:/sql/t-sql/functions/cume-dist-transact-sql
[PERCENT_RANK]:/sql/t-sql/functions/percent-rank-transact-sql
[CHECKSUM()]:/sql/t-sql/functions/checksum-transact-sql
[BINARY_CHECKSUM()]:/sql/t-sql/functions/binary-checksum-transact-sql
[HAS_PERMS_BY_NAME()]:/sql/t-sql/functions/has-perms-by-name-transact-sql
[NEWID()]:/sql/t-sql/functions/newid-transact-sql
[RAND()]:/sql/t-sql/functions/rand-transact-sql


  

  


