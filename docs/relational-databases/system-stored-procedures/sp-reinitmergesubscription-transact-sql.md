---
title: sp_reinitmergesubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_reinitmergesubscription_TSQL
- sp_reinitmergesubscription
helpviewer_keywords:
- sp_reinitmergesubscription
ms.assetid: 249a4048-e885-48e0-a92a-6577f59de751
author: stevestein
ms.author: sstein
ms.openlocfilehash: 27c10f9d5fa04ae449bdcca84891f0f28376eeb6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075698"
---
# <a name="spreinitmergesubscription-transact-sql"></a>sp_reinitmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Signale un abonnement de fusion en vue de sa réinitialisation lors de la prochaine exécution de l’Agent de fusion. Cette procédure stockée est exécutée dans la base de données de publication du serveur de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_reinitmergesubscription [ [ @publication = ] 'publication'  
    [ , [ @subscriber = ] 'subscriber'  
    [ , [ @subscriber_db = ] 'subscriber_db'  
    [ , [ @upload_first = ] 'upload_first'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, avec une valeur par défaut **tous les**.  
  
`[ @subscriber = ] 'subscriber'` Est le nom de l’abonné. *abonné* est **sysname**, avec une valeur par défaut **tous les**.  
  
`[ @subscriber_db = ] 'subscriber_db'` Est le nom de la base de données de l’abonné. *bd_abonné* est **sysname**, avec une valeur par défaut **tous les**.  
  
`[ @upload_first = ] 'upload_first'` Est que les modifications sur l’abonné sont téléchargées avant la réinitialisation de l’abonnement. *upload_first* est **nvarchar (5)** , avec FALSE comme valeur par défaut. Si **true**, les modifications sont téléchargées avant la réinitialisation de l’abonnement. Si **false**, modifications ne sont pas téléchargées.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_reinitmergesubscription** est utilisé dans la réplication de fusion.  
  
 **sp_reinitmergesubscription** peut être appelé depuis le serveur de publication pour réinitialiser les abonnements de fusion. Il est recommandé de réexécuter également l'Agent d'instantané.  
  
 Si vous ajoutez, supprimez ou modifiez un filtre paramétré, les modifications en attente chez l'abonné ne peuvent pas être chargées sur le serveur de publication pendant la réinitialisation. Si vous voulez télécharger les modifications en attente, synchronisez tous les abonnements avant de modifier le filtre.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_reinitmergepushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergesubscripti_1.sql)]  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_reinitmergepushsubwithupload](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergesubscripti_2.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_reinitmergesubscription**.  
  
## <a name="see-also"></a>Voir aussi  
 [Réinitialiser des abonnements](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
