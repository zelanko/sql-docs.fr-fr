---
title: sys. all_views (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.all_views_TSQL
- sys.all_views
- all_views
- all_views_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.all_views catalog view
ms.assetid: d8829213-fce2-41c6-9ab2-aaab5836c941
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8931b3885df642fc4fbd076b18c4375a48c2b32b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001302"
---
# <a name="sysall_views-transact-sql"></a>sys.all_views (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Affiche l'UNION de toutes les vues définies par l'utilisateur et les vues système.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**\<colonnes héritées>**||Pour obtenir la liste des colonnes héritées par cette vue, consultez [sys. objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**is_replicated**|**bit**|1 = La vue est répliquée.|  
|**has_replication_filter**|**bit**|1 = La vue comporte un filtre de réplication.|  
|**has_opaque_metadata**|**bit**|1 = L'option VIEW_METADATA est spécifiée pour la vue. Pour plus d’informations, consultez [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md).|  
|**has_unchecked_assembly_data**|**bit**|1 = La table contient des données persistantes qui dépendent d'un assembly dont la définition a été modifiée lors de la dernière exécution de ALTER ASSEMBLY. Est réinitialisé à 0 après la dernière instruction DBCC CHECKDB ou DBCC CHECKTABLE réussie.|  
|**with_check_option**|**bit**|1 = WITH CHECK OPTION est spécifié dans la définition de la vue.|  
|**is_date_correlation_view**|**bit**|1 = Le système a créé automatiquement la vue pour stocker les informations de corrélation entre les colonnes de date/heure (datetime). La création de cette vue a été activée en affectant la valeur **on**à DATE_CORRELATION_OPTIMIZATION.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)   
 [ALTER ASSEMBLy &#40;Transact-SQL&#41;](../../t-sql/statements/alter-assembly-transact-sql.md)   
 [DBCC CHECKTABLE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)  
  
  
