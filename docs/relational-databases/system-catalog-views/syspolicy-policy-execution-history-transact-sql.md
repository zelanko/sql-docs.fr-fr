---
title: syspolicy_policy_execution_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_TSQL
- syspolicy_policy_execution_history
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history view
ms.assetid: b13c44a7-6d49-4d50-abe1-e657fc52bb05
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ed3bca383e5f6ad1960274145327f915c6e8ca5c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85663768"
---
# <a name="syspolicy_policy_execution_history-transact-sql"></a>syspolicy_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Affiche l'heure d'exécution des stratégies, le résultat de chaque exécution et les détails des erreurs, le cas échéant. Le tableau suivant décrit les colonnes dans la vue syspolicy_policy_execution_history.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|Identificateur de cet enregistrement. Chaque enregistrement indique une stratégie et l'heure de son initialisation.|  
|policy_id|**int**|Identificateur de la stratégie.|  
|start_date|**datetime**|Date et heure de la tentative d'exécution de cette stratégie.|  
|end_date|**datetime**|Heure de fin d'exécution de cette stratégie.|  
|result|**bit**|Succès ou échec de la stratégie. 0 = succès, 1 = échec.|  
|exception_message|**nvarchar(max)**|Message généré par l'exception si celle-ci se produit.|  
|exception|**nvarchar(max)**|Description de l'exception si celle-ci se produit.|  
  
## <a name="remarks"></a>Remarques  
 La vue [syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md) contient des détails connexes sur les cibles de la stratégie et les expressions de condition testées.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Vues de la Gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
