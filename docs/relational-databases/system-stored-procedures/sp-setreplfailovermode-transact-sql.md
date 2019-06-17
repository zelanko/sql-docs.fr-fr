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
manager: craigg
ms.openlocfilehash: ae89e606633fc3555745dd56fc7703ef50685468
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63028629"
---
# <a name="spsetreplfailovermode-transact-sql"></a>sp_setreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet de configurer le mode de basculement des abonnements activés pour la mise à jour immédiate avec possibilité de basculement vers la mise à jour en attente. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné. Pour plus d’informations sur les modes de basculement, consultez [à des abonnements pour la réplication transactionnelle](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
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
`[ @publisher = ] 'publisher'` Est le nom de la publication. *publication* est **sysname**, sans valeur par défaut. La publication doit déjà exister.  
  
`[ @publisher_db = ] 'publisher_db'` Est le nom de la base de données de publication. *publisher_db* est **sysname**, sans valeur par défaut.  
  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication*est **sysname**, sans valeur par défaut.  
  
 [ **@failover_mode=** ] **'***failover_mode***'**  
 Mode de basculement pour l'abonnement. *failover_mode* est **nvarchar (10)** et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**immédiate** ou **sync**|Les modifications de données effectuées sur l'Abonné sont instantanément copiées en bloc sur le serveur de publication.|  
|**queued**|Modifications de données sont stockées dans un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file d’attente.|  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing a été déconseillée et n’est plus pris en charge.  
  
`[ @override = ] override` Usage interne uniquement.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_setreplfailovermode** est utilisé dans la réplication d’instantané ou réplication transactionnelle pour les abonnements sont activés, soit en file d’attente de la mise à jour avec le basculement vers la mise à jour immédiate ou mise à jour immédiate avec basculement en file d’attente la mise à jour.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_setreplfailovermode**.  
  
## <a name="see-also"></a>Voir aussi  
 [Basculer entre les Modes de mise à jour d’un abonnement transactionnel actualisable](../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
