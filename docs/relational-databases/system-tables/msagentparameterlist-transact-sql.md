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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3e240ab373316f72d41f472542907e3feb83cbbd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725493"
---
# <a name="msagentparameterlist-transact-sql"></a>MSagentparameterlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  La table **MSagentparameterlist** contient des informations sur les paramètres de l’agent de réplication et permet de spécifier les paramètres qui peuvent être définis pour un type d’agent donné. Cette table est stockée dans la base de données **msdb** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**agent_type**|**tinyint**|Type d'Agent:<br /><br /> **1** = agent d’instantané.<br /><br /> **2** = agent de lecture du journal.<br /><br /> **3** = agent de distribution.<br /><br /> **4** = agent de fusion.<br /><br /> **9** = agent de lecture de la file d’attente.|  
|**parameter_name**|**sysname**|Nom d'un paramètre d'agent valide.|  
|**default_value**|**nvarchar(4000)**|Valeur par défaut du paramètre d'agent, où NULL indique l'absence d'une telle valeur.|  
|**min_value**|**int**|Définit une limite inférieure pour le paramètre d'agent, où NULL indique l'absence de limite inférieure.|  
|**max_value**|**int**|Définit une limite supérieure pour le paramètre d'agent, où NULL indique l'absence de limite supérieure.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
