---
title: Gérer et surveiller la recherche sémantique | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], managing
- semantic search [SQL Server], monitoring
ms.assetid: eb5c3b29-da70-42aa-aa97-7d35a3f1eb98
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1d68b9452a03c127fe39018c19abab1073dae7c5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046121"
---
# <a name="manage-and-monitor-semantic-search"></a>Gérer et surveiller la recherche sémantique
  Décrit le processus d'indexation sémantique et les tâches associées à la gestion et au contrôle des index.  
  
##  <a name="HowToMonitorStatus"></a> Comment : Vérifier l’état de l’indexation sémantique  
 **La première phase de l’indexation sémantique est terminée ?**  
 Interrogez la vue de gestion dynamique, [sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql), et vérifiez les colonnes **status** et **status_description**.  
  
 La première phase de l'indexation inclut l'alimentation de l'index de mots clés de recherche en texte intégral et de l'index d'expressions clés sémantiques, ainsi que l'extraction de données de ressemblance de document.  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_index_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
 **La deuxième phase de l’indexation sémantique est terminée ?**  
 Interrogez la vue de gestion dynamique, [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql), et vérifiez les colonnes **status** et **status_description**.  
  
 La deuxième phase de l'indexation inclut l'alimentation de l'index de ressemblance de document sémantique.  
  
```wql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_fts_semantic_similarity_population WHERE table_id = OBJECT_ID('table_name')  
GO  
```  
  
##  <a name="HowToCheckSize"></a> Comment : Vérifiez la taille des index sémantiques  
 **Quelle est la taille logique d’un index d’expressions clés sémantiques ou d’un index de ressemblance de document sémantique ?**  
 Interrogez la vue de gestion dynamique, [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql).  
  
 La taille logique est affichée en nombre de pages d'index.  
  
```sql  
USE database_name  
GO  
  
SELECT * FROM sys.dm_db_fts_index_physical_stats WHERE object_id = OBJECT_ID('table_name')  
GO  
```  
  
 **Qu’est la taille totale des index sémantiques et de recherche en texte intégral pour un catalogue de texte intégral ?**  
 Interrogez la propriété **IndexSize** de la fonction de métadonnées [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql).  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'IndexSize')  
GO  
```  
  
 **Combien d’éléments est indexés dans les index de recherche en texte intégral et sémantiques pour un catalogue de texte intégral ?**  
 Interrogez la propriété **ItemCount** de la fonction de métadonnées [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql).  
  
```sql  
SELECT FULLTEXTCATALOGPROPERTY('catalog_name', 'ItemCount')  
GO  
```  
  
##  <a name="HowToForcePopulation"></a> Comment : Imposer l’alimentation des index sémantiques  
 Vous pouvez forcer le remplissage des index sémantiques et de recherche en texte intégral à l'aide de la clause START/STOP/PAUSE ou RESUME POPULATION avec la même syntaxe et le même comportement que ceux décrits pour les index de recherche en texte intégral. Pour plus d’informations, consultez [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql) et [Alimenter des index de recherche en texte intégral](../indexes/indexes.md).  
  
 Étant donné que l'indexation sémantique dépend de l'indexation de texte intégral, les index sémantiques ne sont remplis que lorsque les index de recherche en texte intégral associés le sont également.  
  
 **Exemple : Démarrer un remplissage complet des index sémantiques et de recherche en texte intégral**  
  
 L’exemple suivant démarre une alimentation complète des index sémantiques et de recherche en texte intégral en modifiant un index de recherche en texte intégral existant sur la table **Production.Document** dans l’exemple de base de données AdventureWorks2012.  
  
```vb  
USE AdventureWorks2012  
GO  
  
ALTER FULLTEXT INDEX ON Production.Document  
    START FULL POPULATION  
GO  
```  
  
##  <a name="HowToDisableIndexing"></a> Comment : Désactiver ou réactiver l’indexation sémantique  
 Vous pouvez activer ou désactiver l'indexation sémantique ou de texte intégral à l'aide de la clause ENABLE/DISABLE avec la même syntaxe et le même comportement que ceux décrits pour les index de recherche en texte intégral. Pour plus d’informations, consultez [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql).  
  
 Lorsque l'indexation sémantique est désactivée et suspendue, les requêtes sur les données sémantiques continuent de s'exécuter avec succès et retournent des données indexées précédemment. Ce comportement n'est pas cohérent avec le comportement de la recherche en texte intégral.  
  
```sql  
-- To disable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name DISABLE  
GO  
  
-- To re-enable semantic indexing on a table  
USE database_name  
GO  
  
ALTER FULLTEXT INDEX ON table_name ENABLE  
GO  
```  
  
##  <a name="SemanticIndexing"></a> Phases d’indexation sémantique  
 Une recherche sémantique indexe deux types de données pour chaque colonne sur laquelle elle est activée :  
  
1.  **Expressions clés**  
  
2.  **Ressemblance de document**  
  
 L'indexation sémantique se produit en deux phases, conjointement à l'indexation de texte intégral :  
  
1.  **Phase 1**. L'index de mots clés de texte intégral et l'index d'expressions clés sémantiques sont remplis en même temps, en parallèle. Les données requises pour indexer la ressemblance de document sont également extraites à ce moment.  
  
2.  **Phase 2**. L'index de ressemblance de document sémantique est rempli à son tour. Cet index dépend des deux index remplis à la phase précédente.  
  
##  <a name="BestPracticeUnderstand"></a>   
##  <a name="ProblemNotPopulated"></a> Problème : Les index sémantiques ne sont pas remplis  
 **Les index de recherche en texte intégral associés sont remplis ?**  
 Étant donné que l'indexation sémantique dépend de l'indexation de texte intégral, les index sémantiques ne sont remplis que lorsque les index de recherche en texte intégral associés le sont également.  
  
 **Sont la recherche en texte intégral et la recherche sémantique installées et configurées correctement ?**  
 Pour plus d’informations, consultez [Installer et configurer la recherche sémantique](install-and-configure-semantic-search.md).  
  
 **Le FDHOST service n’est pas disponible, ou existe-t-il une autre condition qui provoquerait l’indexation de texte intégral pour la restauration ?**  
 Pour plus d’informations, consultez [Résoudre l’indexation de recherche en texte intégral](troubleshoot-full-text-indexing.md).  
  
  
