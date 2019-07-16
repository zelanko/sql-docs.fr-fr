---
title: Sys.dm_db_tuning_recommendations (Transact-SQL) | Microsoft Docs
description: Découvrez comment trouver d’éventuels problèmes de performances et recommandé de correctifs dans SQL Server et de la base de données SQL Azure
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
ms.openlocfilehash: dbee7422bdf58d753c31c7aa57a81bc4b29d2568
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096236"
---
# <a name="sysdmdbtuningrecommendations-transact-sql"></a>Sys.DM\_db\_paramétrage\_recommandations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Retourne des informations détaillées sur les recommandations de paramétrage.  
  
 Dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], les vues de gestion dynamique ne peuvent pas exposer des informations qui ont un impact sur la relation contenant-contenu de la base de données, ou exposer des informations concernant d'autres bases de données auxquelles l'utilisateur a accès. Pour éviter d’exposer ces informations, chaque ligne qui contient les données qui n’appartient pas au locataire connecté est filtrée.

| **Nom de la colonne** | **Type de données** | **Description** |
| --- | --- | --- |
| **name** | **nvarchar(4000)** | Nom unique de recommandation. |
| **type** | **nvarchar(4000)** | Le nom de l’option de réglage automatique qui a produit la recommandation, par exemple, `FORCE_LAST_GOOD_PLAN` |
| **reason** | **nvarchar(4000)** | Pourquoi cette recommandation a été fournie de raison. |
| **valide\_dans la mesure où** | **datetime2** | La première fois que cette recommandation a été générée. |
| **last\_refresh** | **datetime2** | La dernière fois cette recommandation a été générée. |
| **state** | **nvarchar(4000)** | Document JSON qui décrit l’état de la recommandation. Les champs suivants sont disponibles :<br />-   `currentValue` -l’état actuel de la recommandation.<br />-   `reason` -(constante) qui décrit la raison pour laquelle il est recommandé dans l’état actuel.|
| **est\_exécutable\_action** | **bit** | 1 = la recommandation peut être exécutée sur la base de données par le biais de [!INCLUDE[tsql_md](../../includes/tsql-md.md)] script.<br />0 = la recommandation ne peut pas être exécutée sur la base de données (par exemple : recommandation uniquement ou rétabli d’informations) |
| **est\_revertable\_action** | **bit** | 1 = la recommandation sont surveillée et automatiquement annulée par le moteur de base de données.<br />0 = la recommandation ne peut pas être surveillée et restaurée automatiquement. La plupart des &quot;exécutable&quot; actions seront &quot;revertable&quot;. |
| **execute\_action\_start\_time** | **datetime2** | Date de que la recommandation est appliquée. |
| **execute\_action\_duration** | **time** | Durée de l’action d’exécution. |
| **Exécutez\_action\_initié\_par** | **nvarchar(4000)** | `User` = Utilisateur forcer manuellement un plan dans la recommandation. <br /> `System` = Système appliqué automatiquement la recommandation. |
| **Exécutez\_action\_initié\_temps** | **datetime2** | Date de que la recommandation a été appliquée. |
| **rétablir\_action\_Démarrer\_temps** | **datetime2** | Date à laquelle que la recommandation a été annulée. |
| **revert\_action\_duration** | **time** | Durée de l’action de restauration. |
| **rétablir\_action\_initié\_par** | **nvarchar(4000)** | `User` = Plan recommandé manuellement obligation d’utilisateur. <br /> `System` = Système restauré automatiquement la recommandation. |
| **rétablir\_action\_initié\_temps** | **datetime2** | Date à laquelle que la recommandation a été annulée. |
| **score** | **Int** | Estimation du/de l’impact de cette recommandation sur le 0-100 mise à l’échelle (plus la meilleure) |
| **Détails** | **nvarchar(max)** | Document JSON qui contient des informations détaillées sur la recommandation. Les champs suivants sont disponibles :<br /><br />`planForceDetails`<br />-    `queryId` -requête\_id de la requête de régression.<br />-    `regressedPlanId` -plan_id du plan de régression.<br />-   `regressedPlanExecutionCount` -Nombre d’exécutions de la requête avec un plan de régression avant la régression est détecté.<br />-    `regressedPlanAbortedCount` -Nombre d’erreurs détectées pendant l’exécution du plan de régression.<br />-    `regressedPlanCpuTimeAverage` -Moyenne temps processeur consommé par la requête de régression avant la détection de la régression.<br />-    `regressedPlanCpuTimeStddev` -Écart de temps processeur consommé par la requête de régression avant la régression est détecté.<br />-    `recommendedPlanId` -plan_id du plan qui doit être forcé.<br />-   `recommendedPlanExecutionCount`-Nombre d’exécutions de la requête avec le plan qui doit être forcée avant la détection de la régression.<br />-    `recommendedPlanAbortedCount` -Nombre d’erreurs détectées pendant l’exécution du plan qui doit être forcée.<br />-    `recommendedPlanCpuTimeAverage` -Moyenne temps processeur consommé par la requête exécutée avec le plan qui doit être forcé (calculé avant la détection de la régression).<br />-    `recommendedPlanCpuTimeStddev` Écart de temps processeur consommé par la requête de régression avant la régression est détecté.<br /><br />`implementationDetails`<br />-  `method` -La méthode qui doit être utilisée pour corriger la régression. Valeur est toujours `TSql`.<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql-md.md)] script qui doit être exécuté pour forcer le plan recommandé. |
  
## <a name="remarks"></a>Notes  
 Informations retournées par `sys.dm_db_tuning_recommendations` est mis à jour lorsque le moteur de base de données identifie la régression potentielle des performances de requête et n’est pas persistant. Recommandations sont simplement conservées jusque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est redémarré. Les administrateurs de base de données doivent effectuer régulièrement des copies de sauvegarde de la recommandation de paramétrage s’ils souhaitent conserver après le recyclage du serveur. 

 `currentValue` champ dans le `state` colonne peut avoir les valeurs suivantes :
 
 | Statut | Description |
 |--------|-------------|
 | `Active` | Recommandation est active et non encore appliqué. Utilisateur peut prendre le script de recommandation et exécutez-le manuellement. |
 | `Verifying` | La recommandation est appliquée par [!INCLUDE[ssde_md](../../includes/ssde_md.md)] et processus de vérification interne compare les performances du plan forcé avec le plan de régression. |
 | `Success` | La recommandation est correctement appliquée. |
 | `Reverted` | Recommandation est annulée, car il n’y a aucune gains de performances significatifs. |
 | `Expired` | Recommandation a expiré et ne peut pas être appliquée plus. |

Document JSON dans `state` colonne contient la raison pour laquelle décrit la raison pour laquelle la recommandation dans l’état actuel. Les valeurs dans le champ raison peuvent être : 

| Reason | Description |
|--------|-------------|
| `SchemaChanged` | Recommandation a expiré, car le schéma d’une table référencée est modifié. |
| `StatisticsChanged`| Recommandation a expiré en raison de la modification de statistiques sur une table référencée. |
| `ForcingFailed` | Impossible de forcer le plan recommandé sur une requête. Rechercher la `last_force_failure_reason` dans le [sys.query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md) vue pour rechercher le motif de l’échec. |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN` option est désactivée par l’utilisateur pendant le processus de vérification. Activer `FORCE_LAST_GOOD_PLAN` option à l’aide de [AUTOMATIC_TUNING de définir de base de données ALTER &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) instruction ou forcer le plan manuellement à l’aide du script dans `[details]` colonne. |
| `UnsupportedStatementType` | Plan ne peut pas être forcé sur la requête. Exemples de requêtes non pris en charge sont les curseurs et `INSERT BULK` instruction. |
| `LastGoodPlanForced` | La recommandation est correctement appliquée. |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)] identifié de régression des performances potentielles, mais la `FORCE_LAST_GOOD_PLAN` option n’est pas activée, consultez [AUTOMATIC_TUNING de définir de base de données ALTER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md). Appliquer les recommandations manuellement ou activer `FORCE_LAST_GOOD_PLAN` option. |
| `VerificationAborted`| Processus de vérification est abandonnée en raison du redémarrage ou de nettoyage de la requête Store. |
| `VerificationForcedQueryRecompile`| La requête est recompilée, car il n’existe aucune amélioration significative des performances. |
| `PlanForcedByUser`| Utilisateur manuellement le plan l’utilisation forcée [sp_query_store_force_plan &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md) procédure. |
| `PlanUnforcedByUser` | Utilisateur unforced manuellement le plan à l’aide [sp_query_store_unforce_plan &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md) procédure. |

 Statistiques dans la colonne Détails n’affiche pas les statistiques de plan d’exécution (par exemple, temps de processeur actuelle). Les détails de la recommandation sont effectuées au moment de la détection de régression et décrivez pourquoi [!INCLUDE[ssde_md](../../includes/ssde_md.md)] identifié régression des performances. Utilisez `regressedPlanId` et `recommendedPlanId` à requête [affichages catalogue de Query Store](../../relational-databases/performance/how-query-store-collects-data.md) pour rechercher les statistiques de plan d’exécution exact.

## <a name="examples-of-using-tuning-recommendations-information"></a>Exemples d’utilisation des informations de recommandations de paramétrage  

### <a name="example-1"></a>Exemple 1
Le code suivant obtient le texte généré [!INCLUDE[tsql](../../includes/tsql-md.md)] script qui force un plan efficace pour une requête donnée :  
 
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
Le code suivant obtient le texte généré [!INCLUDE[tsql](../../includes/tsql-md.md)] script qui force une bonne planification de toute requête donnée et les informations supplémentaires concernant le gain estimé :

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
Le code suivant obtient le texte généré [!INCLUDE[tsql](../../includes/tsql-md.md)] script qui force un plan efficace pour toute requête donnée et des informations supplémentaires qui inclut le texte de requête et les plans de requête stockées dans le Store de la requête :

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

Pour plus d’informations sur les fonctions JSON qui peut être utilisé pour interroger les valeurs dans la vue de la recommandation, consultez [prise en charge JSON](../../relational-databases/json/index.md) dans [!INCLUDE[ssde_md](../../includes/ssde_md.md)].
  
## <a name="permissions"></a>Autorisations  

Requiert `VIEW SERVER STATE` autorisation dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].   
Nécessite le `VIEW DATABASE STATE` autorisation pour la base de données [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].   

## <a name="see-also"></a>Voir aussi  
 [Le réglage automatique](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [sys.database_automatic_tuning_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [Prise en charge JSON](../../relational-databases/json/index.md)
 
