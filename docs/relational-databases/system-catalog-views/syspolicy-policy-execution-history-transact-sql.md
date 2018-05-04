---
title: syspolicy_policy_execution_history (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_TSQL
- syspolicy_policy_execution_history
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history view
ms.assetid: b13c44a7-6d49-4d50-abe1-e657fc52bb05
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 246f9ca4d8368f193547758d079169d2252a2d00
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="syspolicypolicyexecutionhistory-transact-sql"></a>syspolicy_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche l'heure d'exécution des stratégies, le résultat de chaque exécution et les détails des erreurs, le cas échéant. Le tableau suivant décrit les colonnes dans la vue syspolicy_policy_execution_history.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|Identificateur de cet enregistrement. Chaque enregistrement indique une stratégie et l'heure de son initialisation.|  
|policy_id|**int**|Identificateur de la stratégie.|  
|start_date|**datetime**|Date et heure de la tentative d'exécution de cette stratégie.|  
|end_date|**datetime**|Heure de fin d'exécution de cette stratégie.|  
|result|**bit**|Succès ou échec de la stratégie. 0 = succès, 1 = échec.|  
|exception_message|**nvarchar(max)**|Message généré par l'exception si celle-ci se produit.|  
|exception|**nvarchar(max)**|Description de l'exception si celle-ci se produit.|  
  
## <a name="remarks"></a>Notes  
 Le [syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md) vue contient des détails connexes sur les cibles de la stratégie et les expressions de condition testées.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Vues de la Gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
