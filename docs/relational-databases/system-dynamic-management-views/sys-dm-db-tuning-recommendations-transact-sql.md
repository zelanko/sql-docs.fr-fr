---
title: sys.dm_db_tuning_recommendations (Transact-SQL) Microsoft Docs
description: Découvrez comment trouver des problèmes de performances potentiels et des correctifs recommandés dans SQL Server et Azure SQL Database
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_tuning_recommendations
- dm_db_tuning_recommendations
- sys.dm_db_tuning_recommendations_TSQL
- dm_db_tuning_recommendations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database tuning recommendations feature [SQL Server], sys.dm_db_tuning_recommendations dynamic management view
- sys.dm_db_tuning_recommendations dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e8c18ce07ba5e36dcbdb5750db77edf17495c7b9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285469"
---
# <a name="sysdm_db_tuning_recommendations-transact-sql"></a>sys.dm recommandations\_d’accordage\_\_(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Retourne des renseignements détaillés sur les recommandations d’accordage.  
  
 Dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], les vues de gestion dynamique ne peuvent pas exposer des informations qui ont un impact sur la relation contenant-contenu de la base de données, ou exposer des informations concernant d'autres bases de données auxquelles l'utilisateur a accès. Pour éviter d’exposer ces informations, chaque ligne qui contient des données qui n’appartiennent pas au locataire connecté est filtrée.

| **Nom de la colonne** | **Type de données** | **Description** |
| --- | --- | --- |
| **name** | **nvarchar(4000)** | Nom unique de recommandation. |
| **type** | **nvarchar(4000)** | Le nom de l’option d’accordage automatique qui a produit la recommandation, par exemple,`FORCE_LAST_GOOD_PLAN` |
| **reason** | **nvarchar(4000)** | Raison pour laquelle cette recommandation a été fournie. |
| **valide\_depuis** | **datetime2** | La première fois que cette recommandation a été générée. |
| **dernier\_rafraîchissement** | **datetime2** | La dernière fois que cette recommandation a été générée. |
| **État** | **nvarchar(4000)** | Document JSON qui décrit l’état de la recommandation. Les champs suivants sont disponibles :<br />-   `currentValue`- état actuel de la recommandation.<br />-   `reason`- constante qui décrit pourquoi la recommandation est dans l’état actuel.|
| **est\_exécutable\_action** | **bit** | 1 - La recommandation peut être [!INCLUDE[tsql_md](../../includes/tsql-md.md)] exécutée contre la base de données via script.<br />0 - La recommandation ne peut pas être exécutée contre la base de données (par exemple : information seulement ou recommandation inversée) |
| **est\_une\_action ressaptisable** | **bit** | 1 - La recommandation peut être automatiquement surveillée et retournée par le moteur de base de données.<br />0 - La recommandation ne peut pas être automatiquement surveillée et retournée. La &quot;plupart&quot; des &quot;actions&quot;exécutables seront re retournables . |
| **exécuter\_\_l’heure de début\_d’action** | **datetime2** | Date à laquelle la recommandation est appliquée. |
| **exécuter\_\_la durée d’action** | **Temps** | Durée de l’exécution de l’action. |
| **exécuter\_\_l’action initiée\_par** | **nvarchar(4000)** | `User`Plan forcé manuellement de l’utilisateur dans la recommandation. <br /> `System`- Recommandation appliquée automatiquement par le système. |
| **exécuter\_\_le\_temps initié par l’action** | **datetime2** | Date à laquelle la recommandation a été appliquée. |
| **inverser\_\_l’heure de début\_de l’action** | **datetime2** | Date à laquelle la recommandation a été retournée. |
| **inverser\_\_la durée de l’action** | **Temps** | Durée de l’action de retour. |
| **inverser\_\_l’action initiée\_par** | **nvarchar(4000)** | `User`Plan recommandé manuellement non forcé par l’utilisateur. <br /> `System`- Recommandation automatiquement retournée au système. |
| **inverser\_\_le\_temps de l’action** | **datetime2** | Date à laquelle la recommandation a été retournée. |
| **Score** | **int** | Valeur/impact estimé pour cette recommandation sur l’échelle 0-100 (plus grande est la meilleure) |
| **Détails** | **nvarchar(max)** | Document JSON qui contient plus de détails sur la recommandation. Les champs suivants sont disponibles :<br /><br />`planForceDetails`<br />-    `queryId`-\_question id de la requête régressée.<br />-    `regressedPlanId`- plan_id du plan régressé.<br />-   `regressedPlanExecutionCount`- Nombre d’exécutions de la requête avec plan régressé avant que la régression ne soit détectée.<br />-    `regressedPlanAbortedCount`- Nombre d’erreurs détectées lors de l’exécution du plan régressé.<br />-    `regressedPlanCpuTimeAverage`- Temps moyen de processeur (en micro secondes) consommé par la requête régressée avant que la régression ne soit détectée.<br />-    `regressedPlanCpuTimeStddev`- Déviation standard du temps de processeur consommé par la requête régressée avant que la régression ne soit détectée.<br />-    `recommendedPlanId`- plan_id du plan qui devrait être forcé.<br />-   `recommendedPlanExecutionCount`- Nombre d’exécutions de la requête avec le plan qui devrait être forcé avant que la régression ne soit détectée.<br />-    `recommendedPlanAbortedCount`- Nombre d’erreurs détectées lors de l’exécution du plan qui devraient être forcées.<br />-    `recommendedPlanCpuTimeAverage`- Temps moyen de processeur (en micro secondes) consommé par la requête exécutée avec le plan qui doit être forcé (calculé avant que la régression soit détectée).<br />-    `recommendedPlanCpuTimeStddev`Déviation standard du temps de processeur consommé par la requête régressée avant que la régression ne soit détectée.<br /><br />`implementationDetails`<br />-  `method`- La méthode qui doit être utilisée pour corriger la régression. La valeur `TSql`est toujours .<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql-md.md)]script qui doit être exécuté pour forcer le plan recommandé. |
  
## <a name="remarks"></a>Notes  
 Les informations `sys.dm_db_tuning_recommendations` retournées sont mises à jour lorsque le moteur de base de données identifie la régression potentielle des performances des requêtes et n’est pas persisté. Les recommandations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sont conservées que jusqu’à ce qu’elles soient redémarrées. Les administrateurs de base de données doivent périodiquement faire des copies de sauvegarde de la recommandation d’accordage s’ils veulent la conserver après le recyclage du serveur. 

 `currentValue`champ dans `state` la colonne pourrait avoir les valeurs suivantes:
 
 | Statut | Description |
 |--------|-------------|
 | `Active` | La recommandation est active et n’est pas encore appliquée. L’utilisateur peut prendre le script de recommandation et l’exécuter manuellement. |
 | `Verifying` | La recommandation [!INCLUDE[ssde_md](../../includes/ssde_md.md)] est appliquée par et le processus de vérification interne compare le rendement du plan forcé avec le plan régressé. |
 | `Success` | La recommandation est appliquée avec succès. |
 | `Reverted` | La recommandation est retournée parce qu’il n’y a pas de gains de rendement importants. |
 | `Expired` | La recommandation a expiré et ne peut plus être appliquée. |

Le document `state` JSON dans la colonne contient la raison qui décrit pourquoi est la recommandation dans l’état actuel. Les valeurs dans le domaine de la raison pourraient être : 

| Motif | Description |
|--------|-------------|
| `SchemaChanged` | La recommandation a expiré parce que le schéma d’un tableau référencé est modifié. Une nouvelle recommandation sera créée si une nouvelle régression du plan de requête est détectée sur le nouveau schéma. |
| `StatisticsChanged`| La recommandation a expiré en raison du changement statistique sur un tableau référencé. Une nouvelle recommandation sera créée si une nouvelle régression du plan de requête est détectée à partir de nouvelles statistiques. |
| `ForcingFailed` | Le plan recommandé ne peut pas être forcé sur une requête. Trouvez `last_force_failure_reason` le dans le [sys.query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md) vue pour trouver la raison de l’échec. |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN`l’option est désactivée par l’utilisateur pendant le processus de vérification. Activez l’option `FORCE_LAST_GOOD_PLAN` en utilisant [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Déclaration&#41;De Transact-SQL](../../t-sql/statements/alter-database-transact-sql-set-options.md) ou `[details]` forcez le plan manuellement à l’aide du script dans la colonne. |
| `UnsupportedStatementType` | Le plan ne peut pas être forcé sur la requête. Des exemples de requêtes non étayées sont des curseurs et `INSERT BULK` des déclarations. |
| `LastGoodPlanForced` | La recommandation est appliquée avec succès. |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)]identifié la régression potentielle `FORCE_LAST_GOOD_PLAN` des performances, mais l’option n’est pas activée - voir [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md). Appliquer la recommandation `FORCE_LAST_GOOD_PLAN` manuellement ou activer l’option. |
| `VerificationAborted`| Le processus de vérification est interrompu en raison du redémarrage ou du nettoyage du magasin De requête. |
| `VerificationForcedQueryRecompile`| La requête est recompilée parce qu’il n’y a pas d’amélioration significative des performances. |
| `PlanForcedByUser`| L’utilisateur a forcé manuellement le plan à utiliser sp_query_store_force_plan &#40;procédure [de&#41;Transact-SQL.](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md) Le moteur de base de données n’appliquera pas la recommandation si l’utilisateur décidait explicitement d’imposer un plan. |
| `PlanUnforcedByUser` | L’utilisateur a appliqué manuellement le plan à [l’aide de sp_query_store_unforce_plan &#40;procédure de&#41;Transact-SQL.](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md) Étant donné que l’utilisateur a explicitement retourné le plan recommandé, le moteur de base de données continuera d’utiliser le plan actuel et de générer une nouvelle recommandation si une certaine régression de plan se produit à l’avenir. |

 Les statistiques de la colonne des détails ne montrent pas les statistiques du plan d’exécution (par exemple, l’heure actuelle du processeur). Les détails de recommandation sont pris au moment [!INCLUDE[ssde_md](../../includes/ssde_md.md)] de la détection de régression et décrivent pourquoi la régression identifiée des performances. Utilisez `regressedPlanId` `recommendedPlanId` et interrogez les [vues du catalogue de Query Store](../../relational-databases/performance/how-query-store-collects-data.md) pour trouver les statistiques exactes du plan d’exécution.

## <a name="examples-of-using-tuning-recommendations-information"></a>Exemples d’utilisation d’informations sur les recommandations d’accordage  

### <a name="example-1"></a>Exemple 1
Ce qui suit [!INCLUDE[tsql](../../includes/tsql-md.md)] obtient le script généré qui force un bon plan pour n’importe quelle requête donnée:  
 
```sql
SELECT name, reason, score,
    JSON_VALUE(details, '$.implementationDetails.script') AS script,
    details.* 
FROM sys.dm_db_tuning_recommendations
CROSS APPLY OPENJSON(details, '$.planForceDetails')
    WITH (  [query_id] int '$.queryId',
            regressed_plan_id int '$.regressedPlanId',
            last_good_plan_id int '$.recommendedPlanId') AS details
WHERE JSON_VALUE(state, '$.currentValue') = 'Active';
```
### <a name="example-2"></a>Exemple 2
Ce qui suit [!INCLUDE[tsql](../../includes/tsql-md.md)] obtient le script généré qui force un bon plan pour n’importe quelle requête donnée et des informations supplémentaires sur le gain estimé:

```sql
SELECT reason, score,
      script = JSON_VALUE(details, '$.implementationDetails.script'),
      planForceDetails.*,
      estimated_gain = (regressedPlanExecutionCount + recommendedPlanExecutionCount)
                  *(regressedPlanCpuTimeAverage - recommendedPlanCpuTimeAverage)/1000000,
      error_prone = IIF(regressedPlanErrorCount > recommendedPlanErrorCount, 'YES','NO')
FROM sys.dm_db_tuning_recommendations
CROSS APPLY OPENJSON (Details, '$.planForceDetails')
    WITH (  [query_id] int '$.queryId',
            regressedPlanId int '$.regressedPlanId',
            recommendedPlanId int '$.recommendedPlanId',
            regressedPlanErrorCount int,
            recommendedPlanErrorCount int,
            regressedPlanExecutionCount int,
            regressedPlanCpuTimeAverage float,
            recommendedPlanExecutionCount int,
            recommendedPlanCpuTimeAverage float
          ) AS planForceDetails;
```

### <a name="example-3"></a>Exemple 3
Ce qui suit [!INCLUDE[tsql](../../includes/tsql-md.md)] obtient le script généré qui force un bon plan pour toute requête donnée et des informations supplémentaires qui comprend le texte de requête et les plans de requête stockés dans Le magasin de requête:

```sql
WITH cte_db_tuning_recommendations
AS (SELECT reason,
        score,
        query_id,
        regressedPlanId,
        recommendedPlanId,
        current_state = JSON_VALUE(state, '$.currentValue'),
        current_state_reason = JSON_VALUE(state, '$.reason'),
        script = JSON_VALUE(details, '$.implementationDetails.script'),
        estimated_gain = (regressedPlanExecutionCount + recommendedPlanExecutionCount)
                * (regressedPlanCpuTimeAverage - recommendedPlanCpuTimeAverage)/1000000,
        error_prone = IIF(regressedPlanErrorCount > recommendedPlanErrorCount, 'YES','NO')
    FROM sys.dm_db_tuning_recommendations
    CROSS APPLY OPENJSON(Details, '$.planForceDetails')
    WITH ([query_id] int '$.queryId',
        regressedPlanId int '$.regressedPlanId',
        recommendedPlanId int '$.recommendedPlanId',
        regressedPlanErrorCount int,    
        recommendedPlanErrorCount int,
        regressedPlanExecutionCount int,
        regressedPlanCpuTimeAverage float,
        recommendedPlanExecutionCount int,
        recommendedPlanCpuTimeAverage float
        )
    )
SELECT qsq.query_id,
    qsqt.query_sql_text,
    dtr.*,
    CAST(rp.query_plan AS XML) AS RegressedPlan,
    CAST(sp.query_plan AS XML) AS SuggestedPlan
FROM cte_db_tuning_recommendations AS dtr
INNER JOIN sys.query_store_plan AS rp ON rp.query_id = dtr.query_id
    AND rp.plan_id = dtr.regressedPlanId
INNER JOIN sys.query_store_plan AS sp ON sp.query_id = dtr.query_id
    AND sp.plan_id = dtr.recommendedPlanId
INNER JOIN sys.query_store_query AS qsq ON qsq.query_id = rp.query_id
INNER JOIN sys.query_store_query_text AS qsqt ON qsqt.query_text_id = qsq.query_text_id;
```

Pour plus d’informations sur les fonctions JSON qui peuvent être utilisés [!INCLUDE[ssde_md](../../includes/ssde_md.md)]pour interroger les valeurs dans la vue de recommandation, voir [JSON Support](../../relational-databases/json/index.md) dans .
  
## <a name="permissions"></a>Autorisations  

Nécessite `VIEW SERVER STATE` la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]permission dans .   
Nécessite `VIEW DATABASE STATE` la permission pour [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]la base de données dans .   

## <a name="see-also"></a>Voir aussi  
 [Réglage automatique](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [sys.database_automatic_tuning_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [Soutien JSON](../../relational-databases/json/index.md)
 
