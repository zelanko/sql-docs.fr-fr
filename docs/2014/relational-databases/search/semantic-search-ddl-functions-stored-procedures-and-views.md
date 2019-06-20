---
title: DDL, fonctions, procédures stockées et vues de recherche sémantique | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], database objects
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ee5cf7136739b012615121e00d8b8d3ed7c7c6ff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66011034"
---
# <a name="semantic-search-ddl-functions-stored-procedures-and-views"></a>DDL, fonctions, procédures stockées et vues de recherche sémantique
  Répertorie les instructions Transact-SQL et les objets de base de données qui prennent en charge la recherche sémantique statistique dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour obtenir la liste des objets de base de données qui prennent en charge la recherche en texte intégral, consultez [DDL, fonctions, procédures stockées et vues de recherche en texte intégral](../views/views.md).  
  
##  <a name="ddl"></a> Instructions DDL (Data Definition Language, langage de définition de données) Transact-SQL  
  
|Object|Informations supplémentaires|  
|------------|----------------------|  
|[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)|[Activer la recherche sémantique sur les tables et les colonnes](enable-semantic-search-on-tables-and-columns.md)|  
|[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)|[Activer la recherche sémantique sur les tables et les colonnes](enable-semantic-search-on-tables-and-columns.md)|  
  
##  <a name="func"></a> Fonctions système  
  
|Object|Informations supplémentaires|  
|------------|----------------------|  
|[semantickeyphrasetable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semantickeyphrasetable-transact-sql)|[Rechercher des expressions clés dans les documents avec la recherche sémantique](find-key-phrases-in-documents-with-semantic-search.md)|  
|[semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql)|[Rechercher des documents similaires ou connexes avec la recherche sémantique](find-similar-and-related-documents-with-semantic-search.md)|  
|[semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql)|[Rechercher des documents similaires ou connexes avec la recherche sémantique](find-similar-and-related-documents-with-semantic-search.md)|  
  
##  <a name="meta"></a> Fonctions de métadonnées système  
  
|Object|Informations supplémentaires|  
|------------|----------------------|  
|[COLUMNPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/columnproperty-transact-sql)|[Activer la recherche sémantique sur les tables et les colonnes](enable-semantic-search-on-tables-and-columns.md)|  
|[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql)|[Activer la recherche sémantique sur les tables et les colonnes](enable-semantic-search-on-tables-and-columns.md)|  
|[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|[Gérer et surveiller la recherche sémantique](manage-and-monitor-semantic-search.md)|  
|[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql)|[Gérer et surveiller la recherche sémantique](manage-and-monitor-semantic-search.md)|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql)|[Activer la recherche sémantique sur les tables et les colonnes](enable-semantic-search-on-tables-and-columns.md)|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)|[Installer et configurer la recherche sémantique](install-and-configure-semantic-search.md)|  
  
##  <a name="sproc"></a> Procédures stockées système  
  
|Object|Informations supplémentaires|  
|------------|----------------------|  
|[sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql)|[Installer et configurer la recherche sémantique](install-and-configure-semantic-search.md)|  
|[sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql)|[Installer et configurer la recherche sémantique](install-and-configure-semantic-search.md)|  
  
##  <a name="cv"></a> Vues système - Affichages catalogue  
  
|Object|Informations supplémentaires|  
|------------|----------------------|  
|[sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)|[Gérer et surveiller la recherche sémantique](manage-and-monitor-semantic-search.md)|  
|[sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql)|[Installer et configurer la recherche sémantique](install-and-configure-semantic-search.md)|  
|[sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)|[Installer et configurer la recherche sémantique](install-and-configure-semantic-search.md)|  
  
##  <a name="dmv"></a> Vues système – Vues de gestion dynamique  
  
|Object|Informations supplémentaires|  
|------------|----------------------|  
|[sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql)|[Gérer et surveiller la recherche sémantique](manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_index_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql)|[Gérer et surveiller la recherche sémantique](manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql)|[Gérer et surveiller la recherche sémantique](manage-and-monitor-semantic-search.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer et surveiller la recherche sémantique](manage-and-monitor-semantic-search.md)  
  
  
