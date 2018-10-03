---
title: sp_addqueued_artinfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_addqueued_artinfo
- sp_addqueued_artinfo_TSQL
helpviewer_keywords:
- sp_addqueued_artinfo
ms.assetid: decdb6eb-3dcd-4053-a21d-fd367c3fbafb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a2e596ecc5e6470bbcc1a62684c1fd1a6533711d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47770157"
---
# <a name="spaddqueuedartinfo-transact-sql"></a>sp_addqueued_artinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  
  
> [!IMPORTANT]  
>  Le [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) procédure doit être utilisée à la place de **sp_addqueued_artinfo**. [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) génère un script qui contienne le **sp_addqueued_artinfo** et **sp_addsynctrigger** appels.  
  
 Crée le [MSsubscription_articles](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md) table sur l’abonné est utilisé pour effectuer le suivi des informations d’abonnement de l’article (en file d’attente de mise à jour et la mise à jour immédiate avec en file d’attente de mise à jour sous forme de basculement). Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addqueued_artinfo [ @artid= ] 'artid'  
        , [ @article= ] 'article'  
        , [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @dest_table= ] 'dest_table'  
        , [ @owner = ] 'owner'  
        , [ @cft_table= ] 'cft_table'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@artid=** ] **'***artid***'**  
 Nom de l'ID d'article. *artid* est **int**, sans valeur par défaut  
  
 [  **@article=**] **'***article***'**  
 Nom de l'article à écrire. *article* est **sysname**, sans valeur par défaut  
  
 [  **@publisher=**] **'***publisher***'**  
 Est le nom du serveur de publication. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
 [  **@publisher_db=**] **'***publisher_db***'**  
 Nom de la base de données du serveur de publication. *publisher_db* est **sysname**, sans valeur par défaut.  
  
 [  **@publication=**] **'***publication***'**  
 Nom de la publication à écrire. *publication* est **sysname**, sans valeur par défaut.  
  
 [  **@dest_table=** ] *dest_table *****  
 Nom de la table de destination. *dest_table* est **sysname**, sans valeur par défaut.  
  
 [ **@owner =** ] **'***propriétaire***'**  
 Est le propriétaire de l’abonnement. *propriétaire* est **sysname**, sans valeur par défaut.  
  
 [  **@cft_table=** ] **'***cft_table***'**  
 Nom de la table de conflits avec mise à jour en attente pour cet article. *cft_table*est **sysname**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addqueued_artinfo** est utilisé par l’Agent de Distribution dans le cadre de l’abonnement. Cette procédure stockée n'est généralement pas exécutée par les utilisateurs, mais peut s'avérer utile si l'utilisateur doit configurer manuellement un abonnement.  
  
 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) au lieu de **sp_addqueued_artinfo**.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_addqueued_artinfo**.  
  
## <a name="see-also"></a>Voir aussi  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [MSsubscription_articles &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
