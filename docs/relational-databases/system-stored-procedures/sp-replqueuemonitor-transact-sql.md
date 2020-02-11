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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74055217"
---
# <a name="sp_replqueuemonitor-transact-sql"></a>sp_replqueuemonitor (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Répertorie les messages de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file d' [!INCLUDE[msCoName](../../includes/msconame-md.md)] attente d’une file d’attente ou Message Queuing pour les abonnements de mise à jour en attente à une publication spécifiée. Si des files d'attente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont utilisées, cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné. Si Message Queuing est utilisé, elle est exécutée sur la base de données de distribution du serveur de distribution.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replqueuemonitor [ @publisher = ] 'publisher'  
    [ , [ @publisherdb = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @tranid = ] 'tranid' ]  
    [ , [ @queuetype = ] 'queuetype' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, avec NULL comme valeur par défaut. Le serveur doit être configuré pour la publication. Valeur NULL pour tous les serveurs de publication.  
  
`[ @publisherdb = ] 'publisher_db' ]`Nom de la base de données de publication. *publisher_db* est de **type sysname**, avec NULL comme valeur par défaut. Valeur NULL pour toutes les bases de données de publication.  
  
`[ @publication = ] 'publication' ]`Nom de la publication. *publication*est de **type sysname**, avec NULL comme valeur par défaut. Valeur NULL pour toutes les publications.  
  
`[ @tranid = ] 'tranid' ]`ID de la transaction. *tranid*est de **type sysname**, avec NULL comme valeur par défaut. Valeur NULL pour toutes les transactions.  
  
`[ @queuetype = ] 'queuetype' ]`Type de file d’attente qui stocke les transactions. *QueueType* est de **type tinyint** , avec **0**comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|Tous les types de files d'attente|  
|**1**|Message Queuing|  
|**2**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mis|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_replqueuemonitor** est utilisé dans la réplication d’instantané ou la réplication transactionnelle avec des abonnements de mise à jour en attente. Les messages de file d'attente qui ne contiennent pas de commandes SQL ou qui font partie d'une commande SQL globale ne sont pas affichés.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_replqueuemonitor**.  
  
## <a name="see-also"></a>Voir aussi  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
