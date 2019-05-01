---
title: Quelles sont les nouveautés d’Analytique Platform System - un entrepôt de données de la montée en puissance
description: Voir quelles sont les nouveautés dans Microsoft Analytique Platform System, une appliance de montée en puissance en local qui héberge MPP SQL Server Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: cc64fdd430e64f7ad1b152234c2a203f453745c8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63243777"
---
# <a name="whats-new-in-analytics-platform-system-a-scale-out-mpp-data-warehouse"></a>Quelles sont les nouveautés d’Analytique Platform System, un entrepôt de données MPP montée en puissance
Consultez les nouveautés introduite dans les dernières mises à jour de matériel pour Microsoft Analytique Platform System (APS). APS est une appliance de montée en puissance en local qui héberge MPP SQL Server Parallel Data Warehouse. 

::: moniker range=">= aps-pdw-2016-au7 || = sqlallproducts-allversions"
<a name="h2-aps-cu7.3"></a>
## <a name="aps-cu73"></a>APS CU7.3
Date de publication - décembre 2018

### <a name="common-subexpression-elimination"></a>Élimination des sous-expressions communes
APS CU7.3 améliore les performances de requête avec élimination de sous-expressions communes dans l’optimiseur de requête SQL. L’amélioration améliore les requêtes de deux manières. Le premier, c’est la capacité à identifier et éliminer ces expressions permettent de réduire le temps de compilation SQL. L’avantage de la deuxième et le plus important est les opérations de déplacement de données pour ces sous-expressions redondantes sont éliminées ainsi les temps d’exécution de requêtes devient plus rapide. Vous pouvez trouver une explication détaillée de cette fonctionnalité [ici](common-sub-expression-elimination.md).

### <a name="aps-informatica-connector-for-informatica-1020-published"></a>Connecteur APS Informatica pour Informatica 10.2.0 publié
Nous avons publié une nouvelle version des connecteurs d’Informatica pour les points d’accès qui fonctionne avec Informatica version 10.2.0 et 10.2.0 1 de correctif logiciel. Les nouveaux connecteurs peuvent être téléchargées à partir de [site de téléchargement](https://www.microsoft.com/download/details.aspx?id=57472).

#### <a name="supported-versions"></a>Versions prises en charge

| Version de points d’accès | Informatica PowerCenter | Pilote |
|:---|:---|:---|
| APS 2016 | 9.6.1 | SQL Server Native Client 11.x |
| APS 2016 et versions ultérieures | 10.2.0, 10.2.0 correctif 1 | SQL Server Native Client 11.x |

<a name="h2-aps-cu7.2"></a>
## <a name="aps-cu72"></a>APS CU7.2
Date de publication : octobre 2018

### <a name="support-for-tls-12"></a>Prise en charge de TLS 1.2
APS CU7.2 prend en charge TLS 1.2. Ordinateur client pour les points d’accès et des points d’accès des communications intra-nœud peuvent désormais être définie pour communiquer uniquement via TLS 1.2. Outils tels que SSDT, SSIS et Dwloader installé sur les ordinateurs clients qui sont configurés pour communiquer uniquement via TLS 1.2 peuvent maintenant vous connecter aux points d’accès à l’aide de TLS 1.2. Par défaut, les points d’accès prendra en charge toutes les versions TLS (1.0, 1.1 et 1.2) pour la compatibilité descendante. Si vous souhaitez définir votre appliance APS strictement utiliser TLS 1.2, vous pouvez le faire en modifiant les paramètres du Registre. 

Pour plus d’informations, consultez [configuration TLS 1.2 sur APS](configure-tls12-aps.md).

### <a name="hadoop-encryption-zone-support-for-polybase"></a>Zone de chiffrement Hadoop prise en charge de PolyBase
PolyBase peut désormais communiquer aux zones de chiffrement Hadoop. Consultez les modifications de configuration de points d’accès qui sont nécessaires dans [configurer la sécurité de Hadoop](polybase-configure-hadoop-security.md#encryptionzone).

### <a name="insert-select-maxdop-options"></a>Options de maxdop de Insert-Select
Nous avons ajouté un [commutateur de fonctionnalité](appliance-feature-switch.md) qui vous permet de choisir les paramètres maxdop supérieures à 1 pour les opérations insert-select. Vous pouvez maintenant définir le paramètre maxdop à 0, 1, 2 ou 4. La valeur par défaut est 1.

> [!IMPORTANT]  
> Augmenter maxdop peut parfois entraîner des opérations plus lentes ou des erreurs de blocage. Si cela se produit, redéfinissez le paramètres maxdop 1 et recommencez l’opération.

### <a name="columnstore-index-health-dmv"></a>Intégrité de l’index ColumnStore DMV
Vous pouvez afficher des informations d’à l’aide d’intégrité columnstore index **dm_pdw_nodes_db_column_store_row_group_physical_stats** dmv. Utiliser l’affichage suivant pour déterminer la fragmentation et de décider du moment reconstruire ou réorganiser un index columnstore.

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

### <a name="polybase-date-range-increase-for-orc-and-parquet-files"></a>Augmentation de la plage date PolyBase pour les fichiers ORC et Parquet
Lecture, l’importation et exportation des types de données de date à l’aide de PolyBase maintenant prend en charge les dates avant 1970-01-01 et après 2038-01-20 pour les types de fichier ORC et Parquet.

### <a name="ssis-destination-adapter-for-sql-server-2017-as-target"></a>Adaptateur de destination SSIS pour SQL Server 2017 en tant que cible
Nouvel adaptateur de destination APS SSIS qui prend en charge de SQL Server 2017 comme cible de déploiement peut être téléchargé à partir de [site de téléchargement](https://www.microsoft.com/download/details.aspx?id=57472).

<a name="h2-aps-cu7.1"></a>
## <a name="aps-cu71"></a>APS CU7.1
Date de publication - juillet 2018

### <a name="dbcc-commands-do-not-consume-concurrency-slots-behavior-change"></a>Les commandes DBCC ne consomment pas d’emplacements de concurrence (modification du comportement)
Points d’accès prend en charge un sous-ensemble de T-SQL [commandes DBCC](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-transact-sql) comme [DBCC DROPCLEANBUFFERS](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-dropcleanbuffers-transact-sql). Auparavant, ces commandes monopolise un [emplacement de concurrence](https://docs.microsoft.com/sql/analytics-platform-system/workload-management?view=aps-pdw-2016-au7#concurrency-slots) réduisant le nombre de chargements/requêtes utilisateur qui a pu être exécutée. Le `DBCC` commandes sont désormais exécutés dans une file d’attente local qui n’utilisent pas un emplacement de concurrence utilisateur amélioration des performances de l’exécution de requête globale.

### <a name="replaces-some-metadata-calls-with-catalog-objects"></a>Remplace certains appels de métadonnées avec les objets de catalogue
À l’aide des objets de catalogue pour les appels de métadonnées au lieu d’utiliser SMO vous a montré amélioration des performances dans les points d’accès. À partir de CU7.1, certaines de ces appels de métadonnées maintenant utilisent les objets de catalogue par défaut. Ce comportement peut être désactivé en [commutateur de fonctionnalité](appliance-feature-switch.md) si les clients à l’aide de requêtes de métadonnées rencontrez des problèmes.

### <a name="bug-fixes"></a>Correctifs de bogues
Nous avons mis à niveau vers SQL Server 2016 SP2 CU2 avec CU7.1 de points d’accès. La mise à niveau résout certains problèmes décrits ci-dessous.

| Titre | Description |
|:---|:---|
| **Blocage de moteur de tuple potentiels** |La mise à niveau résout un risque de longue date d’interblocage dans un thread d’arrière-plan moteur tuple et les transactions distribué. Après avoir installé CU7.1, les clients qui utilisaient TF634 pour arrêter le moteur de tuple en tant que paramètre de démarrage de SQL Server ou l’indicateur de trace global peuvent en toute sécurité le supprimer. | 
| **Certaines requêtes lag/lead échoue** |Certaines requêtes sur les tables ICC avec des fonctions lag/lead imbriquée qui provoquait une erreur a été corrigé avec cette mise à niveau. | 


<a name="h2-aps-au7"></a>
## <a name="aps-au7"></a>APS AU7
Date de publication : mai 2018

APS 2016 est une condition préalable à la mise à niveau vers AU7. Nouvelles fonctionnalités dans APS AU7 sont les suivantes :

### <a name="auto-create-and-auto-update-statistics"></a>Création automatique et la mise à jour automatique des statistiques
APS AU7 crée et met à jour les statistiques automatiquement, par défaut. Pour mettre à jour les paramètres de statistiques, les administrateurs peuvent utiliser un nouvel élément de menu de commutateur de fonctionnalité dans le [Configuration Manager](appliance-configuration.md#CMTasks). Le [commutateur de fonctionnalité](appliance-feature-switch.md) contrôle l’auto-create, la mise à jour automatique et le comportement de mise à jour asynchrone des statistiques. Vous pouvez également mettre à jour les paramètres de statistiques avec le [ALTER DATABASE (Parallel Data Warehouse)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) instruction.

### <a name="t-sql"></a>T-SQL
Sélectionnez @var est désormais pris en charge. Pour plus d’informations, consultez [sélectionner la variable locale](/sql/t-sql/language-elements/select-local-variable-transact-sql) 

Indicateurs de requête HASH et ordre de groupe sont désormais pris en charge. Pour plus d’informations, consultez [Hints(Transact-SQL) - requête](/sql/t-sql/queries/hints-transact-sql-query)

### <a name="feature-switch"></a>Commutateur de fonctionnalité
APS AU7 introduit le commutateur de fonctionnalité dans [Configuration Manager](launch-the-configuration-manager.md). AutoStatsEnabled et DmsProcessStopMessageTimeoutInSeconds sont désormais des options configurables qui peuvent être modifiées par les administrateurs.

### <a name="known-issues"></a>Problèmes connus
Avec le logiciel de APS AU7, une mise à jour du BIOS Intel est fourni qui résout un problème appelé *attaques par canal latéral de l’exécution spéculative*. Les attaques visent à exploiter sont appelées *vulnérabilités Spectre et Meltdown*. Bien qu’il est empaqueté avec les points d’accès, la mise à jour du BIOS est installé manuellement et non comme faisant partie de l’installation du logiciel AU7 de points d’accès.

Microsoft conseille à tous les clients pour installer le BIOS mis à jour. Microsoft a mesuré l’effet de noyau virtuels adresse occultation (KVAS), Kernel Page Table Indirection (KPTI) et l’atténuation de prédiction de branchement Indirect (IBP) sur les différentes charges de travail SQL dans différents environnements. Les mesures de trouver une dégradation importante sur certaines charges de travail. En fonction des résultats, il est recommandé que vous tester l’effet de performances de l’activation de la mise à jour avant de les déployer dans un environnement de production. Consultez l’aide de SQL Server [ici](https://support.microsoft.com/help/4073225/guidance-protect-sql-server-against-spectre-meltdown).

::: moniker-end
::: moniker range=">= aps-pdw-2016 || = sqlallproducts-allversions"
<a name="h2-aps-au6"></a>
## <a name="aps-2016"></a>APS 2016
Cette section décrit les nouvelles fonctionnalités pour APS 2016-AU6.

### <a name="sql-server-2016"></a>SQL Server 2016

APS AU6 s’exécute sur la dernière version de SQL Server 2016 et utilise le niveau de compatibilité de base de données 130 par défaut. SQL Server 2016 permet la prise en charge de nouvelles fonctionnalités telles que :

- Index secondaires pour les index columnstore en cluster.
- Protocole Kerberos pour PolyBase.

### <a name="t-sql"></a>T-SQL
APS AU6 prend en charge ces améliorations de compatibilité de T-SQL.  Ces éléments de langage supplémentaires facilitent la migration à partir de SQL Server et d’autres sources de données. 

- [Classements SQL au niveau des colonnes][] sont désormais pris en charge, en plus des classements de Windows.
- [Index non cluster sur les index columnstore en cluster][] améliorer les performances des requêtes qui recherchent des valeurs spécifiques dans l’index cluster columnstore. 
- [SELECT...INTO][] 
- [sp_spaceused()][] affiche l’espace disque utilisé ou réservé dans une table ou une base de données.
- [Tableaux larges][] prise en charge est identique à SQL Server 2016. La limite de 32 Ko pour la taille de ligne n’existe plus. 

**Types de données**

- [VARCHAR(MAX)][], [NVARCHAR(MAX)][] et [VARBINARY(MAX)][]. Ces types de données LOB ont une taille maximale de 2 Go. Pour charger ces objets utilisent [utilitaire bcp][]. Actuellement, PolyBase et dwloader ne prennent en charge ces types de données. 
- [SYSNAME][]
- [UNIQUEIDENTIFIER][]
- [NUMERIC][] et types de données décimal.

**Fonctions de fenêtre**

- [ROWS ou RANGE][] dans la clause OVER de l’instruction SELECT.
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

### <a name="polybasehadoop-enhancements"></a>Améliorations de PolyBase/Hadoop

- Compatibilité avec Hortonworks HDP 2.4 et HDP 2.5
- Prise en charge de Kerberos via les informations d’identification de niveau base de données
- Prise en charge des informations d’identification avec des objets BLOB de stockage Azure

### <a name="install-and-upgrade-enhancements"></a>Installation et les améliorations de la mise à niveau

**Mises à jour de Enterprise architecture** mise à niveau de votre appliance existante vers APS AU6 installe la dernière version du microprogramme et les mises à jour du pilote, qui incluent des correctifs de sécurité. 

Un nouveau matériel à partir de HPE ou DELL inclut toutes les dernières mises à jour ainsi que :

- Prise en charge de dernière génération processeur (Broadwell)
- Mettre à jour vers inférieur de barrettes DIMM DDR4
- Améliorer le débit DIMM

**Integration**

- Entièrement prise en charge du nom de domaine complet (FQDN) permet de configurer une approbation de domaine à l’appliance. 
- Pour utiliser le nom de domaine complet, vous devez effectuer une mise à niveau complète et participer au cours de la mise à niveau. 

**Temps mort réduit** installation ou mise à niveau vers les points d’accès AU6 est plus rapide et nécessite moins de temps d’arrêt que les versions précédentes. Pour réduire les temps d’arrêt, l’installation ou la mise à niveau : 

 - Rationalise application des mises à jour WSUS à l’aide d’une image qui contient toutes les mises à jour via juin 2016
 - Applique les mises à jour de sécurité avec les mises à jour du microprogramme et du pilote
 - Place les derniers correctifs et l’utilitaire de vérification d’appliance (PAV) sur votre appliance, afin qu’ils soient prêtes à être installées sans avoir à les télécharger.

::: moniker-end

<!--
Link references to other articles in this same GitHub repo.

The link format that starts with '/sql/what-ever/my-artlcle' is not appropriate for common links within the same repo (as most of these link are).  The first couple links have been edited to show the proper syntax, but all other links in this article need to be similarly edited.
The proper formats have at least two big advantages.  One big advantage is that the proper formats enable the OPS Build system to detect broken links at Pull Request build time, instead of only later during run time.
-->
[database compatibility level 130]: ../t-sql/statements/alter-database-transact-sql-compatibility-level.md
[Classements SQL au niveau des colonnes]: ~/relational-databases/collations/collation-and-unicode-support.md

[Index non cluster sur les index columnstore en cluster]:/sql/t-sql/statements/create-index-transact-sql
[VARCHAR(MAX)]:/sql/t-sql/data-types/char-and-varchar-transact-sql
[NVARCHAR(MAX)]:/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql
[VARBINARY(MAX)]:/sql/t-sql/data-types/binary-and-varbinary-transact-sql
[SYSNAME]:/sql/relational-databases/system-catalog-views/sys-types-transact-sql
[SELECT...INTO]:/sql/t-sql/queries/select-into-clause-transact-sql
[sp_spaceused()]:/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql
[Tableaux larges]:/sql/sql-server/maximum-capacity-specifications-for-sql-server
[BULK INSERT]:/sql/t-sql/statements/bulk-insert-transact-sql
[Utilitaire bcp]:/sql/tools/bcp-utility
[UNIQUEIDENTIFIER]:/sql/t-sql/data-types/uniqueidentifier-transact-sql
[NUMERIC]:/sql/t-sql/data-types/decimal-and-numeric-transact-sql
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


  

  


