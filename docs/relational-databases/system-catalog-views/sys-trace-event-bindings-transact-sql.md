---
description: sys.trace_event_bindings (Transact-SQL)
title: sys. trace_event_bindings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.trace_event_bindings_TSQL
- trace_event_bindings
- sys.trace_event_bindings
- trace_event_bindings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_event_bindings catalog view
ms.assetid: 22f534e1-4ed6-4b3e-9ead-1d1001a1b0f5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a1e9410664022a19b731d0d06e082dc8d15187a4
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544959"
---
# <a name="systrace_event_bindings-transact-sql"></a>sys.trace_event_bindings (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  L’affichage catalogue **sys. trace_event_bindings** contient une liste de toutes les combinaisons possibles d’utilisation d’événements et de colonnes. Pour chaque événement répertorié dans la colonne **trace_event_id** , toutes les colonnes disponibles sont répertoriées dans la colonne **trace_column_id** . Toutes les colonnes disponibles ne sont pas remplies chaque fois qu'un événement donné se produit. Ces valeurs ne changent pas pour une version donnée de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Pour obtenir la liste complète des événements de trace pris en charge, consultez [SQL Server référence](../../relational-databases/event-classes/sql-server-event-class-reference.md)de la classe d’événements.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt les affichages catalogue des événements étendus.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**trace_event_id**|**smallint**|ID de l'événement de trace. Cette colonne se trouve également dans l’affichage catalogue **sys. trace_events** .|  
|**trace_column_id**|**smallint**|ID de la colonne de trace. Cette colonne se trouve également dans l’affichage catalogue **sys. trace_columns** .|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys. traces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys. trace_categories &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys. trace_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys. trace_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys. trace_subclass_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
