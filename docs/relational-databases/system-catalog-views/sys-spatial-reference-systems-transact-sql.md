---
title: Sys.spatial_reference_systems (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- spatial_reference_systems_TSQL
- sys.spatial_reference_systems_TSQL
- sys.spatial_reference_systems
- spatial_reference_systems
dev_langs: TSQL
helpviewer_keywords:
- sys.spatial_reference_systems catalog view
- spatial_reference_systems
ms.assetid: 3c9bc120-67c3-463f-9e24-29fd623f25a0
caps.latest.revision: "11"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4490cc6d28ee06193436de8b57cde8e7ac04402
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysspatialreferencesystems-transact-sql"></a>sys.spatial_reference_systems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Répertorie les systèmes de référence spatiale (SRID) pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|spatial_reference_id|**int**|SRID pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|authority_name|**nvarchar (128)**|Autorité du SRID.|  
|authorized_spatial_reference_id|**int**|SRID attribué par l’autorité nommée dans **authority_name**.|  
|well_known_text|**nvarchar(4000)**|Représentation WKT du SRID.|  
|unit_of_measure|**nvarchar (128)**|Nom de l'unité de mesure.|  
|unit_conversion_factor|**float**|Longueur de l'unité de mesure en mètres.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
  
