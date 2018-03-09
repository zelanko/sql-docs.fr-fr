---
title: sp_cleanup_log_shipping_history (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cleanup_log_shipping_history_TSQL
- sp_cleanup_log_shipping_history
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cleanup_log_shipping_history
ms.assetid: 96d236a9-1d0e-4f83-a4d3-f825b7381e46
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 368df0eee8a25341b2abde865175644a2cd6405d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="spcleanuplogshippinghistory-transact-sql"></a>sp_cleanup_log_shipping_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette procédure stockée nettoie l'historique localement et sur le serveur moniteur en fonction de la période de rétention.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_cleanup_log_shipping_history  
[ @agent_id = ] 'agent_id',  
[ @agent_type = ] 'agent_type'  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@agent_id =** ] '*agent_id*',  
 ID principal pour la sauvegarde ou ID secondaire pour la copie ou la restauration. *éléments agent_id* est **uniqueidentifier** et ne peut pas être NULL.  
  
 [ **@agent_type =** ] '*agent_type*'  
 Type d'opération de copie des journaux de transaction. 0 = Sauvegarde, 1 = Copie, 2 = Restauration. *agent_type* est **tinyint** et ne peut pas être NULL.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 **sp_cleanup_log_shipping_history** doit être exécuté à partir de la **master** base de données sur n’importe quel serveur d’expédition de journal. Cette procédure stockée nettoie les copies locales et distantes de **log_shipping_monitor_history_detail** et **log_shipping_monitor_error_detail** en fonction de la période de rétention de l’historique.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe peut exécuter cette procédure.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de journaux de transaction &#40; SQL Server &#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
