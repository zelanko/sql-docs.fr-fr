---
description: sys.sp_xtp_control_proc_exec_stats (Transact-SQL)
title: sys. sp_xtp_control_proc_exec_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_control_proc_exec_stats
- sys.sp_xtp_control_proc_exec_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_control_proc_exec_stats
ms.assetid: f5119808-76a1-4522-8529-9e02ee39adcb
author: markingmyname
ms.author: maghan
ms.openlocfilehash: dcfc3a19de02b46cb869d529c1ec3c2ce88a1c22
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545846"
---
# <a name="syssp_xtp_control_proc_exec_stats-transact-sql"></a>sys.sp_xtp_control_proc_exec_stats (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

  Active la collection de statistiques pour les procédures stockées compilées en mode natif de l'instance.  
  
 Pour activer la collecte de statistiques au niveau de la requête pour les procédures stockées compilées en mode natif, consultez [sys. sp_xtp_control_query_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_xtp_control_proc_exec_stats [ [ @new_collection_value = ] collection_value ], [ @old_collection_value]  
```  
  
## <a name="arguments"></a>Arguments  
 @new_collection_value = *valeur*  
 Détermine si la collection de statistiques au niveau de la procédure est activée (1) ou désactivée (0).  
  
 @new_collection_value a la valeur zéro lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou la base de données démarre.  
  
 @old_collection_value = *valeur*  
 Retourne l'état actuel.  
  
## <a name="return-code"></a>Code de retour  
 0 pour réussite. Une valeur différente de zéro pour un échec.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle sysadmin fixe.  
  
## <a name="code-samples"></a>Exemples de code  
 Pour définir @new_collection_value et interroger la valeur de @new_collection_value:  
  
```  
exec [sys].[sp_xtp_control_proc_exec_stats] @new_collection_value = 1  
declare @c bit  
exec sp_xtp_control_proc_exec_stats @old_collection_value=@c output  
select @c as 'collection status'  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
