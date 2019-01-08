---
title: sp_dropsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropsubscription
- sp_dropsubscription_TSQL
helpviewer_keywords:
- sp_dropsubscription
ms.assetid: 7551f345-5510-4684-ab53-f9057249d13a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 08e25ee6f2de589c3d7367c140bd0ea63d4cec1e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52812966"
---
# <a name="spdropsubscription-transact-sql"></a>sp_dropsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime les abonnements relatifs à un article, une publication ou un ensemble d'abonnements particuliers sur le serveur de publication. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropsubscription [ [ @publication= ] 'publication' ]  
    [ , [ @article= ] 'article' ]  
        , [ @subscriber= ] 'subscriber'  
    [ , [ @destination_db= ] 'destination_db' ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=** ] **'**_publication_**'**  
 Nom de la publication associée. *publication* est **sysname**, avec NULL comme valeur par défaut. Si **tous les**, tous les abonnements pour toutes les publications de l’abonné spécifié seront annulés. *publication* est un paramètre obligatoire.  
  
 [  **@article=** ] **'**_article_**'**  
 Nom de l'article. *article* est **sysname**, avec NULL comme valeur par défaut. Si **tous les**, spécifié d’abonnements à tous les articles pour chaque publication et abonné sont supprimés. Utilisez **tous les** pour les publications qui autorisent immédiates mis à jour.  
  
 [  **@subscriber=** ] **'**_subscribe_r **'**  
 Nom de l'Abonné dont les abonnements seront supprimés. *abonné* est **sysname**, sans valeur par défaut. Si **tous les**, tous les abonnements pour tous les abonnés sont supprimés.  
  
 [  **@destination_db=** ] **'**_destination_db_**'**  
 Nom de la base de données de destination. *destination_db* est **sysname**, avec NULL comme valeur par défaut. Si la valeur est NULL, tous les abonnements de cet Abonné seront supprimés.  
  
 [  **@ignore_distributor =** ] *ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@reserved=** ] **'**_réservé_**'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_dropsubscription** est utilisé dans la réplication transactionnelle et d’instantané.  
  
 Si vous supprimez l'abonnement à un article dans une publication à synchronisation immédiate, vous ne pourrez le rajouter que si vous supprimez les abonnements relatifs à tous les articles de la publication et que vous les rajoutez tous en même temps.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropsubscription-tran_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe le **db_owner** rôle de base de données fixe ou de l’utilisateur qui a créé l’abonnement peut exécuter **sp_dropsubscription**.  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer un abonnement envoyé](../../relational-databases/replication/delete-a-push-subscription.md)   
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
