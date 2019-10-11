---
title: sp_setreplfailovermode (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setreplfailovermode
- sp_setreplfailovermode_TSQL
helpviewer_keywords:
- sp_setreplfailovermode
ms.assetid: ca98a4c3-bea4-4130-88d7-79e0fd1e85f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5b39a5fa53560abb825b303d37d111bcbd7d0886
ms.sourcegitcommit: 79e6d49ae4632f282483b0be935fdee038f69cc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72173561"
---
# <a name="sp_setreplfailovermode-transact-sql"></a>sp_setreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet de configurer le mode de basculement des abonnements activés pour la mise à jour immédiate avec possibilité de basculement vers la mise à jour en attente. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné. Pour plus d’informations sur les modes de basculement, consultez [abonnements pouvant être mis à jour pour la réplication transactionnelle](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_setreplfailovermode [ @publisher= ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication= ] 'publication' ]  
    [ , [ @failover_mode= ] 'failover_mode' ]  
    [ , [ @override = ] override ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'` est le nom de la publication. *publication* est de **type sysname**, sans valeur par défaut. La publication doit déjà exister.  
  
`[ @publisher_db = ] 'publisher_db'` est le nom de la base de données de publication. *publisher_db* est de **type sysname**, sans valeur par défaut.  
  
`[ @publication = ] 'publication'` est le nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @failover_mode = ] 'failover_mode'` est le mode de basculement de l’abonnement. *failover_mode* est de type **nvarchar (10)** et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**exécution** ou **synchronisation**|Les modifications de données effectuées sur l'Abonné sont instantanément copiées en bloc sur le serveur de publication.|  
|**en attente**|Les modifications de données sont stockées dans une file d’attente [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing est déconseillé et n’est plus pris en charge.  
  
`[ @override = ] override` à usage interne uniquement.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_setreplfailovermode** est utilisé dans la réplication d’instantané ou dans la réplication transactionnelle pour laquelle les abonnements sont activés, soit pour la mise à jour en attente avec basculement vers la mise à jour immédiate, soit pour la mise à jour immédiate avec basculement vers la mise à jour en attente.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_setreplfailovermode**.  
  
## <a name="see-also"></a>Voir aussi  
 [Basculer entre les modes de mise à jour d’un abonnement transactionnel pouvant être mis à](../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)jour    
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
