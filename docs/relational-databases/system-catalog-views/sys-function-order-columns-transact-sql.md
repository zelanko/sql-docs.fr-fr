---
title: Sys.function_order_columns (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- function_order_columns
- sys.function_order_columns_TSQL
- function_order_columns_TSQL
- sys.function_order_columns
dev_langs: TSQL
helpviewer_keywords: sys.function_order_columns catalog view
ms.assetid: 29287973-3125-4d35-8ca9-92cb45828854
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 151d91a53092b9303f576d5b650abdc71a797039
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysfunctionordercolumns-transact-sql"></a>sys.function_order_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne par colonne qui fait partie d’un **commande** expression d’une fonction table de Common language runtime (CLR).  

  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID de l'objet (fonction table CLR) sur lequel l'ordre est défini.|  
|**order_column_id**|**int**|ID de la colonne d'ordre. **order_column_id** est unique seulement dans **object_id**.<br /><br /> **order_column_id** représente la position de cette colonne dans l’ordre.|  
|**column_id**|**int**|ID de la colonne dans **object_id**.<br /><br /> **column_id** est unique seulement dans **object_id**.|  
|**is_descending par**|**bit**|1 = colonne d'ordre avec un ordre de tri descendant.<br /><br /> 0 = colonne d'ordre avec un ordre de tri ascendant.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
