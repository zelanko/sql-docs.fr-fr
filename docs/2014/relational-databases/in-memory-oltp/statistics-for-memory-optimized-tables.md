---
title: Statistiques pour les tables optimisées en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e644766d-1d1c-43d7-83ff-8ccfe4f3af9f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1a15c617c2be877c19d447d615261a6d38eae9eb
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718948"
---
# <a name="statistics-for-memory-optimized-tables"></a>Statistiques pour les tables optimisées en mémoire
  L'optimiseur de requête utilise des statistiques sur les colonnes dans l'optique de créer des plans de requête qui améliorent les performances des requêtes. Les statistiques sont collectées dans les tables de la base de données et stockées dans les métadonnées de la base de données.  
  
 Les statistiques sont créées automatiquement, mais elles peuvent également être créées manuellement. Par exemple, des statistiques sont créées automatiquement pour les colonnes clés d'index lorsque l'index est créé. Pour plus d'informations sur la création de statistiques, consultez [Statistics](../statistics/statistics.md).  
  
 Les données de table sont généralement modifiées au fil du temps, à mesure que des lignes sont insérées, mises à jour et supprimées. Cela signifie que les statistiques doivent être mises à jour régulièrement. Par défaut, les statistiques sur les tables sur disque sont mises à jour automatiquement lorsque l'optimiseur détermine qu'elles sont obsolètes.  
  
 Les statistiques sur les tables mémoire optimisées ne sont pas mises à jour par défaut. Vous devez les mettre à jour manuellement. Utilisez [update statistics &#40;&#41;Transact-SQL](/sql/t-sql/statements/update-statistics-transact-sql) pour des colonnes, des index ou des tables individuels. Utilisez [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) pour mettre à jour les statistiques de toutes les tables utilisateur et internes de la base de données.  
  
 Lorsque vous utilisez [create statistics &#40;Transact-sql&#41;](/sql/t-sql/statements/create-statistics-transact-sql) ou [UPDATE statistics &#40;&#41;Transact-SQL ](/sql/t-sql/statements/update-statistics-transact-sql), vous devez spécifier la `NORECOMPUTE` désactivation de la mise à jour automatique des statistiques pour les tables optimisées en mémoire. Pour les tables sur disque, [sp_updatestats &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) met à jour les statistiques uniquement si la table a été modifiée depuis la dernière [sp_updatestats &#40;transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql). Pour les tables optimisées en mémoire, [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) génère toujours des statistiques mises à jour. [sp_updatestats &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql) est une bonne option pour les tables optimisées en mémoire ; dans le cas contraire, vous devez connaître les tables qui ont des modifications importantes pour pouvoir mettre à jour les statistiques individuellement.  
  
 Les statistiques peuvent être générées lors de l'échantillonnage des données ou d'une analyse complète. Les statistiques échantillonnées n'utilisent qu'un échantillon des données de la table pour estimer la distribution des données. Les statistiques d'analyse complète analysent la table entière pour déterminer la distribution des données. Les statistiques d'analyse complète sont généralement plus précises, mais prennent plus temps pour le calcul. Les statistiques échantillonnées sont collectées plus rapidement.  
  
 Par défaut, les tables sur disque utilisent des statistiques échantillonnées. Les tables mémoire optimisées prennent uniquement en charge les statistiques d'analyse complète. Lorsque vous utilisez [create statistics &#40;Transact-sql&#41;](/sql/t-sql/statements/create-statistics-transact-sql) ou [UPDATE statistics &#40;&#41;Transact-SQL ](/sql/t-sql/statements/update-statistics-transact-sql), vous devez spécifier l' `FULLSCAN` option pour les tables mémoire optimisées.  
  
 Considérations supplémentaires pour les statistiques sur les tables mémoire optimisées :  
  
-   Les index sur les tables mémoire optimisées sont créés avec la table. Les statistiques sur les colonnes clés d'index sont créées lorsque la table est vide. Par conséquent, ces statistiques doivent être mises à jour après que les données ont été chargées dans la table.  
  
-   Pour les procédures stockées compilées en mode natif, les plans d'exécution de requêtes dans la procédure sont optimisés lorsque la procédure est compilée. Cela se produit uniquement lorsque la procédure est créée et au redémarrage du serveur, et non pas lorsque les statistiques sont mises à jour. Par conséquent, les tables doivent contenir un jeu représentatif de données et les statistiques doivent être à jour avant de pouvoir créer les procédures. (Les procédures stockées compilées en mode natif sont recompilées si la base de données est mise hors connexion, puis remise en ligne, ou en cas de redémarrage du serveur.)  
  
## <a name="guidelines-for-statistics-when-deploying-memory-optimized-tables"></a>Instructions relatives aux statistiques lors du déploiement de tables mémoire optimisées  
 Pour garantir que l'optimiseur de requête dispose de statistiques à jour lorsque vous créez des plans de requête, déployez les tables mémoire optimisées à l'aide de ces cinq étapes :  
  
1.  Créez des tables et des index. Les index sont spécifiés inline dans les instructions `CREATE TABLE`.  
  
2.  Chargez des données dans les tables.  
  
3.  Mettez à jour les statistiques des tables.  
  
4.  Créez des procédures stockées qui accèdent aux tables.  
  
5.  Exécutez la charge de travail, qui peut contenir des procédures stockées [!INCLUDE[tsql](../../../includes/tsql-md.md)] interprétées et compilées en mode natif, ainsi que des traitements ad hoc.  
  
 La création de procédures stockées compilées en mode natif après que vous avez chargé les données et mis à jour les statistiques garantit que l'optimiseur dispose de statistiques pour les tables mémoire optimisées. De cette façon, les plans de requête sont efficaces lorsque la procédure est compilée.  
  
## <a name="guidelines-for-maintaining-statistics-on-memory-optimized-tables"></a>Instructions relatives à la gestion des statistiques de tables mémoire optimisées  
 Pour conserver les statistiques à jour, mettez régulièrement à jour les statistiques de tables mémoire optimisées.  
  
 Si les données sont modifiées fréquemment, mettez à jour les statistiques fréquemment. Par exemple, mettez à jour les statistiques de tables après une mise à jour par lot. Après avoir mis à jour les statistiques, supprimez et recréez les procédures stockées compilées en mode natif de façon à ce qu'elles puissent tirer parti des statistiques mises à jour.  
  
 .  
  
 Ne mettez pas à jour les statistiques au cours d'une charge importante.  
  
 Pour mettre à jour les statistiques :  
  
-   Utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour [Create a Maintenance Plan](../maintenance-plans/create-a-maintenance-plan.md) avec une [tâche de mise à jour des statistiques](../maintenance-plans/update-statistics-task-maintenance-plan.md)  
  
-   Ou mettez à jour les statistiques au moyen d'un script [!INCLUDE[tsql](../../../includes/tsql-md.md)] , tel que l'indique la section suivante.  
  
 Pour mettre à jour les statistiques d'une seule table mémoire optimisée (*myschema*. *Mytable*), exécutez le script suivant :  
  
```  
UPDATE STATISTICS myschema.Mytable WITH FULLSCAN, NORECOMPUTE  
```  
  
 Pour mettre à jour les statistiques de toutes les tables mémoire optimisées dans la base de données active, exécutez le script suivant :  
  
```sql  
DECLARE @sql NVARCHAR(MAX) = N''  
  
SELECT @sql += N'  
   UPDATE STATISTICS ' + quotename(schema_name(schema_id)) + N'.' + quotename(name) + N' WITH FULLSCAN, NORECOMPUTE'  
FROM sys.tables WHERE is_memory_optimized=1  
  
EXEC sp_executesql @sql  
```  
  
 Pour mettre à jour les statistiques de toutes les tables de la base de données, exécutez [sp_updatestats &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-updatestats-transact-sql).  
  
 Les exemples suivants indiquent quand les statistiques sur les tables mémoire optimisées ont été mises à jour pour la dernière fois. Ces informations peuvent vous aider à décider si vous devez mettre à jour les statistiques.  
  
```sql  
select t.object_id, t.name, sp.last_updated as 'stats_last_updated'  
from sys.tables t join sys.stats s on t.object_id=s.object_id cross apply sys.dm_db_stats_properties(t.object_id, s.stats_id) sp  
where t.is_memory_optimized=1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tables à mémoire optimisée](memory-optimized-tables.md)  
  
  
