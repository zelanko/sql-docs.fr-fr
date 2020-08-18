---
description: DDL, fonctions, procédures stockées et vues de recherche sémantique
title: DDL, fonctions, procédures stockées et vues de recherche sémantique
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], database objects
ms.assetid: 182f395f-3168-48a4-b723-ef4403544f9f
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.custom: seo-lt-2019
ms.openlocfilehash: 8564c0f0a5dcd83a434743281c85b3524fa06d10
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88325784"
---
# <a name="semantic-search-ddl-functions-stored-procedures-and-views"></a>DDL, fonctions, procédures stockées et vues de recherche sémantique
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Répertorie les instructions Transact-SQL et les objets de base de données qui prennent en charge la recherche sémantique statistique dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour obtenir la liste des objets de base de données qui prennent en charge la recherche en texte intégral, consultez [DDL, fonctions, procédures stockées et vues de recherche en texte intégral](../../relational-databases/search/full-text-search-ddl-functions-stored-procedures-and-views.md).  
  
##  <a name="data-definition-language-ddl-statements"></a><a name="ddl"></a> Instructions DDL (Data Definition Language)  
  
|Object|Informations complémentaires|  
|------------|----------------------|  
|[ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)|[Activer la recherche sémantique sur les tables et les colonnes](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-index-transact-sql.md)|[Activer la recherche sémantique sur les tables et les colonnes](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
  
##  <a name="system-functions"></a><a name="func"></a> Fonctions système  
  
|Object|Informations complémentaires|  
|------------|----------------------|  
|[semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)|[Rechercher des expressions clés dans les documents avec la recherche sémantique](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md)|  
|[semanticsimilaritydetailstable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md)|[Rechercher des documents similaires ou connexes avec la recherche sémantique](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)|  
|[semanticsimilaritytable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md)|[Rechercher des documents similaires ou connexes avec la recherche sémantique](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)|  
  
##  <a name="system-metadata-functions"></a><a name="meta"></a> Fonctions de métadonnées système  
  
|Object|Informations complémentaires|  
|------------|----------------------|  
|[COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)|[Activer la recherche sémantique sur les tables et les colonnes](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)|[Activer la recherche sémantique sur les tables et les colonnes](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)|[Gérer et surveiller la recherche sémantique](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)|[Gérer et surveiller la recherche sémantique](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)|[Activer la recherche sémantique sur les tables et les colonnes](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)|  
|[SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)|[Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md)|  
  
##  <a name="system-stored-procedures"></a><a name="sproc"></a> Procédures stockées système  
  
|Object|Informations complémentaires|  
|------------|----------------------|  
|[sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql.md)|[Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md)|  
|[sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql.md)|[Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md)|  
  
##  <a name="catalog-views"></a><a name="cv"></a> Affichages catalogue  
  
|Object|Informations complémentaires|  
|------------|----------------------|  
|[sys.fulltext_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)|[Gérer et surveiller la recherche sémantique](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)|[Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md)|  
|[sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql.md)|[Installer et configurer la recherche sémantique](../../relational-databases/search/install-and-configure-semantic-search.md)|  
  
##  <a name="dynamic-management-views"></a><a name="dmv"></a> Vues de gestion dynamique  
  
|Object|Informations complémentaires|  
|------------|----------------------|  
|[sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)|[Gérer et surveiller la recherche sémantique](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)|[Gérer et surveiller la recherche sémantique](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
|[sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)|[Gérer et surveiller la recherche sémantique](../../relational-databases/search/manage-and-monitor-semantic-search.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer et surveiller la recherche sémantique](../../relational-databases/search/manage-and-monitor-semantic-search.md)  
  
  
