---
title: sysarticlecolumns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
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
- sysarticlecolumns system table
ms.assetid: 55918592-e05d-43b6-843b-7e4d82fa6275
author: stevestein
ms.author: sstein
ms.openlocfilehash: 61e1329fe35ae032b5d35f94dd2e1ce5e8d08d38
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68130516"
---
# <a name="sysarticlecolumns-transact-sql"></a>sysarticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **sysarticlecolumns** table contient une ligne pour chaque colonne de table qui est publié dans une publication transactionnelle ou d’instantané et mappe chaque colonne à son article. Cette table est stockée dans la base de données de publication.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Identifie un article.|  
|**colid**|**smallint**|Identifie une colonne dans un article.|  
|**is_udt**|**bit**|Indique si la colonne correspond à une colonne de type de données défini par l'utilisateur (UDT, User-defined Data Type). La valeur **1** indique une colonne UDT.|  
|**is_xml**|**bit**|Indique si la colonne est une **xml** colonne. La valeur **1** indique une colonne xml.|  
|**is_max**|**bit**|Indique si la colonne est une colonne de type de données de valeur élevée, **varchar (max)** , **nvarchar (max)** , et **varbinary (max)** . La valeur **1** indique une colonne de valeur élevée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
