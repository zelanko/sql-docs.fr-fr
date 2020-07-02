---
title: sysarticlecolumns (vue système) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns view
ms.assetid: a8dd8d13-c827-45c4-87ba-802725301382
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10467dfa991efbed27941ba31424057b721527d1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750134"
---
# <a name="sysarticlecolumns-system-view-transact-sql"></a>sysarticlecolumns (Vue système, Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  La vue **sysarticlecolumns** expose des informations supplémentaires sur les colonnes dans les articles publiés. Cette vue est stockée dans la base de données de distribution.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Identifie un article.|  
|**colid**|**int**|Identifie une colonne dans un article.|  
|**is_udt**|**int**|Indique si la colonne correspond à une colonne de type de données défini par l'utilisateur (UDT, User-defined Data Type). La valeur **1** indique une colonne UDT.|  
|**is_xml**|**int**|Indique si la colonne est une colonne **XML** . La valeur **1** indique une colonne **XML** .|  
|**is_max**|**int**|Indique si la colonne est une colonne de type de données de valeur élevée (**varchar (max)**, **nvarchar (max)** ou **varbinary (max)**). La valeur **1** indique une colonne de valeur élevée.|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
