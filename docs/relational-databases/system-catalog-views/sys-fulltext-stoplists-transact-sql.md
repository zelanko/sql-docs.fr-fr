---
title: sys.fulltext_stoplists (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_stoplists
- sys.fulltext_stoplists_TSQL
- fulltext_stoplists_TSQL
- fulltext_stoplists
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- sys.fulltext_stoplists catalog view
- stopwords [full-text search]
ms.assetid: eb69fb8f-f6d9-446e-83c0-67afd05dfba0
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 88f4354a343e9748e1111d26c3ce8c248431b1be
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68133771"
---
# <a name="sysfulltextstoplists-transact-sql"></a>sys.fulltext_stoplists (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contient une ligne par liste de mots vides de texte intégral dans la base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**stoplist_id**|**Int**|ID de la liste de mots vides ; il est unique dans la base de données.|  
|**name**|**sysname**|Nom de la liste de mots vides.|  
|**create_date**|**datetime**|Date de création de la liste de mots vides.|  
|**modify_date**|**datetime**|Date de dernière modification de la liste de mots vides au moyen d'une instruction ALTER.|  
|**Principal_id**|**Int**|ID du principal de la base de données propriétaire de la liste de mots vides.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.fulltext_system_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-system-stopwords-transact-sql.md)   
 [sys.fulltext_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)   
 [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-stoplist-transact-sql.md)  
  
  
