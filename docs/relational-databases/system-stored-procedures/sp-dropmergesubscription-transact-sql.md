---
title: sp_dropmergesubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergesubscription_TSQL
- sp_dropmergesubscription
helpviewer_keywords:
- sp_dropmergesubscription
ms.assetid: 34244ae6-bd98-4a6a-bbd3-85f50edfcdc0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 34ba40387c246fe5f7f2de8dd74197b7cd43c0f5
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54130739"
---
# <a name="spdropmergesubscription-transact-sql"></a>sp_dropmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un abonnement à une publication de fusion et à l'Agent de fusion qui lui est associé. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropmergesubscription [ [ @publication= ] 'publication' ]   
    [ , [ @subscriber= ] 'subscriber'    
    [ , [ @subscriber_db= ] 'subscriber_db' ]   
    [ , [ @subscription_type= ] 'subscription_type' ]   
    [ , [ @ignore_distributor = ] ignore_distributor ]   
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=** ] **'**_publication_**'**  
 Est le nom de la publication. *publication* est **sysname**, avec NULL comme valeur par défaut. La publication doit déjà exister et se conformer aux règles des identificateurs.  
  
 [  **@subscriber=**] **'**_abonné_**'**  
 Nom de l'Abonné. *abonné* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@subscriber_db=** ] **'**_bd_abonné_**'**  
 Est le nom de la base de données d’abonnement. *base_de_données_abonnement*est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@subscription_type=** ] **'**_subscription_type_**'**  
 Est le type d’abonnement. *subscription_type*est **nvarchar (15)**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**Tous les**|Abonnements par envoi de données (push), par extraction de données (pull) et anonymes.|  
|**Anonyme**|Abonnement anonyme.|  
|**push**|Abonnement par envoi de données (push).|  
|**Extraction**|Abonnement par extraction de données (pull).|  
|**les deux** (valeur par défaut)|Abonnements par envoi et extraction de données.|  
  
 [  **@ignore_distributor =** ] *ignore_distributor*  
 Indique si cette procédure stockée est exécutée sans se connecter au serveur de distribution. *ignore_distributor* est **bits**, avec une valeur par défaut **0**. Ce paramètre peut être utilisé pour supprimer un abonnement sans effectuer de tâches de nettoyage sur le serveur de distribution. Il est également utile si vous devez réinstaller le serveur de distribution.  
  
 [  **@reserved=** ] *réservé*  
 Elle est réservée pour un usage futur. *réservé* est **bits**, avec une valeur par défaut **0**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_dropmergesubscription** est utilisé dans la réplication de fusion.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropmergesubscription_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_dropmergesubscription**.  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer un abonnement envoyé](../../relational-databases/replication/delete-a-push-subscription.md)   
 [Supprimer un abonnement par extraction](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
