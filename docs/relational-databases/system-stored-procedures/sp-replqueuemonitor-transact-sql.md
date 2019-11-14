---
title: sp_replqueuemonitor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replqueuemonitor
- sp_replqueuemonitor_TSQL
helpviewer_keywords:
- sp_replqueuemonitor
ms.assetid: 6909a3f1-43a2-4df5-a6a5-9e6f347ac841
author: stevestein
ms.author: sstein
ms.openlocfilehash: d3c84d15087c3cb6bb63380bc6cf0c75e773b883
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74055217"
---
# <a name="sp_replqueuemonitor-transact-sql"></a>sp_replqueuemonitor (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Répertorie les messages de la file d’attente d’un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file d’attente ou de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing pour les abonnements de mise à jour en attente à une publication spécifiée. Si des files d'attente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont utilisées, cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné. Si Message Queuing est utilisé, elle est exécutée sur la base de données de distribution du serveur de distribution.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replqueuemonitor [ @publisher = ] 'publisher'  
    [ , [ @publisherdb = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @tranid = ] 'tranid' ]  
    [ , [ @queuetype = ] 'queuetype' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'` est le nom du serveur de publication. *Publisher* est de **type sysname**, avec NULL comme valeur par défaut. Le serveur doit être configuré pour la publication. Valeur NULL pour tous les serveurs de publication.  
  
`[ @publisherdb = ] 'publisher_db' ]` est le nom de la base de données de publication. *publisher_db* est de **type sysname**, avec NULL comme valeur par défaut. Valeur NULL pour toutes les bases de données de publication.  
  
`[ @publication = ] 'publication' ]` est le nom de la publication. *publication*est de **type sysname**, avec NULL comme valeur par défaut. Valeur NULL pour toutes les publications.  
  
`[ @tranid = ] 'tranid' ]` est l’ID de la transaction. *tranid*est de **type sysname**, avec NULL comme valeur par défaut. Valeur NULL pour toutes les transactions.  
  
`[ @queuetype = ] 'queuetype' ]` est le type de file d’attente qui stocke les transactions. *QueueType* est de **type tinyint** , avec **0**comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|Tous les types de files d'attente|  
|**1**|Message Queuing|  
|**2**|File d'attente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_replqueuemonitor** est utilisé dans la réplication d’instantané ou la réplication transactionnelle avec des abonnements de mise à jour en attente. Les messages de file d'attente qui ne contiennent pas de commandes SQL ou qui font partie d'une commande SQL globale ne sont pas affichés.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_replqueuemonitor**.  
  
## <a name="see-also"></a>Voir aussi  
 [Abonnements pouvant être mis à jour pour la réplication transactionnelle](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
