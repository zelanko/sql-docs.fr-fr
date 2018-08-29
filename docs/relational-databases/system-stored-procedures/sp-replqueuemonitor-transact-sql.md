---
title: sp_replqueuemonitor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_replqueuemonitor
- sp_replqueuemonitor_TSQL
helpviewer_keywords:
- sp_replqueuemonitor
ms.assetid: 6909a3f1-43a2-4df5-a6a5-9e6f347ac841
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 57bf20aa17d7c60e0902a1e216b4d892da54f62f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43023307"
---
# <a name="spreplqueuemonitor-transact-sql"></a>sp_replqueuemonitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie les messages de file d’attente à partir d’un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] file d’attente ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing pour les abonnements mis à jour en file d’attente à une publication spécifiée. Si des files d'attente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont utilisées, cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné. Si Message Queuing est utilisé, elle est exécutée sur la base de données de distribution du serveur de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replqueuemonitor [ @publisher = ] 'publisher'  
    [ , [ @publisherdb = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @tranid = ] 'tranid' ]  
    [ , [ @queuetype = ] 'queuetype' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@publisher** =] **'***publisher***'**  
 Nom du serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut. Le serveur doit être configuré pour la publication. Valeur NULL pour tous les serveurs de publication.  
  
 [ **@publisherdb** =] **'***publisher_db***'** ]  
 Nom de la base de données de publication. *publisher_db* est **sysname**, avec NULL comme valeur par défaut. Valeur NULL pour toutes les bases de données de publication.  
  
 [ **@publication** =] **'***publication***'** ]  
 Nom de la publication. *publication*est **sysname**, avec NULL comme valeur par défaut. Valeur NULL pour toutes les publications.  
  
 [ **@tranid** =] **'***tranid***'** ]  
 Est l’ID de transaction. *tranid*est **sysname**, avec NULL comme valeur par défaut. Valeur NULL pour toutes les transactions.  
  
 [**@queuetype=** ] **'***queuetype***'** ]  
 Type de file d'attente stockant les transactions. *QueueType* est **tinyint** avec une valeur par défaut **0**, et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**0**|Tous les types de files d'attente|  
|**1**|Message Queuing|  
|**2**|File d'attente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_replqueuemonitor** est utilisée dans la réplication d’instantané ou réplication transactionnelle avec abonnements mis à jour en file d’attente. Les messages de file d'attente qui ne contiennent pas de commandes SQL ou qui font partie d'une commande SQL globale ne sont pas affichés.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_replqueuemonitor**.  
  
## <a name="see-also"></a>Voir aussi  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
