---
title: MSagentparameterlist (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSagentparameterlist_TSQL
- MSagentparameterlist
dev_langs:
- TSQL
helpviewer_keywords:
- Msagentparameterlist system table
ms.assetid: 4ea571a0-078d-4e13-95ee-f3d4bbd4dfb2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1a765732f4d44ef31ed947a10d3b9449e261d1a0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760927"
---
# <a name="msagentparameterlist-transact-sql"></a>MSagentparameterlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSagentparameterlist** table contient des informations de paramètre de l’agent de réplication et est utilisée pour spécifier les paramètres qui peuvent être définies pour un type d’agent donné. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**agent_type**|**tinyint**|Type d'Agent:<br /><br /> **1** = Agent d’instantané.<br /><br /> **2** = Agent de lecture du journal.<br /><br /> **3** = Agent de distribution.<br /><br /> **4** = Agent de fusion.<br /><br /> **9** = Agent de lecture de file d’attente.|  
|**parameter_name**|**sysname**|Nom d'un paramètre d'agent valide.|  
|**default_value**|**nvarchar(4000)**|Valeur par défaut du paramètre d'agent, où NULL indique l'absence d'une telle valeur.|  
|**MIN_VALUE**|**Int**|Définit une limite inférieure pour le paramètre d'agent, où NULL indique l'absence de limite inférieure.|  
|**MAX_VALUE**|**Int**|Définit une limite supérieure pour le paramètre d'agent, où NULL indique l'absence de limite supérieure.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
