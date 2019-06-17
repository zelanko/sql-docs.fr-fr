---
title: MSagentparameterlist (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
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
ms.openlocfilehash: 1fd8e84a443c87846b4c40c45152b1225e2bc7b1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62817085"
---
# <a name="msagentparameterlist-transact-sql"></a>MSagentparameterlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSagentparameterlist** table contient des informations de paramètre de l’agent de réplication et est utilisée pour spécifier les paramètres qui peuvent être définies pour un type d’agent donné. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**agent_type**|**tinyint**|Type d'Agent:<br /><br /> **1** = Agent d’instantané.<br /><br /> **2** = Agent de lecture du journal.<br /><br /> **3** = Agent de distribution.<br /><br /> **4** = Agent de fusion.<br /><br /> **9** = Agent de lecture de file d’attente.|  
|**parameter_name**|**sysname**|Nom d'un paramètre d'agent valide.|  
|**default_value**|**nvarchar(4000)**|Valeur par défaut du paramètre d'agent, où NULL indique l'absence d'une telle valeur.|  
|**min_value**|**Int**|Définit une limite inférieure pour le paramètre d'agent, où NULL indique l'absence de limite inférieure.|  
|**max_value**|**Int**|Définit une limite supérieure pour le paramètre d'agent, où NULL indique l'absence de limite supérieure.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
