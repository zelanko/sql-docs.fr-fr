---
title: sys.fulltext_system_stopwords (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.fulltext_system_stopwords_TSQL
- fulltext_system_stopwords
- fulltext_system_stopwords_TSQL
- sys.fulltext_system_stopwords
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- sys.fulltext_system_stopwords catalog view
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 487de53f-c637-4d78-85f6-fef5e768cd0c
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8c29e615afbaf86d9311fa2c4c3d35f3d6b00660
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysfulltextsystemstopwords-transact-sql"></a>sys.fulltext_system_stopwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Fournit l'accès à la liste de mots vides système.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**stopword**|**nvarchar(64)**|Terme considéré pour une correspondance de mot vide.|  
|**language_id**|**int**|Identificateur des paramètres régionaux (LCID) de la langue. Ce LCID est utilisé pour l'analyse lexicale.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)   
 [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)  
  
  
