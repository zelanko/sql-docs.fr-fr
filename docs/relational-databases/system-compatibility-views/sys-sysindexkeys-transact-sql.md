---
title: Sys.sysindexkeys (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysindexkeys
- sys.sysindexkeys_TSQL
- sysindexkeys_TSQL
- sys.sysindexkeys
dev_langs:
- TSQL
helpviewer_keywords:
- sysindexkeys system table
- sys.sysindexkeys compatibility view
ms.assetid: 53a33c8d-e5f0-430d-a712-b65f43d64318
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d920d557ada0015bae0d7f242d2d11f7533909ec
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="syssysindexkeys-transact-sql"></a>sys.sysindexkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient des informations sur les clés ou les colonnes dans un index de la base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID de la table.|  
|**indid**|**smallint**|Identificateur de l'index.|  
|**colid**|**smallint**|ID de la colonne.|  
|**keyno**|**smallint**|Position de la colonne dans l'index.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Tables système pour les vues système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Vues de compatibilité &#40; Transact-SQL &#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
