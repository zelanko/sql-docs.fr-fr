---
title: sys. dm_db_tuning_recommendations (Transact-SQL) | Microsoft Docs
description: Découvrez comment identifier les problèmes de performances potentiels et les correctifs recommandés dans SQL Server et Azure SQL Database
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096236"
---
# <a name="sysdm_db_tuning_recommendations-transact-sql"></a>recommandations\_pour\_le\_paramétrage de sys.DM dB (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Retourne des informations détaillées sur les recommandations de paramétrage.  
  
 Dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], les vues de gestion dynamique ne peuvent pas exposer des informations qui ont un impact sur la relation contenant-contenu de la base de données, ou exposer des informations concernant d'autres bases de données auxquelles l'utilisateur a accès. Pour éviter d’exposer ces informations, chaque ligne qui contient des données qui n’appartiennent pas au locataire connecté est filtrée.

| **Nom de la colonne** | **Type de données** | **Description** |
| --- | --- | --- |
| **nomme** | **nvarchar(4000)** | Nom unique de recommandation. |
| **entrer** | **nvarchar(4000)** | Nom de l’option de réglage automatique qui a produit la recommandation, par exemple`FORCE_LAST_GOOD_PLAN` |
| **donc** | **nvarchar(4000)** | Raison pour laquelle cette recommandation a été fournie. |
| **valide\_depuis** | **datetime2** | La première fois que cette recommandation a été générée. |
| **dernière\_actualisation** | **datetime2** | Heure de la dernière génération de cette recommandation. |
| **Département** | **nvarchar(4000)** | Document JSON qui décrit l’état de la recommandation. Les champs suivants sont disponibles :<br />-   `currentValue`: état actuel de la recommandation.<br />-   `reason`-constante qui décrit la raison pour laquelle la recommandation est dans l’état actuel.|
| **est\_une\_action exécutable** | **bit** | 1 = la recommandation peut être exécutée sur la base [!INCLUDE[tsql_md](../../includes/tsql-md.md)] de données par le biais d’un script.<br />0 = la recommandation ne peut pas être exécutée sur la base de données (par exemple : information uniquement ou rétablie) |
| **\_\_** | **bit** | 1 = la recommandation peut être automatiquement surveillée et restaurée par le moteur de base de données.<br />0 = la recommandation ne peut pas être automatiquement surveillée et restaurée. La &quot;plupart des&quot; actions exécutables &quot;seront rétablies&quot;. |
| **heure\_de\_début\_de l’action d’exécution** | **datetime2** | Date à laquelle la recommandation est appliquée. |
| **durée\_de\_l’action d’exécution** | **time** | Durée de l’action d’exécution. |
| **exécuter\_l'\_action\_lancée par** | **nvarchar(4000)** | `User`= Planification forcée manuelle de l’utilisateur dans la recommandation. <br /> `System`= Recommandation appliquée automatiquement par le système. |
| **heure\_d'\_exécution\_initiée par l’action** | **datetime2** | Date à laquelle la recommandation a été appliquée. |
| **rétablir l'\_heure\_de\_début de l’action** | **datetime2** | Date à laquelle la recommandation a été annulée. |
| **durée de\_l'\_action de restauration** | **time** | Durée de l’action de restauration. |
| **annuler l'\_action\_initiée\_par** | **nvarchar(4000)** | `User`= Le plan recommandé par l’utilisateur n’est pas forcé manuellement. <br /> `System`= Le système rétablit automatiquement la recommandation. |
| **rétablir l'\_heure\_d'\_initiation de l’action** | **datetime2** | Date à laquelle la recommandation a été annulée. |
| **enjeu** | **int** | Valeur/impact estimé pour cette recommandation sur l’échelle 0-100 (plus la meilleure est grande) |
| **plus** | **nvarchar(max)** | Document JSON qui contient plus de détails sur la recommandation. Les champs suivants sont disponibles :<br /><br />`planForceDetails`<br />-    `queryId`: ID\_de requête de la requête régressée.<br />-    `regressedPlanId`-plan_id du plan régressé.<br />-   `regressedPlanExecutionCount`-Nombre d’exécutions de la requête avec un plan régressé avant la détection de la régression.<br />-    `regressedPlanAbortedCount`-Nombre d’erreurs détectées pendant l’exécution du plan régressé.<br />-    `regressedPlanCpuTimeAverage`-Temps processeur moyen consommé par la requête régressée avant la détection de la régression.<br />-    `regressedPlanCpuTimeStddev`-Écart type du temps processeur consommé par la requête régressée avant la détection de la régression.<br />-    `recommendedPlanId`-plan_id du plan qui doit être forcé.<br />-   `recommendedPlanExecutionCount`-Nombre d’exécutions de la requête avec le plan qui doit être forcé avant la détection de la régression.<br />-    `recommendedPlanAbortedCount`-Nombre d’erreurs détectées pendant l’exécution du plan qui doit être forcé.<br />-    `recommendedPlanCpuTimeAverage`-Temps processeur moyen consommé par la requête exécutée avec le plan qui doit être forcé (calculé avant la détection de la régression).<br />-    `recommendedPlanCpuTimeStddev`Écart type du temps processeur consommé par la requête régressée avant la détection de la régression.<br /><br />`implementationDetails`<br />-  `method`-Méthode qui doit être utilisée pour corriger la régression. La valeur est `TSql`toujours.<br />-    `script` - [!INCLUDE[tsql_md](../../includes/tsql-md.md)]script à exécuter pour forcer le plan recommandé. |
  
## <a name="remarks"></a>Notes  
 Les informations retournées par `sys.dm_db_tuning_recommendations` sont mises à jour lorsque le moteur de base de données identifie la régression potentielle des performances des requêtes et n’est pas conservée. Les recommandations sont conservées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uniquement jusqu’au redémarrage de. Les administrateurs de base de données doivent effectuer régulièrement des copies de sauvegarde de la recommandation de paramétrage si elles souhaitent les conserver après le recyclage du serveur. 

 `currentValue`le champ de `state` la colonne peut avoir les valeurs suivantes :
 
 | Statut | Description |
 |--------|-------------|
 | `Active` | La recommandation est active et n’est pas encore appliquée. L’utilisateur peut prendre un script de recommandation et l’exécuter manuellement. |
 | `Verifying` | La recommandation est appliquée [!INCLUDE[ssde_md](../../includes/ssde_md.md)] par et le processus de vérification interne compare les performances du plan forcé avec le plan régressé. |
 | `Success` | La recommandation a été appliquée avec succès. |
 | `Reverted` | La recommandation est annulée, car il n’y a pas d’amélioration significative des performances. |
 | `Expired` | La recommandation a expiré et ne peut plus être appliquée. |

Document JSON dans `state` la colonne contient la raison qui décrit la raison pour laquelle la recommandation est dans l’état actuel. Les valeurs du champ raison peuvent être : 

| Motif | Description |
|--------|-------------|
| `SchemaChanged` | La recommandation a expiré car le schéma d’une table référencée a été modifié. |
| `StatisticsChanged`| La recommandation a expiré en raison de la modification de la statistique sur une table référencée. |
| `ForcingFailed` | Le plan recommandé ne peut pas être forcé sur une requête. Recherchez `last_force_failure_reason` dans la vue [sys. query_store_plan](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md) pour trouver la raison de l’échec. |
| `AutomaticTuningOptionDisabled` | `FORCE_LAST_GOOD_PLAN`l’option est désactivée par l’utilisateur lors du processus de vérification. Activez `FORCE_LAST_GOOD_PLAN` l’option à l’aide de l’instruction [ALTER database SET AUTOMATIC_TUNING &#40;instruction Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md) ou forcez `[details]` le plan manuellement à l’aide du script de la colonne. |
| `UnsupportedStatementType` | Le plan ne peut pas être forcé sur la requête. Les curseurs et les `INSERT BULK` instructions sont des exemples de requêtes non prises en charge. |
| `LastGoodPlanForced` | La recommandation a été appliquée avec succès. |
| `AutomaticTuningOptionNotEnabled`| [!INCLUDE[ssde_md](../../includes/ssde_md.md)]identification de la régression potentielle des performances `FORCE_LAST_GOOD_PLAN` , mais l’option n’est pas activée-voir [ALTER database SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md). Appliquez la recommandation manuellement ou `FORCE_LAST_GOOD_PLAN` activez l’option. |
| `VerificationAborted`| Le processus de vérification est abandonné en raison du redémarrage ou du nettoyage du Magasin des requêtes. |
| `VerificationForcedQueryRecompile`| La requête est recompilée, car il n’y a pas d’amélioration significative des performances. |
| `PlanForcedByUser`| L’utilisateur a forcé manuellement le plan à l’aide de [sp_query_store_force_plan &#40;procédure&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md) . |
| `PlanUnforcedByUser` | L’utilisateur n’a pas forcé manuellement le plan à l’aide de [sp_query_store_unforce_plan &#40;procédure&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md) . |

 Les statistiques de la colonne Détails n’affichent pas les statistiques du plan d’exécution (par exemple, le temps processeur actuel). Les détails de la recommandation sont pris au moment de la détection de la régression et décrivent pourquoi [!INCLUDE[ssde_md](../../includes/ssde_md.md)] une régression des performances a été identifiée. Utilisez `regressedPlanId` et `recommendedPlanId` pour interroger [magasin des requêtes affichages catalogue](../../relational-databases/performance/how-query-store-collects-data.md) afin de rechercher des statistiques de plan d’exécution exactes.

## <a name="examples-of-using-tuning-recommendations-information"></a>Exemples d’utilisation des informations sur les recommandations de paramétrage  

### <a name="example-1"></a>Exemple 1
L’exemple suivant obtient le [!INCLUDE[tsql](../../includes/tsql-md.md)] script généré qui force un plan approprié pour une requête donnée :  
 
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
L’exemple suivant obtient le [!INCLUDE[tsql](../../includes/tsql-md.md)] script généré qui force un plan approprié pour une requête donnée et des informations supplémentaires sur le gain estimé :

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
L’exemple suivant obtient le [!INCLUDE[tsql](../../includes/tsql-md.md)] script généré qui force un plan approprié pour une requête donnée et des informations supplémentaires qui incluent le texte de la requête et les plans de requête stockés dans magasin des requêtes :

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

Pour plus d’informations sur les fonctions JSON qui peuvent être utilisées pour interroger des valeurs dans la vue recommandation, [!INCLUDE[ssde_md](../../includes/ssde_md.md)]consultez [prise en charge de JSON](../../relational-databases/json/index.md) dans.
  
## <a name="permissions"></a>Autorisations  

Nécessite `VIEW SERVER STATE` l’autorisation [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]dans.   
Requiert l' `VIEW DATABASE STATE` autorisation pour la base de [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]données dans.   

## <a name="see-also"></a>Voir aussi  
 [Réglage automatique](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [sys. database_automatic_tuning_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)   
 [sys. database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [Prise en charge de JSON](../../relational-databases/json/index.md)
 
