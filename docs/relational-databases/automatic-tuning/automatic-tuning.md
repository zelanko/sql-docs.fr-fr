---
title: Le réglage automatique | Microsoft Docs
description: En savoir plus sur le réglage automatique dans SQL Server et de la base de données SQL Azure
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7382e4d1b9e9d968d7ad87af9830691dd931d657
ms.sourcegitcommit: 170c275ece5969ff0c8c413987c4f2062459db21
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54226616"
---
# <a name="automatic-tuning"></a>Paramétrage automatique
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

L’optimisation automatique est une fonctionnalité de base de données qui fournit des insights sur les éventuels problèmes de performances des requêtes, recommande des solutions et corrige automatiquement les problèmes identifiés.

Le réglage automatique dans [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] vous avertit chaque fois qu’un problème de performances potentiel est détecté et vous permet d’appliquer des actions correctives ou de laisser le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] résoudre automatiquement les problèmes de performances.
Le réglage automatique dans [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] vous permet d’identifier et résoudre les problèmes de performances causés par **régressions de choix du plan d’exécution de requête**. Le réglage automatique dans [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] également crée des index nécessaires et les index inutilisés. Pour plus d’informations sur les plans d’exécution de requête, consultez [Plans d’exécution](../../relational-databases/performance/execution-plans.md).

Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] surveille les requêtes qui sont exécutées automatiquement et sur la base de données améliore les performances de la charge de travail. Le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] dispose d’un mécanisme d’intelligence intégrée qui peut automatiquement régler et améliorer les performances de vos requêtes en adaptant de manière dynamique la base de données à votre charge de travail. Il existe deux fonctionnalités de paramétrage automatique qui sont disponibles :

 -  **Correction automatique du plan** identifie les requêtes problématiques, l’exécution des plans et résout des problèmes de performances du plan de l’exécution des requêtes. **S’applique à** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (En commençant par [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]) et [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
 -  **Gestion automatique des index** identifie les index qui doivent être ajoutés à votre base de données et ceux qui doit être supprimés. **S’applique à** : [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]

## <a name="why-automatic-tuning"></a>Pourquoi le réglage automatique ?

Trois des principales tâches d’administration de base de données classique analysez la charge de travail, en identifiant critiques [!INCLUDE[tsql_md](../../includes/tsql-md.md)] les requêtes, les index qui doivent être ajoutées pour améliorer les performances et identification rarement utilisés. Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] fournit des informations détaillées sur les requêtes et les index que vous devez surveiller. Toutefois, le contrôle en permanence et une base de données est une tâche difficile et fastidieuse, en particulier lors du traitement de nombreuses bases de données. La gestion d’un très grand nombre de bases de données peut s’avérer impossible de faire de façon efficace. Au lieu de surveillance et de régler votre base de données manuellement, vous pouvez envisager de déléguer certaines de la surveillance et réglage des actions à la [!INCLUDE[ssde_md](../../includes/ssde_md.md)] à l’aide de la fonctionnalité de réglage automatique.

### <a name="how-does-automatic-tuning-work"></a>Comment est établie de réglage automatique ?

Le réglage automatique est un processus d’analyse qui apprend en permanence sur les caractéristiques de votre charge de travail et de surveillance continue et identifier les problèmes et améliorations potentiels.

![Processus de réglage automatique](./media/tuning-process.png)

Ce processus permet de s’adapter dynamiquement à votre charge de travail en recherchant les plans et les index peuvent améliorer les performances de vos charges de travail et les index qui affectent vos charges de travail de base de données. En fonction de ces résultats, le réglage automatique effectue les actions de réglage qui améliorent les performances de votre charge de travail. En outre, base de données surveille en permanence les performances après toute modification apportée par le réglage automatique pour vous assurer qu’il améliore les performances de votre charge de travail. Toute action qui n’a pas améliorer les performances est automatiquement annulée. Ce processus de vérification est une fonctionnalité clé qui permet de s’assurer que toute modification apportée par le réglage automatique ne diminue pas les performances de votre charge de travail.

## <a name="automatic-plan-correction"></a>Correction automatique du plan

Correction du plan automatique est une fonctionnalité de réglage automatique identifie **régression de choix des plans d’exécution** et résoudre automatiquement le problème en forçant le dernier plan correct connu. Pour plus d’informations sur les plans d’exécution et l’optimiseur de requête, consultez la [Guide d’Architecture de traitement des requêtes](../../relational-databases/query-processing-architecture-guide.md).

### <a name="what-is-execution-plan-choice-regression"></a>Quelle est la régression de choix du plan d’exécution ?

Le [!INCLUDE[ssdenoversion_md](../../includes/ssdenoversion_md.md)] peut utiliser des plans d’exécution pour exécuter le [!INCLUDE[tsql_md](../../includes/tsql-md.md)] requêtes. Plans de requête varient selon les statistiques, les index et les autres facteurs. Le plan optimal qui doit être utilisé pour exécuter certaines [!INCLUDE[tsql_md](../../includes/tsql-md.md)] requête peut être modifiée au fil du temps. Dans certains cas, le nouveau plan peut ne pas être une meilleure que la précédente, et le nouveau plan peut entraîner une baisse des performances.

 ![Régression de choix du plan d’exécution de requête](media/plan-choice-regression.png "régression de choix du plan d’exécution de requête") 

Chaque fois que vous remarquez la régression de choix de plan, vous devriez trouver corrects précédents planifient et forcer au lieu d’utiliser un cours `sp_query_store_force_plan` procédure.
[!INCLUDE[ssde_md](../../includes/ssde_md.md)] dans [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] fournit des informations sur le point ont régressé plans et les actions correctives recommandées.
En outre, [!INCLUDE[ssde_md](../../includes/ssde_md.md)] vous permet d’automatiser ce processus entièrement et de laisser [!INCLUDE[ssde_md](../../includes/ssde_md.md)] résoudre tout problème rencontré liées à ces modifications de plan.

### <a name="automatic-plan-choice-correction"></a>Correction automatique du plan choix

[!INCLUDE[ssde_md](../../includes/ssde_md.md)] peut basculer automatiquement vers le dernier plan correct connu chaque fois que la régression de choix de plan est détectée.

![Correction de choix de plan d’exécution de requête](media/force-last-good-plan.png "correction de choix de plan d’exécution de requête") 

[!INCLUDE[ssde_md](../../includes/ssde_md.md)] détecte automatiquement de régression de choix plan potentielle, notamment le plan doit être utilisé au lieu du plan incorrect.
Lorsque le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] applique le dernier bon plan connu, il surveille automatiquement les performances du plan forcé. Si le plan forcé n’est pas meilleur que le plan de régression, le nouveau plan sera obligation et la [!INCLUDE[ssde_md](../../includes/ssde_md.md)] compilera un nouveau plan. Si le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] vérifie que le plan forcé est préférable au plan, le plan forcé est conservé si il est préférable que le plan régressé, jusqu'à ce qu’une recompilation se produit (par exemple, sur la prochaine statistiques mises à jour ou schéma modification).

> [!NOTE]
> N’importe quel automatique de plans d’exécution forcée ne sont pas conservées entre les redémarrages de le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.

### <a name="enabling-automatic-plan-choice-correction"></a>L’activation de correction automatique du plan choix

Vous pouvez activer le réglage automatique pour chaque base de données et spécifier que le dernier bon plan connu doit être forcé quand une régression de changement de plan est détectée. Pour cela, utilisez la commande suivante :

```sql   
ALTER DATABASE current
SET AUTOMATIC_TUNING ( FORCE_LAST_GOOD_PLAN = ON ); 
```

Une fois que vous activez cette option, le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] automatiquement forcer une recommandation où le gain d’UC estimé est supérieur à 10 secondes, ou le nombre d’erreurs dans le nouveau plan est supérieur au nombre d’erreurs dans le plan recommandé et vérifiez que le plan forcé est préférable à celle en cours.

### <a name="alternative---manual-plan-choice-correction"></a>Autre possibilité : correction des choix de plan manuel

Quand le réglage automatique n’est pas activé, les utilisateurs doivent régulièrement surveiller le système et rechercher les requêtes régressées. Si n’importe quel plan régressé, ils doivent rechercher précédent bien planifier et force au lieu d’utiliser un cours `sp_query_store_force_plan` procédure. La meilleure pratique serait de forcer le dernier plan correct connu, car des plans plus anciens ne sont pas valides en raison de modifications des statistiques ou des index. L’utilisateur qui force le dernier plan correct connu doit surveiller les performances de la requête est exécutée à l’aide du plan forcé et vérifiez que le plan forcé fonctionne comme prévu. Selon les résultats de la surveillance et l’analyse, plan doit être forcé ou ils doivent rechercher une autre façon d’optimiser la requête.
Plans forcés manuellement ne doivent pas être forcées indéfiniment, étant donné que le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] doit être en mesure d’appliquer des plans non optimaux. L’utilisateur ou un administrateur doit finalement annuler l’application forcée du plan à l’aide `sp_query_store_unforce_plan` procédure et laisser le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] trouver le plan optimal. 

> [!TIP]
> Alternativelly, utilisez le **requêtes avec des Plans forcés** vue requête Store pour localiser et annuler l’application forcée des plans.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit toutes les vues nécessaires et les procédures requises pour surveiller les performances et résoudre les problèmes dans le Store de la requête.

Dans [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)], vous pouvez rechercher les régressions de choix de plan à l’aide de vues de système de Store de la requête. Dans [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)], le [!INCLUDE[ssde_md](../../includes/ssde_md.md)] détecte et montre les régressions de choix de plan potentiels et les actions recommandées qui doivent être appliquées dans le [sys.dm_db_tuning_recommendations &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md) vue. La vue affiche des informations sur le problème, l’importance du problème et des détails tels que la requête identifiée, l’ID du plan régressé, l’ID du plan qui a été utilisé comme base de référence pour la comparaison et le [!INCLUDE[tsql_md](../../includes/tsql-md.md)] instruction qui peut être exécutée pour corriger le problème.

| Type | description | DATETIME | score | détails | ... |
| --- | --- | --- | --- | --- | --- |
| `FORCE_LAST_GOOD_PLAN` | Temps processeur a été remplacée par 4 ms à 14 ms | 3/17/2017 | 83 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |
| `FORCE_LAST_GOOD_PLAN` | Temps processeur passé de 37 ms à 84 ms | 3/16/2017 | 26 | `queryId` `recommendedPlanId` `regressedPlanId` `T-SQL` |   |

Certaines colonnes de cette vue sont décrits dans la liste suivante :
 - Type de l’action recommandée- `FORCE_LAST_GOOD_PLAN`
 - Description qui contient des informations pourquoi [!INCLUDE[ssde_md](../../includes/ssde_md.md)] pense que ce changement de plan est une régression des performances potentielles
 - Date et heure de la régression potentielle est détectée.
 - Score de cette recommandation
 - Pour plus d’informations sur les problèmes tels que l’ID du plan détecté, ID du plan régressé, ID du plan qui doit être forcé pour résoudre le problème, [!INCLUDE[tsql_md](../../includes/tsql-md.md)] script qui peut-être être appliquée pour résoudre le problème, etc. Sont stockés les détails [au format JSON](../../relational-databases/json/index.md)

Utilisez la requête suivante pour obtenir un script qui résout le problème et des informations supplémentaires sur l’estimation bénéficiez :

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

| reason | score | script | requête\_id | plan actuel\_id | recommandé plan\_id | estimé\_obtenir | erreur\_susceptibles d’engendrer des
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Temps processeur a été remplacée par 3 ms à 46 ms | 36 | EXEC sp\_requête\_stocker\_forcer\_plan 12, 17 ; | 12 | 28 | 17 | 11.59 | 0

`estimated_gain` représente le nombre estimé de secondes qui seraient enregistrés si le plan recommandé serait exécuté au lieu du plan actuel. Le plan recommandé doit être forcé au lieu du plan actuel si le gain est supérieur à 10 secondes. S’il existe plus d’erreurs (par exemple, les délais d’attente ou les exécutions abandonnées) dans le plan actuel que dans l’architecture recommandée plan, la colonne `error_prone` est défini sur la valeur `YES`. Plan susceptibles d’engendrer des erreurs est une autre raison, pourquoi le plan recommandé doit être forcé plutôt que celui en cours.

Bien que [!INCLUDE[ssde_md](../../includes/ssde_md.md)] fournit toutes les informations requises pour identifier les régressions de choix de plan ; continue surveillance et la résolution des problèmes de performances peuvent être un processus fastidieux. Le réglage automatique rend ce processus est beaucoup plus facile.

> [!NOTE]
> Les données dans la vue de gestion dynamique sys.dm_db_tuning_recommendations ne sont pas conservées entre les redémarrages de le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.

## <a name="automatic-index-management"></a>Gestion automatique des index

Dans [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)], gestion de l’index est facile, car [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] a eu connaissance de votre charge de travail et garantit que vos données sont toujours de façon optimale indexées. Conception d’index doit être correctement est essentielle pour optimiser les performances de votre charge de travail, et la gestion automatique des index peut vous aider à optimiser vos index. Gestion automatique des index peut résoudre les problèmes de performances dans les bases de données indexées de manière incorrecte, ou mettre à jour et améliorez les index sur le schéma de base de données existante. Le réglage automatique dans [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] effectue les actions suivantes :

 - Identifie les index qui peut améliorer les performances de votre [!INCLUDE[tsql_md](../../includes/tsql-md.md)] requêtes qui lisent les données à partir des tables.
 - Identifie les index redondants ou les index qui n’ont pas été utilisés dans une longue période de temps qui a pu être supprimé. Suppression d’index inutiles améliore les performances des requêtes qui mettent à jour des données dans des tables.

### <a name="why-do-you-need-index-management"></a>Pourquoi devez-vous gestion des index ?

Les index accélèrent certaines de vos requêtes qui lisent les données à partir des tables ; Cependant, ils peuvent ralentir les requêtes qui mettent à jour des données. Vous devez analyser soigneusement quand créer un index et les colonnes que vous devez inclure dans l’index. Certains index ne peut pas être nécessaire après un certain temps. Par conséquent, vous devez régulièrement identifier et supprimer les index qui n’apportent aucun avantage. Si vous ignorez les index inutilisés, performances des requêtes qui mettent à jour de données diminuent sans aucun avantage pour les requêtes qui lisent les données. Les index inutilisés affectent également les performances globales du système, car les mises à jour supplémentaires impliquent une journalisation inutile.

Recherche de l’ensemble optimal d’index qui améliore les performances des requêtes qui lisent des données à partir de vos tables et ont un impact minimal sur les mises à jour peut nécessiter l’analyse continue complexe.

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] utilise l’intelligence intégrée et des règles avancées pour analyser vos requêtes, identifier les index qui seraient optimaux pour vos charges de travail actuels, et les index peuvent être supprimés. Base de données SQL Azure permet de s’assurer que vous disposez d’un ensemble minimal nécessaire d’index qui optimisent les requêtes qui lisent les données, avec un impact réduit sur les autres requêtes.

### <a name="automatic-index-management"></a>Gestion automatique des index

En plus de détection, [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] peuvent appliquer automatiquement les recommandations identifiées. Si vous trouvez que les règles intégrées améliorent les performances de votre base de données, vous pouvez laisser [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] gérer automatiquement vos index.

Pour activer le réglage automatique [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] et autoriser la fonctionnalité de réglage automatique entièrement gérer votre charge de travail, consultez [activer le réglage automatique dans Azure SQL Database à l’aide du portail Azure](/azure/sql-database/sql-database-automatic-tuning-enable).

Lorsque le [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] applique une recommandation CREATE INDEX ou DROP INDEX, il surveille automatiquement les performances des requêtes qui sont affectés par l’index. Nouvel index est conservé uniquement si les performances des requêtes concernées sont améliorées. L’index supprimé sera automatiquement recréé s’il existe certaines requêtes qui s’exécutent plus lentement en raison de l’absence de l’index.

### <a name="automatic-index-management-considerations"></a>Considérations sur la gestion automatique des index

Actions requises pour créer les index nécessaires dans [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] peut consommer des ressources et affecter temporairement les performances de la charge de travail. Pour minimiser l’impact de la création d’index sur les performances de la charge de travail, [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] recherche la fenêtre de temps approprié pour toute opération de gestion d’index. Action de réglage est reporté à plus tard si la base de données a besoin de ressources pour l’exécution de votre charge de travail et démarré lors de la base de données dispose de suffisamment les ressources inutilisées qui peuvent être utilisées pour la tâche de maintenance. Une fonctionnalité importante dans la gestion automatique des index est une vérification des actions. Lorsque [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] crée ou supprime des index, un processus de surveillance analyse les performances de votre charge de travail pour vérifier que l’action amélioré les performances. Si elle n’a pas d’apporter une amélioration significative : l’action est immédiatement annulée. De cette façon, [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] garantit que les actions automatiques n’affectent pas négativement les performances de votre charge de travail. Index créés par le réglage automatique sont transparents pour l’opération de maintenance sur le schéma sous-jacent. Modifications de schéma tels que déplacer ou renommer des colonnes ne sont pas bloquées par la présence d’index créés automatiquement. Les index sont créés automatiquement par [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] sont immédiatement supprimés lorsque liés de table ou colonnes est supprimée.

### <a name="alternative---manual-index-management"></a>Autre possibilité : gestion d’index manuelles

Sans la gestion automatique des index, il devra interroger manuellement [sys.dm_db_missing_index_details &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md) afficher ou utiliser le rapport de tableau de bord performances dans [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] aux index de recherche peuvent améliorer les performances, de créer des index en utilisant les informations fournies dans cette vue et d’analyser manuellement les performances de la requête. Afin de trouver les index qui doivent être supprimés, les utilisateurs doivent analyser les statistiques d’utilisation opérationnelle des index aux index de recherche rarement utilisée.

[!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] simplifie ce processus. [!INCLUDE[ssazure_md](../../includes/ssazure_md.md)] analyse votre charge de travail, identifie les requêtes qui pourraient s’exécuter plus rapidement avec un nouvel index et identifie les index inutilisés ou dupliqués. Plus d’informations sur l’identification des index qui doit être modifié à [trouver des recommandations d’index dans le portail Azure](https://docs.microsoft.com/azure/sql-database/sql-database-advisor-portal).

## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys.database_automatic_tuning_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-automatic-tuning-options-transact-sql.md)  
 [Sys.dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 [sys.dm_db_missing_index_details &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [sp_query_store_force_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)     
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)           
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [Fonctions JSON](../../relational-databases/json/index.md)    
 [Plans d’exécution](../../relational-databases/performance/execution-plans.md)    
 [Surveiller et régler les performances](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [Outils de surveillance et d’optimisation des performances](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [Analyse des performances à l'aide du magasin de requêtes](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
 [Assistant Paramétrage de requête](../../relational-databases/performance/upgrade-dbcompat-using-qta.md)
