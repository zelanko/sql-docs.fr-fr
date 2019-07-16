---
title: MSagent_parameters (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSagent_parameters_TSQL
- MSagent_parameters
dev_langs:
- TSQL
helpviewer_keywords:
- MSagent_parameters system table
ms.assetid: be30abc9-c00d-446f-b1b4-1269772f37e6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38c6bb0ae74ffe54e9637610139374e458e3649d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68095704"
---
# <a name="msagentparameters-transact-sql"></a>MSagent_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSagent_parameters** table contient les paramètres associés à un profil d’agent. Les noms de paramètres sont identiques à ceux qui sont pris en charge par l'agent. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|L’ID de profil à partir de la **MSagent_profiles** table.|  
|**parameter_name**|**sysname**|Nom du paramètre.|  
|**value**|**nvarchar(255)**|Valeur du paramètre.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
