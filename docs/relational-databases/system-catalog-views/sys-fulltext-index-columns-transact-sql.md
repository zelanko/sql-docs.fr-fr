---
title: sys.fulltext_index_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_index_columns
- fulltext_index_columns
- sys.fulltext_index_columns_TSQL
- fulltext_index_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text indexes [SQL Server], columns
- sys.fulltext_index_columns catalog view
- full-text indexes [SQL Server], properties
ms.assetid: c34b8625-e53c-4281-ace6-d46230d5cb84
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9c139a45df1031ac47750d995780f8e13ea64f2c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68133812"
---
# <a name="sysfulltextindexcolumns-transact-sql"></a>sys.fulltext_index_columns (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contient une ligne pour chaque colonne qui fait partie d'un index de recherche en texte intégral.    
 
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|ID de l'objet dont celui-ci fait partie.|  
|**column_id**|**int**|ID de la colonne qui fait partie de l'index de texte intégral.|  
|**type_column_id**|**int**|ID de la colonne de type qui stocke le document fourni par l’utilisateur fichier extension-« .doc », « .xls » et ainsi de suite du document dans une ligne donnée. La colonne de type est spécifiée uniquement pour les colonnes dont les données requièrent un filtrage pendant l'indexation de texte intégral. NULL si non applicable. Pour plus d’informations, consultez [Configurer et gérer les extensions analytiques avancées](../../relational-databases/search/configure-and-manage-filters-for-search.md).|  
|**language_id**|**Int**|LCID de langue dont l'analyseur lexical est utilisé pour indexer cette colonne de texte intégral.<br /><br /> 0 = Neutre<br /><br /> Pour plus d’informations, consultez [sys.fulltext_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).|  
|**statistical_semantics**|**int**|1 = L'indexation sémantique statistique est activée pour cette colonne, en plus de l'indexation de texte intégral.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
