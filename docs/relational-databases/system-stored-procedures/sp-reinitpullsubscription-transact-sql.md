---
title: sp_reinitpullsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_reinitpullsubscription_TSQL
- sp_reinitpullsubscription
helpviewer_keywords:
- sp_reinitpullsubscription
ms.assetid: 7d9abe49-ce92-47f3-82c9-aea749518c91
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1389e76d4e679a3ee16c548bf752d5668dfa48b7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075672"
---
# <a name="spreinitpullsubscription-transact-sql"></a>sp_reinitpullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Signale un abonnement par extraction de données (pull) transactionnel ou anonyme en vue de sa réinitialisation lors de la prochaine exécution de l’Agent de distribution. Cette procédure stockée est exécutée sur la base de données d'abonnement par extraction de données (pull) de l'abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_reinitpullsubscription [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'` Est le nom de la base de données du serveur de publication. *publisher_db* est **sysname**, sans valeur par défaut.  
  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, par défaut, all, marque tous les abonnements pour réinitialisation.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_reinitpullsubscription** est utilisé dans la réplication transactionnelle.  
  
 **sp_reinitpullsubscription** n’est pas pris en charge pour la réplication transactionnelle peer-to-peer.  
  
 **sp_reinitpullsubscription** peut être appelée à partir de l’abonné pour réinitialiser l’abonnement, au cours de la prochaine exécution de l’Agent de Distribution.  
  
 Abonnements aux publications créées avec la valeur **false** pour **@immediate_sync** ne peuvent pas être réinitialisés à partir de l’abonné.  
  
 Vous pouvez réinitialiser un abonnement par extraction en l’exécutant **sp_reinitpullsubscription** sur l’abonné ou **sp_reinitsubscription** sur le serveur de publication.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_reinitpullsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitpullsubscriptio_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_reinitpullsubscription**.  
  
## <a name="see-also"></a>Voir aussi  
 [Réinitialiser un abonnement](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Réinitialiser des abonnements](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
