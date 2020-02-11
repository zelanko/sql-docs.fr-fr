---
title: sp_expired_subscription_cleanup (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_expired_subscription_cleanup
- SP_EXPIRED_SUBSCRIPTION_CLEANUP_TSQL
helpviewer_keywords:
- sp_expired_subscription_cleanup
ms.assetid: 6abc29fe-d77a-4673-9d99-ae31c688012c
author: stevestein
ms.author: sstein
ms.openlocfilehash: fb556a464077092cacd7107a8c2b4b124c6db707
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124431"
---
# <a name="sp_expired_subscription_cleanup-transact-sql"></a>sp_expired_subscription_cleanup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contrôle l'état de tous les abonnements de chaque publication et supprime ceux qui ont expiré. Cette procédure stockée est exécutée sur le serveur de publication sur n’importe quelle base de données ou sur le serveur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de distribution de la base de données de distribution pour un serveur de publication non-.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_expired_subscription_cleanup [ [ @publisher = ] 'publisher' ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'`Nom d’un serveur de publication non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -. *publication* est de **type sysname**, avec NULL comme valeur par défaut. Ne spécifiez pas ce paramètre pour un serveur de publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_expired_subscription_cleanup** est utilisé dans tous les types de réplications.  
  
 **sp_expired_subscription_cleanup** est exécutée par la tâche de nettoyage d’abonnement expirée pour détecter et supprimer les abonnements expirés des bases de données de publication toutes les 24 heures. Si l'un d'entre eux est périmé, c'est-à-dire s'il n'a pas été synchronisé avec le serveur de publication au cours de la période de rétention, la publication est considérée comme étant arrivée à expiration et les traces de l'abonnement sont effacées du serveur de publication. Pour plus d’informations, voir [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_expired_subscription_cleanup**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md)   
 [sp_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
