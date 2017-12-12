---
title: "Mise à jour - Documentation des bases de données relationnelles | Microsoft Docs"
description: "Affichage d’extraits de contenu mis à jour de la documentation récemment modifiée des bases de données relationnelles."
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.openlocfilehash: 1fbc7affa833eb34b6e13e28b229d47ac0b05a5c
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Contenu nouveau et récemment mis à jour : documentation des bases de données relationnelles



Presque tous les jours, Microsoft met à jour certains de ses articles sur son site web de documentation [Docs.Microsoft.com](http://docs.microsoft.com/). Cet article contient des extraits d’articles récemment mis à jour. Des liens vers de nouveaux articles peuvent également être répertoriés.

Cet article est généré par un programme qui est réexécuté régulièrement. Un extrait peut parfois apparaître avec une mise en forme imparfaite ou au format Markdown de l’article source. Les images ne sont jamais affichées ici.

Les mises à jour récentes sont signalées pour la plage de dates et le sujet suivants :



- *Période des mises à jour :* &nbsp; **28-09-2017** &nbsp; au &nbsp; **02-12-2017**
- *Domaine :* &nbsp; **bases de données relationnelles**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nouveaux articles créés récemment

Les liens suivants renvoient aux nouveaux articles ajoutés récemment.


1. [Utiliser SSMS XEvent Profiler](extended-events/use-the-ssms-xe-profiler.md)
2. [Assistant Importation d’un fichier plat dans SQL](import-export/import-flat-file-wizard.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articles mis à jour avec des extraits

Cette section affiche les extraits des mises à jour collectés dans des articles qui ont récemment fait l’objet d’une mise à jour importante.

Les extraits affichés ici apparaissent séparés de leur contexte sémantique propre. Un extrait est parfois séparé de la syntaxe Markdown importante qui l’entoure dans l’article. Ces extraits sont donc donnés à titre indicatif uniquement. Les extraits vous permettent seulement de savoir si les articles correspondants vont vous intéresser et si oui, de cliquer dessus pour les consulter.

Pour cela et pour d’autres raisons, ne copiez pas le code de ces extraits et ne prenez pas à la lettre les extraits de texte. Consultez plutôt l’article.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Liste compacte d’articles mis à jour récemment

Cette liste compacte fournit des liens vers tous les articles mis à jour qui sont répertoriés dans la section des extraits.

1. [Base de données tempdb](#TitleNum_1)
2. [Guide d’architecture de gestion de la mémoire](#TitleNum_2)
3. [Statistiques](#TitleNum_3)
4. [sp_server_diagnostics (Transact-SQL)](#TitleNum_4)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-tempdb-databasedatabasestempdb-databasemd"></a>1. &nbsp; [ Base de données tempdb](databases/tempdb-database.md)

*Mise à jour : 20/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Suivant](#TitleNum_2))

<!-- Source markdown line 121.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5c8bb5f9c40625aaf955295e5b5d03e4257e6c6b 337555ea28f4c3fdd6b78f1bfb4d62607a6bf92d  (PR=4039  ,  Filename=tempdb-database.md  ,  Dirpath=docs\relational-databases\databases\  ,  MergeCommitSha40=ef1fa818beea435f58986af3379853dc28f5efd8) -->



**Optimisation des performances de tempdb**

 La taille et l’emplacement physique de la base de données tempdb peuvent influer sur les performances d’un système. Par exemple, si la taille définie pour tempdb est trop petite, il se peut qu’à chaque redémarrage de l’instance de ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)], une partie de la charge de traitement du système soit absorbée par l’ajustement automatique de tempdb à la taille nécessaire à la gestion de la charge de travail.

 Si possible, utilisez [l’initialisation instantanée des fichiers de base de données--../../relational-databases/databases/database-instant-file-initialization.md) pour améliorer les performances des opérations de développement du fichier de données.

 Pré-allouez l'espace de tous les fichiers de tempdb en définissant leur taille avec une valeur suffisamment élevée pour assumer la charge de travail habituelle de l'environnement. Cela évite que tempdb ne se développe trop fréquemment et que les performances n'en soient affectées. La base de données tempdb doit être définie de façon à autoriser la croissance automatique, mais celle-ci doit être utilisée pour augmenter l'espace disque en cas d'exceptions non prévues.

 Les fichiers de données doivent être de taille égale au sein de chaque [groupe de fichiers--../../relational-databases/databases/database-files-and-filegroups.md#filegroups), car ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] utilise un algorithme de remplissage proportionnel qui privilégie les allocations dans les fichiers avec davantage d’espace libre. Le fait de diviser tempdb en plusieurs fichiers de données de taille égale procure un niveau élevé d’efficacité parallèle dans les opérations qui utilisent tempdb.

 Définissez l'incrément de croissance de la taille du fichier avec une taille suffisante afin d'éviter que la valeur de croissance des fichiers de la base de données tempdb ne soit trop faible. Si, au vu de la quantité de données à écrire dans la base de données tempdb, l'incrément de croissance est trop faible, la base de données tempdb risque d'avoir à se développer en permanence, affectant ainsi les performances.

 Pour vérifier les paramètres actuels de croissance et de taille de tempdb, utilisez la requête suivante :
```sql
 SELECT name AS FileName,
    size*1.0/128 AS FileSizeinMB,
    CASE max_size
        WHEN 0 THEN 'Autogrowth is off.'
        WHEN -1 THEN 'Autogrowth is on.'
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-memory-management-architecture-guidememory-management-architecture-guidemd"></a>2. &nbsp; [Guide d’architecture de gestion de la mémoire](memory-management-architecture-guide.md)

*Mise à jour : 28/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_1) | [Suivant](#TitleNum_3))

<!-- Source markdown line 75.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 dd47431ca47eab16af40e41adaeeaf3fc5fb7461 445f013af3bdad65dd3eaf837db7f744b43e8f97  (PR=4113  ,  Filename=memory-management-architecture-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=28cccac53767db70763e5e705b8cc59a83c77317) -->



Dans les versions antérieures de SQL Server (..!NCLUDE-NotShown--ssVersion2005--../includes/ssversion2005-md.md)], ..!NCLUDE-NotShown--ssKatmai--../includes/ssKatmai-md.md)] et ..!NCLUDE-NotShown--ssKilimanjaro--../includes/ssKilimanjaro-md.md)]), la mémoire était allouée par cinq mécanismes différents :
-  **Allocateur de page unique (SPA)**, comprenant uniquement les allocations de mémoire inférieures ou égales à 8 Ko dans le processus ..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)]. Les options de configuration *Mémoire maximum du serveur (Mo)* et *Mémoire minimum du serveur (Mo)* déterminaient les limites de la mémoire physique consommée par SPA. Le pool de tampons était aussi le mécanisme pour SPA et le plus grand consommateur d’allocations de pages uniques.
-  **Allocateur de plusieurs pages (MPA)**, pour les allocations de mémoire demandant plus de 8 Ko.
-  **Allocateur du CLR**, comprenant les segments de mémoire du CLR SQL et ses allocations globales créées durant l’initialisation du CLR.
-  Allocations de mémoire pour les **[--piles de threads--../relational-databases/memory-management-architecture-guide.md#stacksizes)** dans le processus ..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)].
-  **Allocations Windows directes (DWA)**, pour les demandes d’allocation de mémoire apportées directement à Windows. Il s’agit notamment de l’utilisation des segments de mémoire Windows et des allocations virtuelles directes effectuées par les modules chargés dans le processus ..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)]. Les allocations à partir des DLL de procédure stockée étendue, les objets créés au moyen de procédures Automation (appels sp_OA) et les allocations à partir de fournisseurs de serveur lié sont des exemples de demandes d’allocation de mémoire.

À compter de ..!NCLUDE-NotShown--ssSQL11--../includes/sssql11-md.md)], les allocations de page unique, de plusieurs pages et du CLR sont regroupées dans un **allocateur de pages de « toute taille »**, les limites de mémoire étant contrôlées par les options de configuration *Mémoire maximum du serveur (Mo)* et *Mémoire minimum du serveur (Mo)*. Ce changement offre des capacités de redimensionnement plus précises pour tous les besoins en mémoire transitant par le Gestionnaire de mémoire de ..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)].



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-statisticsstatisticsstatisticsmd"></a>3. &nbsp; [Statistiques](statistics/statistics.md)

*Mise à jour : 27/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_2) | [Suivant](#TitleNum_4))

<!-- Source markdown line 48.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1dbe3bd6fdfcd27cf4a597cac5a4a09821b51ba7 971cfccf75fbc8842a0ef020a2bc93992c5f4ad9  (PR=4087  ,  Filename=statistics.md  ,  Dirpath=docs\relational-databases\statistics\  ,  MergeCommitSha40=9fbe5403e902eb996bab0b1285cdade281c1cb16) -->



> [!NOTE]
> Les histogrammes dans ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] sont créés uniquement pour une seule colonne (la première colonne dans le jeu de colonnes clés de l’objet de statistiques).

Pour créer l'histogramme, l'optimiseur de requête trie les valeurs de colonnes, calcule le nombre de valeurs qui correspondent à chaque valeur de colonne distincte, puis regroupe les valeurs de colonnes dans 200 étapes d'histogramme contiguës au maximum. Chaque étape de l’histogramme inclut une plage de valeurs de colonnes, suivie d’une valeur de colonne de limite supérieure. La plage comprend toutes les valeurs de colonnes possibles entre des valeurs limites, à l'exception des valeurs limites elles-mêmes. La plus basse des valeurs de colonnes triées est la valeur de limite supérieure pour la première étape d'histogramme.

Plus précisément, ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] crée **l’histogramme** à partir du jeu trié de valeurs de colonne en trois étapes :

- **Initialisation de l’histogramme** : Dans la première étape, une suite de valeurs situées au début du jeu trié est traitée, et jusqu’à 200 valeurs de *range_high_key*, *equal_rows*, *range_rows* et *distinct_range_rows* sont collectées (*range_rows* et *distinct_range_rows* ont toujours une valeur nulle lors de cette étape). La première étape se termine quand toutes les entrées ont été traitées ou quand 200 valeurs ont été trouvées.
- **Analyse avec fusion des compartiments** : chaque valeur supplémentaire, issue de la première colonne de la clé de statistiques, est traitée selon l’ordre de tri à la deuxième étape. Chaque valeur suivante est ajoutée à la dernière plage ou une nouvelle plage est créée à la fin (ceci est possible parce que les valeurs d’entrée sont triées). Si une plage est créée, une paire de plages voisines existantes est réduite en une plage unique. Cette paire de plages est sélectionnée pour minimiser la perte d’informations. Cette méthode utilise un algorithme de *différence maximale* pour réduire le nombre d’étapes dans l’histogramme, tout en augmentant la différence entre les valeurs limites. Le nombre d’étapes après réduction des plages reste à 200 pendant toute la durée de cette étape.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-spserverdiagnostics-transact-sqlsystem-stored-proceduressp-server-diagnostics-transact-sqlmd"></a>4. &nbsp; [sp_server_diagnostics (Transact-SQL)](system-stored-procedures/sp-server-diagnostics-transact-sql.md)

*Mise à jour : 21/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Précédent](#TitleNum_3))

<!-- Source markdown line 157.  ms.author= "edmaca".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 d0d97efbb0b16638d0120af9ac5e66ec3bcfa391 b98735ec26a091f8c8c58ca1790243be7942e038  (PR=4052  ,  Filename=sp-server-diagnostics-transact-sql.md  ,  Dirpath=docs\relational-databases\system-stored-procedures\  ,  MergeCommitSha40=45e4efb7aa828578fe9eb7743a1a3526da719555) -->



L’exemple de requête ci-dessous lit la sortie sous forme de résumé de la table :
```sql
SELECT create_time,
       component_name,
       state_desc
FROM SpServerDiagnosticsResult;
```

L’exemple de requête ci-dessous lit une partie de la sortie détaillée de chaque composant dans la table :
```sql
-- system
select data.value('(/system/@systemCpuUtilization)[1]','bigint') as 'System_CPU',
   data.value('(/system/@sqlCpuUtilization)[1]','bigint') as 'SQL_CPU',
   data.value('(/system/@nonYieldingTasksReported)[1]','bigint') as 'NonYielding_Tasks',
   data.value('(/system/@pageFaults)[1]','bigint') as 'Page_Faults',
   data.value('(/system/@latchWarnings)[1]','bigint') as 'Latch_Warnings',
   data.value('(/system/@BadPagesDetected)[1]','bigint') as 'BadPages_Detected',
   data.value('(/system/@BadPagesFixed)[1]','bigint') as 'BadPages_Fixed'
from SpServerDiagnosticsResult
where component_name like 'system'
go

-- Resource Monitor
select data.value('(./Record/ResourceMonitor/Notification)[1]', 'VARCHAR(max)') AS [Notification],
    data.value('(/resource/memoryReport/entry[@description=''Working Set'']/@value)[1]', 'bigint')/1024 AS [SQL_Mem_in_use_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Paging File'']/@value)[1]', 'bigint')/1024 AS [Avail_Pagefile_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Physical Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_Physical_Mem_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Virtual Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_VAS_MB],
    data.value('(/resource/@lastNotification)[1]','varchar(100)') as 'LastNotification',
    data.value('(/resource/@outOfMemoryExceptions)[1]','bigint') as 'OOM_Exceptions'
from SpServerDiagnosticsResult
where component_name like 'resource'
go

-- Nonpreemptive waits
```







## <a name="similar-articles"></a>Articles similaires

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

Cette section liste les articles très similaires récemment mis à jour dans d’autres domaines, dans notre dépôt public GitHub.com : [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Zones de sujet avec des articles nouveaux ou mis à jour récemment

- [Nouveaux + Mis à jour (3 + 14) : **Analytique avancée pour SQL** (documentation)](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nouveaux + Mis à jour (1 + 0) : **Analysis Services pour SQL** (documentation)](../analysis-services/new-updated-analysis-services.md)
- [Nouveaux + Mis à jour (87 + 0) : **Système de la plateforme d’analyse pour SQL** (documentation)](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nouveaux + Mis à jour (5 + 4) : **Connexion à SQL** (documentation)](../connect/new-updated-connect.md)
- [Nouveaux + Mis à jour (0 + 1) : **Moteur de base de données pour SQL** (documentation)](../database-engine/new-updated-database-engine.md)
- [Nouveaux + Mis à jour (2 + 2) : **Integration Services pour SQL** (documentation)](../integration-services/new-updated-integration-services.md)
- [Nouveaux + Mis à jour (10 + 9) : **Linux pour SQL** (documentation)](../linux/new-updated-linux.md)
- [Nouveaux + Mis à jour (2 + 4) : **Bases de données relationnelles pour SQL** (documentation)](../relational-databases/new-updated-relational-databases.md)
- [Nouveaux + Mis à jour (4 + 2) : **Reporting Services pour SQL** (documentation)](../reporting-services/new-updated-reporting-services.md)
- [Nouveaux + Mis à jour (0 + 1) : **Exemples pour SQL** (documentation)](../sample/new-updated-sample.md)
- [Nouveaux + Mis à jour (21 + 0)  : **SQL Operations Studio** (documentation)](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nouveaux + Mis à jour (5 + 1) : **Microsoft SQL Server** (documentation)](../sql-server/new-updated-sql-server.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Data Tools (SSDT)** (documentation)](../ssdt/new-updated-ssdt.md)
- [Nouveaux + Mis à jour (1 + 0) : **Assistant Migration SQL Server (SSMA)** (documentation)](../ssma/new-updated-ssma.md)
- [Nouveaux + Mis à jour (0 + 1) : **SQL Server Management Studio (SSMS)** (documentation)](../ssms/new-updated-ssms.md)
- [Nouveaux + Mis à jour (0 + 2) : **Transact-SQL** (documentation)](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Zones de sujet sans article nouveau ou mis à jour récemment

- [Nouveaux + Mis à jour (0 + 0) : **Data Migration Assistant (DMA) pour SQL** (documentation)](../dma/new-updated-dma.md)
- [Nouveaux + Mis à jour (0 + 0) : **ActiveX Data Objects (ADO) pour SQL** (documentation)](../ado/new-updated-ado.md)
- [Nouveaux + Mis à jour (0 + 0) : **Data Quality Services pour SQL** (documentation)](../data-quality-services/new-updated-data-quality-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Extensions DMX (Data Mining Extensions) pour SQL** (documentation)](../dmx/new-updated-dmx.md)
- [Nouveaux + Mis à jour (0 + 0) : **Master Data Services (MDS) for SQL** (documentation)](../master-data-services/new-updated-master-data-services.md)
- [Nouveaux + Mis à jour (0 + 0) : **Expressions MDX (Multidimensional Expressions) pour SQL** (documentation)](../mdx/new-updated-mdx.md)
- [Nouveaux + Mis à jour (0 + 0) : **ODBC (Open Database Connectivity) pour SQL** (documentation)](../odbc/new-updated-odbc.md)
- [Nouveaux + Mis à jour (0 + 0) : **PowerShell pour SQL** (documentation)](../powershell/new-updated-powershell.md)
- [Nouveaux + Mis à jour (0 + 0) : **Outils pour SQL** (documentation)](../tools/new-updated-tools.md)
- [Nouveaux + Mis à jour (0 + 0) : **XQuery pour SQL** (documentation)](../xquery/new-updated-xquery.md)


