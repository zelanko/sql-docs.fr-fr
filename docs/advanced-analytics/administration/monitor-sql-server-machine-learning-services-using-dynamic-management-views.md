---
title: Surveiller l’exécution de script R et Python à l’aide de vues de gestion dynamique (DMV) - SQL Server Machine Learning
description: Utiliser des vues de gestion dynamique (DMV) pour surveiller l’exécution de script externe R et Python dans SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 8d701d9e8595eee3a583e913baabc2148af214fe
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67681623"
---
# <a name="monitor-sql-server-machine-learning-services-using-dynamic-management-views-dmvs"></a>Surveiller SQL Server Machine Learning Services à l’aide de vues de gestion dynamique (DMV)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Utilisez les vues de gestion dynamique (DMV) pour surveiller l’exécution d’external scripts (R et Python), des ressources utilisées, diagnostiquer les problèmes et régler les performances dans SQL Server Machine Learning Services.

Dans cet article, vous trouverez les DMV qui sont spécifiques à SQL Server Machine Learning Services. Vous y trouverez également des exemples de requêtes qui montrent :

+ Paramètres et les options de configuration pour l’apprentissage
+ Sessions actives en cours d’exécution des scripts R ou Python externes
+ Statistiques d’exécution pour le runtime externe pour R et Python
+ Compteurs de performances pour les scripts externes
+ Utilisation de la mémoire pour le système d’exploitation, SQL Server et pools de ressources externes
+ Configuration de la mémoire pour SQL Server et les pools de ressources externes
+ Pools de ressources du gouverneur de ressources, y compris les pools de ressources externes
+ Packages installés pour R et Python

Pour obtenir des informations plus générales sur les vues DMV, consultez [les vues de gestion dynamique système](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).

> [!TIP]
> Vous pouvez également utiliser les rapports personnalisés pour surveiller SQL Server Machine Learning Services. Pour plus d’informations, consultez [surveiller machine learning en utilisant des rapports personnalisés dans Management Studio](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="dynamic-management-views"></a>Vues de gestion dynamique

Les vues de gestion dynamique suivantes peuvent être utilisés lors de l’analyse des charges de travail machine learning dans SQL Server. Pour interroger les vues de gestion dynamique, vous devez `VIEW SERVER STATE` autorisation sur l’instance.

| Vue de gestion dynamique | type | Description |
|-------------------------|------|-------------|
| [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) | Exécution | Renvoie une ligne pour chaque compte de travail actif qui exécute un script externe. |
| [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) | Exécution | Renvoie une ligne pour chaque type de demande de script externe. |
| [sys.dm_os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md) | Exécution | Renvoie une ligne par compteur de performance maintenu par le serveur. Si vous utilisez la condition de recherche `WHERE object_name LIKE '%External Scripts%'`, vous pouvez utiliser ces informations pour voir combien de scripts a été exécuté, ce qui les scripts ont été exécutés à l’aide de quel mode d’authentification ou combien de R ou d’appels de Python ont été émis sur l’instance globale. |
| [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) | gouverneur de ressources | Retourne des informations sur l’état actuel du pool de ressources externes dans gouverneur de ressources, la configuration actuelle de pools de ressources et les statistiques de pool de ressources. |
| [sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md) | gouverneur de ressources | Retourne les informations d’affinité du processeur sur la configuration de pool de ressources externes en cours dans le gouverneur de ressources. Retourne une ligne par planificateur dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] où chaque planificateur est associé à un processeur. Vous pouvez utiliser cette vue pour surveiller la condition d'un planificateur ou pour identifier des tâches d'échappement. |

Pour plus d’informations sur la surveillance [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] instances, consultez [affichages catalogue](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) et [Resource Governor vues de gestion dynamiques](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).

## <a name="settings-and-configuration"></a>Paramètres et la configuration

Afficher les options d’installation Machine Learning Services paramètre et la configuration.

![Requête de configuration des paramètres de sortie](media/dmv-settings-and-configuration.png "requête de la configuration des paramètres de sortie")

Exécutez la requête ci-dessous pour obtenir la sortie suivante. Pour plus d’informations sur les vues et les fonctions utilisées, consultez [sys.dm_server_registry](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md), [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md), et [SERVERPROPERTY](../../t-sql/functions/serverproperty-transact-sql.md).

```sql
SELECT CAST(SERVERPROPERTY('IsAdvancedAnalyticsInstalled') AS INT) AS IsMLServicesInstalled
    , CAST(value_in_use AS INT) AS ExternalScriptsEnabled
    , COALESCE(SIGN(SUSER_ID(CONCAT (
                    CAST(SERVERPROPERTY('MachineName') AS NVARCHAR(128))
                    , '\SQLRUserGroup'
                    , CAST(serverproperty('InstanceName') AS NVARCHAR(128))
                    ))), 0) AS ImpliedAuthenticationEnabled
    , COALESCE((
            SELECT CAST(r.value_data AS INT)
            FROM sys.dm_server_registry AS r
            WHERE r.registry_key LIKE 'HKLM\Software\Microsoft\Microsoft SQL Server\%\SuperSocketNetLib\Tcp'
            AND r.value_name = 'Enabled'
            ), - 1) AS IsTcpEnabled
FROM sys.configurations
WHERE name = 'external scripts enabled';
```

La requête retourne les colonnes suivantes :

| colonne | Description |
|--------|-------------|
| IsMLServicesInstalled | Retourne 1 si SQL Server Machine Learning Services est installé pour l’instance. Sinon, retourne 0. |
| ExternalScriptsEnabled | Retourne 1 si les scripts externes est activé pour l’instance. Sinon, retourne 0. |
| ImpliedAuthenticationEnabled | Retourne 1 si l’authentification implicite est activé. Sinon, retourne 0. La configuration pour l’authentification implicite est vérifiée en vérifiant si une connexion existe pour SQLRUserGroup. |
| IsTcpEnabled | Retourne 1 si le protocole TCP/IP est activé pour l’instance. Sinon, retourne 0. Pour plus d’informations, consultez [Configuration protocole du réseau par défaut SQL Server](../../database-engine/configure-windows/default-sql-server-network-protocol-configuration.md). |

## <a name="active-sessions"></a>Sessions actives

Afficher les sessions actives en cours d’exécution des scripts externes.

![La sortie à partir de la requête active paramètres](media/dmv-active-sessions.png "la sortie à partir de la requête de paramètres actifs")

Exécutez la requête ci-dessous pour obtenir la sortie suivante. Pour plus d’informations sur les vues de gestion dynamique utilisées, consultez [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md), [sys.dm_external_script_requests](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md), et [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md).

```sql
SELECT r.session_id, r.blocking_session_id, r.status, DB_NAME(s.database_id) AS database_name
    , s.login_name, r.wait_time, r.wait_type, r.last_wait_type, r.total_elapsed_time, r.cpu_time
    , r.reads, r.logical_reads, r.writes, er.language, er.degree_of_parallelism, er.external_user_name
FROM sys.dm_exec_requests AS r
INNER JOIN sys.dm_external_script_requests AS er
ON r.external_script_request_id = er.external_script_request_id
INNER JOIN sys.dm_exec_sessions AS s
ON s.session_id = r.session_id;
```

La requête retourne les colonnes suivantes :

| colonne | Description |
|--------|-------------|
| session_id | Identifie la session associée à chaque connexion principale active. |
| blocking_session_id | ID de la session qui bloque la demande. Si cette colonne est NULL, la demande n'est pas bloquée, ou les informations de session de la session bloquant la demande ne sont pas disponibles (ou ne peuvent pas être identifiées). |
| status | Statut de la demande. |
| database_name | Nom de la base de données actuelle pour chaque session. |
| login_name | Nom de connexion SQL Server sous lequel la session est en cours d’exécution. |
| wait_time | Si la demande est actuellement bloquée, cette colonne retourne la durée de l'attente, en millisecondes. N'accepte pas la valeur NULL. |
| wait_type | Si la demande est actuellement bloquée, cette colonne retourne le type d'attente. Pour plus d’informations sur les types d’attentes, consultez [sys.dm_os_wait_stats](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md). |
| last_wait_type | Si la demande a été bloquée précédemment, cette colonne indique le type de la dernière attente. |
| total_elapsed_time | Temps total écoulé en millisecondes depuis l'arrivée de la demande. |
| cpu_time | Quantité de temps UC (en millisecondes) utilisée par la demande. |
| reads | Nombre de lectures effectuées par la demande. |
| logical_reads | Nombre de lectures logiques effectuées par la demande. |
| writes | Nombre d'écritures effectuées par la demande. |
| langage | Mot clé qui représente un langage de script pris en charge. |
| degree_of_parallelism | Nombre indiquant le nombre de traitements parallèles qui ont été créés. Cette valeur peut être différente du nombre de traitements parallèles qui ont été demandés. |
| external_user_name | Le compte de travail Windows sous lequel le script a été exécuté. |

## <a name="execution-statistics"></a>Statistiques d'exécution

Afficher les statistiques d’exécution pour le runtime externe pour R et Python. Uniquement les statistiques de fonctions du package microsoftml RevoScaleR ou revoscalepy sont actuellement disponibles.

![La sortie à partir de la requête de statistiques d’exécution](media/dmv-execution-statistics.png "la sortie à partir de la requête de statistiques d’exécution")

Exécutez la requête ci-dessous pour obtenir la sortie suivante. Pour plus d’informations sur la vue de gestion dynamique utilisée, consultez [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). La requête retourne uniquement les fonctions qui ont été exécutées plusieurs fois.

```sql
SELECT language, counter_name, counter_value
FROM sys.dm_external_script_execution_stats
WHERE counter_value > 0
ORDER BY language, counter_name;
```

La requête retourne les colonnes suivantes :

| colonne | Description |
|--------|-------------|
| langage | Nom du langage enregistré de script externe. |
| counter_name | Nom de la fonction enregistrée de script externe. |
| counter_value | Nombre total d’instance appelée de la fonction enregistrée de script externe sur le serveur. Cette valeur, cumulative, commence par l’horodatage d’installation de la fonction sur l’instance. Elle ne peut pas être réinitialisée. |

## <a name="performance-counters"></a>Compteurs de performance

Afficher les compteurs de performances liés à l’exécution de scripts externes.

![Requête des compteurs de sortie à partir de la performance](media/dmv-performance-counters.png "requête des compteurs de sortie de l’exécution")

Exécutez la requête ci-dessous pour obtenir la sortie suivante. Pour plus d’informations sur la vue de gestion dynamique utilisée, consultez [sys.dm_os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md).

```sql
SELECT counter_name, cntr_value
FROM sys.dm_os_performance_counters 
WHERE object_name LIKE '%External Scripts%'
```

**Sys.dm_os_performance_counters** génère les compteurs de performances suivants pour les scripts externes :

| Compteur | Description |
|---------|-------------|
| Nombre total d’exécutions | Nombre de processus externes démarrés par des appels locaux ou distants. |
| Exécutions parallèles | Nombre de fois où un script contenait la _@parallel_ spécification et que [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] a été en mesure de générer et utiliser un plan de requête parallèle. |
| Exécutions avec diffusion en continu | Nombre de fois où la fonctionnalité de diffusion en continu a été appelée. |
| Exécutions de contexte de calcul SQL | Nombre de scripts externes exécuter où l’appel a été instancié à distance et SQL Server a été utilisé comme contexte de calcul. |
| Connexions avec authentification implicite Connexions | Nombre de fois où un appel de bouclage ODBC a été effectué à l’aide de l’authentification implicite ; Autrement dit, le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] exécuté l’appel au nom de l’utilisateur qui envoie la demande de script. |
| Durée totale d’exécution (ms) | Temps écoulé entre l’appel et l’achèvement de l’appel. |
| Erreurs d’exécution | Nombre de scripts ont signalé des erreurs. Ce nombre n’inclut pas les erreurs de R ou Python. |

## <a name="memory-usage"></a>Utilisation de la mémoire

Afficher des informations sur la mémoire utilisée par le système d’exploitation, SQL Server et les pools externes.

![La sortie à partir de la requête de l’utilisation de mémoire](media/dmv-memory-usage.png "la sortie à partir de la requête de l’utilisation de mémoire")

Exécutez la requête ci-dessous pour obtenir la sortie suivante. Pour plus d’informations sur les vues de gestion dynamique utilisées, consultez [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) et [sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md).

```sql
SELECT physical_memory_kb, committed_kb
    , (SELECT SUM(peak_memory_kb)
        FROM sys.dm_resource_governor_external_resource_pools AS ep
        ) AS external_pool_peak_memory_kb
FROM sys.dm_os_sys_info;
```

La requête retourne les colonnes suivantes :

| colonne | Description |
|--------|-------------|
| physical_memory_kb | Quantité totale de mémoire physique sur l’ordinateur. |
| committed_kb | La mémoire allouée en kilo-octets (Ko) dans le Gestionnaire de mémoire. Elle ne comprend pas la mémoire réservée dans le gestionnaire de mémoire. |
| external_pool_peak_memory_kb | La somme de la quantité maximale de mémoire utilisée, en kilo-octets, pour tous les pools de ressources externes. |

## <a name="memory-configuration"></a>Configuration de la mémoire

Afficher des informations sur la configuration de mémoire maximale en pourcentage de SQL Server et les pools de ressources externes. Si SQL Server est en cours d’exécution avec la valeur par défaut `max server memory (MB)`, elle est considérée comme 100 % de la mémoire du système d’exploitation.

![La sortie à partir de la requête de configuration mémoire](media/dmv-memory-configuration.png "la sortie à partir de la requête de configuration de mémoire")

Exécutez la requête ci-dessous pour obtenir la sortie suivante. Pour plus d’informations sur les vues utilisées, consultez [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) et [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md).

```sql
SELECT 'SQL Server' AS name
    , CASE CAST(c.value AS BIGINT)
        WHEN 2147483647 THEN 100
        ELSE (SELECT CAST(c.value AS BIGINT) / (physical_memory_kb / 1024.0) * 100 FROM sys.dm_os_sys_info)
        END AS max_memory_percent
FROM sys.configurations AS c
WHERE c.name LIKE 'max server memory (MB)'
UNION ALL
SELECT CONCAT ('External Pool - ', ep.name) AS pool_name, ep.max_memory_percent
FROM sys.dm_resource_governor_external_resource_pools AS ep;
```

La requête retourne les colonnes suivantes :

| colonne | Description |
|--------|-------------|
| name | Nom du pool de ressources externes ou SQL Server. |
| max_memory_percent | Mémoire maximale que SQL Server ou le pool de ressources externes peut utiliser. |

## <a name="resource-pools"></a>Pools de ressources

Dans [gouverneur de ressources SQL Server](../../relational-databases/resource-governor/resource-governor.md), un [pool de ressources](../../relational-databases/resource-governor/resource-governor-resource-pool.md) représente un sous-ensemble des ressources physiques d’une instance. Vous pouvez spécifier des limites sur la quantité d’UC, e/s physiques et de mémoire que les demandes d’application entrantes, y compris l’exécution de scripts externes, dans le pool de ressources. Afficher les pools de ressources utilisés pour SQL Server et de scripts externes.

![Requête des pools de sortie à partir de la ressource](media/dmv-resource-pools.png "requête des pools de sortie à partir de la ressource")

Exécutez la requête ci-dessous pour obtenir la sortie suivante. Pour plus d’informations sur les vues de gestion dynamique utilisées, consultez [sys.dm_resource_governor_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md) et [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md).

```sql
SELECT CONCAT ('SQL Server - ', p.name) AS pool_name
    , p.total_cpu_usage_ms, p.read_io_completed_total, p.write_io_completed_total
FROM sys.dm_resource_governor_resource_pools AS p
UNION ALL
SELECT CONCAT ('External Pool - ', ep.name) AS pool_name
    , ep.total_cpu_user_ms, ep.read_io_count, ep.write_io_count
FROM sys.dm_resource_governor_external_resource_pools AS ep;
```

La requête retourne les colonnes suivantes :

| colonne | Description |
|--------|-------------|
| nom du pool | Nom du pool de ressources. Pools de ressources SQL Server sont précédés de `SQL Server` et pools de ressources externes sont précédés de `External Pool`.
| total_cpu_usage_hours | L’utilisation du processeur cumulée en millisecondes depuis que les statistiques du gouverneur de ressources ont été réinitialisées. |
| read_io_completed_total | Total d'entrées/sorties de lecture terminées depuis que les statistiques du gouverneur de ressources ont été réinitialisées. |
| write_io_completed_total | Total des entrées/sorties d'écriture terminées depuis que les statistiques du gouverneur de ressources ont été réinitialisées. |

## <a name="installed-packages"></a>Packages installés

Vous pouvez pour afficher les packages R et Python sont installées dans SQL Server Machine Learning Services en exécutant un script R ou Python qui génère ces.

### <a name="installed-packages-for-r"></a>Packages installés pour R

Afficher les packages R dans SQL Server Machine Learning Services.

![La sortie à partir de packages installés pour la requête de R](media/dmv-installed-packages-r.png "la sortie à partir de packages installés pour la requête de R")

Exécutez la requête ci-dessous pour obtenir la sortie suivante. Cette requête utilise un script R pour déterminer les packages R installés avec SQL Server.

```sql
EXEC sp_execute_external_script @language = N'R'
, @script = N'
OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
    , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
```

Les colonnes retournées sont :

| colonne | Description |
|--------|-------------|
| Package | Nom du package installé. |
| Version | Version du package. |
| Dépend | Répertorie les packages qui le package installé dépend. |
| Licence | Licence pour le package installé. |
| LibPath | Répertoire où vous pouvez trouver le package. |

### <a name="installed-packages-for-python"></a>Packages installés pour Python

Afficher les packages Python dans SQL Server Machine Learning Services.

![La sortie à partir de packages installés pour la requête de Python](media/dmv-installed-packages-python.png "la sortie à partir de packages installés pour la requête de Python")

Exécutez la requête ci-dessous pour obtenir la sortie suivante. La requête utiliser un script Python pour déterminer les packages Python installés avec SQL Server.

```sql
EXEC sp_execute_external_script @language = N'Python'
, @script = N'
import pip
OutputDataSet = pandas.DataFrame([(i.key, i.version, i.location) for i in pip.get_installed_distributions()])'
WITH result sets((Package NVARCHAR(128), Version NVARCHAR(128), Location NVARCHAR(1000)));
```

Les colonnes retournées sont :

| colonne | Description |
|--------|-------------|
| Package | Nom du package installé. |
| Version | Version du package. |
| Location | Répertoire où vous pouvez trouver le package. |

## <a name="next-steps"></a>Étapes suivantes

+ [Gestion et surveillance des solutions Machine Learning](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)
+ [Événements étendus pour machine learning](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md)
+ [Vues de gestion dynamique liées à gouverneur de ressources](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)
+ [Vues de gestion dynamique système](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
+ [Moniteur machine learning en utilisant des rapports personnalisés dans Management Studio](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md)