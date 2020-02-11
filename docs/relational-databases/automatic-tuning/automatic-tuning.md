---
title: Réglage automatique | Microsoft Docs
description: En savoir plus sur le paramétrage automatique dans SQL Server et Azure SQL Database
ms.custom: ''
ms.date: 08/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- performance tuning [SQL Server]
ms.assetid: ''
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4ad185085c19d8286fa6a09e46742860a948849a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67934555"
---
# <a name="automatic-tuning"></a>Réglage automatique
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

L’optimisation automatique est une fonctionnalité de base de données qui fournit des insights sur les éventuels problèmes de performances des requêtes, recommande des solutions et corrige automatiquement les problèmes identifiés.

Le réglage automatique [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] dans vous avertit chaque fois qu’un problème de performances potentiel est détecté, et vous permet d’appliquer des actions [!INCLUDE[ssde_md](../../includes/ssde_md.md)] correctives ou de faire en sorte que le résolve automatiquement les problèmes de performances.
Le paramétrage [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] automatique de vous permet d’identifier et de résoudre les problèmes de performances provoqués par les **régressions de choix de plan d’exécution de requête**. Le paramétrage [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] automatique de crée également des index nécessaires et supprime les index inutilisés. Pour plus d’informations sur les plans d’exécution de requête, consultez [plans d’exécution](../../relational-databases/performance/execution-plans.md).

[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Surveille les requêtes exécutées sur la base de données et améliore automatiquement les performances de la charge de travail. [!INCLUDE[ssde_md](../../includes/ssde_md.md)] Dispose d’un mécanisme d’intelligence intégré qui peut automatiquement ajuster et améliorer les performances de vos requêtes en adaptant de manière dynamique la base de données à votre charge de travail. Deux fonctionnalités de réglage automatique sont disponibles :

 -  La **Correction de plan automatique** identifie les plans d’exécution de requête problématiques et résout les problèmes de performances du plan d’exécution de requête. **S’applique à** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (à compter de [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]) et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].
 -  La **gestion automatique des index** identifie les index qui doivent être ajoutés à votre base de données, ainsi que les index qui doivent être supprimés. **S’applique à**:[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]

## <a name="why-automatic-tuning"></a>À quoi sert le réglage automatique ?

Trois des tâches principales de l’administration de base de données classique sont la surveillance de [!INCLUDE[tsql_md](../../includes/tsql-md.md)] la charge de travail, l’identification des requêtes critiques, les index qui doivent être ajoutés pour améliorer les performances et l’identification rarement utilisée. Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] fournit des informations détaillées sur les requêtes et les index que vous devez surveiller. Toutefois, la surveillance permanente d’une base de données est une tâche difficile et fastidieuse, en particulier lors du traitement de plusieurs bases de données. Il peut être impossible de gérer efficacement un grand nombre de bases de données. Au lieu de surveiller et de paramétrer manuellement votre base de données, vous pouvez envisager de déléguer certaines actions de surveillance [!INCLUDE[ssde_md](../../includes/ssde_md.md)] et de paramétrage à la fonctionnalité à l’aide du réglage automatique.

### <a name="how-does-automatic-tuning-work"></a>Comment fonctionne le réglage automatique ?

Le réglage automatique est un processus de surveillance et d’analyse continu qui apprend constamment sur les caractéristiques de votre charge de travail et identifie les problèmes potentiels et les améliorations.

![Processus de réglage automatique](./media/tuning-process.png)

Ce processus permet à la base de données de s’adapter de manière dynamique à votre charge de travail en recherchant les index et les plans susceptibles d’améliorer les performances de vos charges de travail et les index qui affectent vos charges de travail. En fonction de ces résultats, le réglage automatique effectue des actions de réglage qui améliorent les performances de votre charge de travail. En outre, la base de données surveille en permanence les performances après toute modification apportée par le réglage automatique pour s’assurer qu’elle améliore les performances de votre charge de travail. Toute action qui n’a pas amélioré les performances est automatiquement rétablie. Ce processus de vérification est une fonctionnalité clé qui permet de s’assurer que les modifications apportées par le réglage automatique ne diminuent pas les performances de votre charge de travail.

## <a name="automatic-plan-correction"></a>Correction automatique du plan

La correction de plan automatique est une fonctionnalité de réglage automatique qui identifie la **régression de choix des plans d’exécution** et corrige automatiquement le problème en forçant le dernier plan correct connu. Pour plus d’informations sur les plans d’exécution de requête et l’optimiseur de requête, consultez le [Guide d’architecture de traitement des requêtes](../../relational-databases/query-processing-architecture-guide.md).

### <a name="what-is-execution-plan-choice-regression"></a>Qu’est-ce que la régression de choix de plan d’exécution ?

[!INCLUDE[ssdenoversion_md](../../includes/ssdenoversion_md.md)] Peut utiliser différents plans d’exécution pour exécuter les [!INCLUDE[tsql_md](../../includes/tsql-md.md)] requêtes. Les plans de requête dépendent des statistiques, des index et d’autres facteurs. Le plan optimal à utiliser pour exécuter une [!INCLUDE[tsql_md](../../includes/tsql-md.md)] requête peut être modifié au fil du temps. Dans certains cas, le nouveau plan peut ne pas être mieux que le précédent, et le nouveau plan peut entraîner une régression des performances.

 ![Régression de choix du plan d’exécution de requête](media/plan-choice-regression.png "Régression de choix du plan d’exécution de requête") 

Chaque fois que vous remarquerez la régression de choix de plan, vous devriez trouver un plan précédent et le forcer à `sp_query_store_force_plan` la place de la procédure actuelle.
[!INCLUDE[ssde_md](../../includes/ssde_md.md)]dans [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] fournit des informations sur les plans régressés et les actions correctives recommandées.
En outre, [!INCLUDE[ssde_md](../../includes/ssde_md.md)] vous permet d’automatiser entièrement ce processus et de [!INCLUDE[ssde_md](../../includes/ssde_md.md)] corriger tout problème trouvé en rapport avec les modifications du plan.

### <a name="automatic-plan-choice-correction"></a>Correction automatique du choix de plan

[!INCLUDE[ssde_md](../../includes/ssde_md.md)]peut automatiquement basculer vers le dernier plan correct connu chaque fois que la régression de choix de plan est détectée.

![Correction du choix du plan d’exécution de requête](media/force-last-good-plan.png "Correction du choix du plan d’exécution de requête") 

[!INCLUDE[ssde_md](../../includes/ssde_md.md)]détecte automatiquement toute régression de choix de plan potentielle, y compris le plan qui doit être utilisé à la place du plan incorrect.
Lorsque le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] applique le dernier plan correct connu, il surveille automatiquement les performances du plan forcé. Si le plan forcé n’est pas mieux que le plan régressé, le nouveau plan est non forcé et le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] compile un nouveau plan. Si le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] vérifie que le plan forcé est mieux que le plan régressé, le plan forcé est conservé s’il est mieux que le plan régressé, jusqu’à ce qu’une recompilation se produise (par exemple, lors de la mise à jour des statistiques suivante ou du changement de schéma).

> [!NOTE]
> Les plans d’exécution forcés automatiquement ne sont pas conservés entre les redémarrages de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.

### <a name="enabling-automatic-plan-choice-correction"></a>Activation de la correction automatique du choix de plan

Vous pouvez activer le réglage automatique pour chaque base de données et spécifier que le dernier bon plan connu doit être forcé quand une régression de changement de plan est détectée. Pour cela, utilisez la commande suivante :

```sql   
ALTER DATABASE current
SET AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = ON ); 
```

Une fois que vous activez cette option [!INCLUDE[ssde_md](../../includes/ssde_md.md)] , le force automatiquement toute recommandation dans laquelle le gain de processeur estimé est supérieur à 10 secondes, ou le nombre d’erreurs dans le nouveau plan est supérieur au nombre d’erreurs dans le plan recommandé, et vérifie que le plan forcé est mieux que le plan actuel.

### <a name="alternative---manual-plan-choice-correction"></a>Autre possibilité : la correction manuelle du choix de plan

Quand le réglage automatique n’est pas activé, les utilisateurs doivent régulièrement surveiller le système et rechercher les requêtes régressées. Si un plan a fait l’objet d’une régression, l’utilisateur doit trouver un plan précédent et le forcer `sp_query_store_force_plan` à la place de l’application actuelle à l’aide de la procédure. La meilleure pratique consiste à forcer le dernier plan correct connu car des plans plus anciens peuvent ne pas être valides en raison de modifications de statistiques ou d’index. L’utilisateur qui force le dernier plan correct connu doit surveiller les performances de la requête exécutée à l’aide du plan forcé et vérifier que le plan forcé fonctionne comme prévu. Selon les résultats de la surveillance et de l’analyse, le plan doit être forcé ou l’utilisateur doit trouver une autre façon d’optimiser la requête.
Les plans forcés manuellement ne doivent pas être indéfiniment forcés, car l’application doit être en mesure d’appliquer des [!INCLUDE[ssde_md](../../includes/ssde_md.md)] plans optimaux. L’utilisateur ou l’administrateur de bases de droits doit finalement `sp_query_store_unforce_plan` annuler l’application du plan [!INCLUDE[ssde_md](../../includes/ssde_md.md)] à l’aide de la procédure et laisser le plan optimal. 

> [!TIP]
> Alternativelly, utilisez les **requêtes avec des plans forcés** magasin des requêtes vue pour rechercher et annuler les plans.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]fournit toutes les vues et procédures nécessaires pour analyser les performances et résoudre les problèmes dans Magasin des requêtes.

Dans [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)], vous pouvez rechercher des régressions de choix de plan à l’aide d’magasin des requêtes vues système. Dans [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)], le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] détecte et affiche les régressions de choix de plan potentielles et les actions recommandées qui doivent être appliquées dans la vue [sys. dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md) . La vue affiche des informations sur le problème, l’importance du problème et des détails tels que la requête identifiée, l’ID du plan régressé, l’ID du plan utilisé comme ligne de base pour la comparaison et l' [!INCLUDE[tsql_md](../../includes/tsql-md.md)] instruction qui peut être exécutée pour résoudre le problème.

| type | description | DATETIME | de votre application | details | ... |
| --- | --- | --- | --- | --- | --- |
| `FORCE_LAST_GOOD_PLAN` | Temps processeur passé de 4 ms à 14 ms | 3/17/2017 | 83 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |
| `FORCE_LAST_GOOD_PLAN` | Temps processeur passé de 37 ms à 84 ms | 3/16/2017 | 26 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |

Certaines colonnes de cette vue sont décrites dans la liste suivante :
 - Type de l’action recommandée-`FORCE_LAST_GOOD_PLAN`
 - Description qui contient des informations [!INCLUDE[ssde_md](../../includes/ssde_md.md)] expliquant pourquoi cette modification de plan est une régression potentielle des performances
 - Date et heure de détection de la régression potentielle
 - Score de cette recommandation
 - Détails sur les problèmes tels que l’ID du plan détecté, l’ID du plan régressé, l’ID du plan qui doit être forcé à résoudre le problème, [!INCLUDE[tsql_md](../../includes/tsql-md.md)] le script qui peut être appliqué pour résoudre le problème, etc. Les détails sont stockés au [format JSON](../../relational-databases/json/index.md)

Utilisez la requête suivante pour obtenir un script qui résout le problème et des informations supplémentaires sur le gain estimé :

```sql   
SELECT reason, score,
      script = JSON_VALUE(details, '$.implementationDetails.script'),
      planForceDetails.*,
      estimated_gain = (regressedPlanExecutionCount + recommendedPlanExecutionCount)
                  * (regressedPlanCpuTimeAverage - recommendedPlanCpuTimeAverage)/1000000,
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

[!INCLUDE[ssresult-md](../../includes/ssresult-md.md)]     

| reason | de votre application | script | ID\_de requête | ID de\_plan actuel | ID de\_plan recommandé | gain\_estimé | risque\_d’erreur
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Temps processeur passé de 3 ms à 46 ms | 36 | EXEC SP\_Query\_Store\_force\_plan 12, 17 ; | 12 | 28 | 17 | 11,59 | 0

`estimated_gain`représente le nombre estimé de secondes qui seraient enregistrées si le plan recommandé est exécuté à la place du plan actuel. Le plan recommandé doit être forcé au lieu du plan actuel si le gain est supérieur à 10 secondes. S’il y a plus d’erreurs (par exemple, de délais d’attente ou d’exécutions abandonnées) dans le plan actuel que dans le plan `error_prone` recommandé, la colonne est définie `YES`sur la valeur. Le plan à risque d’erreur est une autre raison pour laquelle le plan recommandé doit être forcé à la place de celui actuel.

Bien [!INCLUDE[ssde_md](../../includes/ssde_md.md)] que fournit toutes les informations requises pour identifier les régressions de choix de plan ; la surveillance continue et la résolution des problèmes de performances peuvent être un processus fastidieux. Le réglage automatique facilite grandement ce processus.

> [!NOTE]
> Les données de la DMV sys. dm_db_tuning_recommendations ne sont pas conservées entre les redémarrages de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.

## <a name="automatic-index-management"></a>Gestion automatique des index

Dans [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)], la gestion des index est [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] simple, car elle apprend sur votre charge de travail et garantit que vos données sont toujours indexées de manière optimale. Pour assurer des performances optimales de votre charge de travail, l’index doit être correctement conçu. La gestion automatique des index peut vous aider à les optimiser. La gestion automatique des index permet de résoudre les problèmes de performances dans les bases de données indexées de manière incorrecte, ou de conserver et d’améliorer les index dans la structure de base de données existante. Le paramétrage [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] automatique de effectue les actions suivantes :

 - Identifie les index qui peuvent améliorer les performances de [!INCLUDE[tsql_md](../../includes/tsql-md.md)] vos requêtes qui lisent les données des tables.
 - Identifie les index redondants ou les index qui n’ont pas été utilisés pendant une période plus longue qui pourrait être supprimée. La suppression des index inutiles améliore les performances des requêtes qui mettent à jour les données dans les tables.

### <a name="why-do-you-need-index-management"></a>Pourquoi utiliser la gestion des index ?

Les index accélèrent certaines de vos requêtes qui lisent les données à partir des tables ; cependant, ils peuvent ralentir les requêtes qui mettent à jour les données. Vous devez analyser soigneusement quand créer un index et les colonnes que vous devez inclure dans l’index. Certains index peuvent ne plus être nécessaires après un certain temps. Par conséquent, vous devez régulièrement identifier et supprimer les index qui n’apportent aucun avantage. Si vous ignorez les index non utilisés, les performances des requêtes qui mettent à jour les données diminuent sans aucun avantage pour les requêtes qui lisent les données. Les index inutilisés affectent également les performances globales du système, car les mises à jour supplémentaires impliquent une journalisation inutile.

Pour trouver l’ensemble optimal d’index qui améliore les performances des requêtes qui lisent les données de vos tables et ont un impact minimal sur les mises à jour, vous aurez peut-être besoin d’une analyse continue complexe.

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]utilise l’intelligence intégrée et des règles avancées qui analysent vos requêtes, identifient les index qui seraient optimaux pour vos charges de travail actuelles, et les index peuvent être supprimés. Azure SQL Database permet de s’assurer que vous disposez de l’ensemble d’index minimal nécessaire à l’optimisation des requêtes qui lisent les données, avec un impact réduit sur les autres requêtes.

### <a name="automatic-index-management"></a>Gestion automatique des index

En plus de la détection [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] , peut appliquer automatiquement les recommandations identifiées. Si vous constatez que les règles intégrées améliorent les performances de votre base de données, [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] vous pouvez autoriser la gestion automatique de vos index.

Pour activer le réglage automatique [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] dans et permettre à la fonctionnalité de réglage automatique de gérer entièrement votre charge de travail, consultez [activer le réglage automatique dans Azure SQL Database à l’aide de portail Azure](/azure/sql-database/sql-database-automatic-tuning-enable).

Lorsque le [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] applique une recommandation créer un INDEX ou Drop Index, il surveille automatiquement les performances des requêtes qui sont affectées par l’index. Le nouvel index sera conservé uniquement si les performances des requêtes affectées sont améliorées. L’index supprimé sera automatiquement recréé s’il y a des requêtes qui s’exécutent plus lentement en raison de l’absence de l’index.

### <a name="automatic-index-management-considerations"></a>Considérations sur la gestion automatique des index

Les actions requises pour créer des index nécessaires [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] dans peuvent consommer des ressources et affecter temporellement les performances de la charge de travail. Pour réduire l’impact de la création d’index sur les [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] performances de la charge de travail, recherche la fenêtre de temps appropriée pour toute opération de gestion d’index. Le réglage est reporté à plus tard si la base de données a besoin de ressources pour exécuter votre charge de travail. Il démarre lorsque la base de données dispose de suffisamment de ressources inutilisées qui peuvent être exploitées pour la tâche de maintenance. Une fonctionnalité importante dans la gestion automatique des index est la vérification des actions. Lorsque [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] crée ou supprime un index, un processus de surveillance analyse les performances de votre charge de travail pour vérifier que l’action a amélioré les performances. S’il n’a pas été amélioré, l’action est immédiatement annulée. Ainsi, [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] les actions automatiques n’ont pas d’impact négatif sur les performances de votre charge de travail. Les index créés par le réglage automatique sont transparents pour l’opération de maintenance sur le schéma sous-jacent. Les modifications du schéma, par exemple le fait de supprimer ou de renommer des colonnes, ne sont pas bloquées par la présence d’index créés automatiquement. Les index créés automatiquement par [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] sont supprimés immédiatement lorsque la table ou les colonnes associées sont supprimées.

### <a name="alternative---manual-index-management"></a>Alternative-gestion manuelle des index

Sans la gestion automatique des index, l’utilisateur doit interroger manuellement [sys. dm_db_missing_index_details &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md) afficher ou utiliser le rapport tableau [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] de bord des performances dans pour rechercher des index susceptibles d’améliorer les performances, créer des index à l’aide des détails fournis dans cette vue et surveiller manuellement les performances de la requête. Pour rechercher les index qui doivent être supprimés, les utilisateurs doivent surveiller les statistiques d’utilisation opérationnelle des index pour trouver des index rarement utilisés.

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]simplifie ce processus. [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)]analyse votre charge de travail, identifie les requêtes qui peuvent être exécutées plus rapidement avec un nouvel index et identifie les index inutilisés ou en double. Pour plus d’informations sur l’identification des index à modifier, voir [Rechercher des recommandations d’index dans le portail Azure](https://docs.microsoft.com/azure/sql-database/sql-database-advisor-portal).

## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys. database_automatic_tuning_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)  
 [sys. dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 [sys. dm_db_missing_index_details &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sp_query_store_force_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)     
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)           
 [sys. database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [Fonctions JSON](../../relational-databases/json/index.md)    
 [Plans d’exécution](../../relational-databases/performance/execution-plans.md)    
 [Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [Outils de surveillance et d’optimisation des performances](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [Analyse des performances à l'aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
 [Assistant Paramétrage de requêtes](../../relational-databases/performance/upgrade-dbcompat-using-qta.md)
