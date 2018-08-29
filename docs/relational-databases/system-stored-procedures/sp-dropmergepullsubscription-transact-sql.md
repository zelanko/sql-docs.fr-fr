---
title: sp_dropmergepullsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
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
- sp_dropmergepullsubscription
- sp_dropmergepullsubscription_TSQL
helpviewer_keywords:
- sp_dropmergepullsubscription
ms.assetid: 9301dd80-72f7-4adb-9b13-87e7f9114248
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1fa2a31c5ef60b869fe387e4a3ac8155a73d3690
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43017955"
---
# <a name="spdropmergepullsubscription-transact-sql"></a>sp_dropmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un abonnement de fusion par extraction de données (pull). Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropmergepullsubscription [ @publication= ] 'publication'   
        , [ @publisher= ] 'publisher'   
        , [ @publisher_db= ] 'publisher_db'   
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=**] **'***publication***'**  
 Nom de la publication. *publication* est **sysname**, avec NULL comme valeur par défaut. Ce paramètre est obligatoire. Spécifiez la valeur **tous les** pour supprimer les abonnements à toutes les publications  
  
 [  **@publisher=**] **'***publisher***'**  
 Nom du serveur de publication. *serveur de publication*est **sysname**, avec NULL comme valeur par défaut. Ce paramètre est obligatoire.  
  
 [  **@publisher_db=**] **'***publisher_db***'**  
 Nom de la base de données du serveur de publication. *publisher_db*est **sysname**, avec NULL comme valeur par défaut. Ce paramètre est obligatoire.  
  
 [  **@reserved=**] **'***réservé***'**  
 Elle est réservée pour un usage futur. *réservé* est **bits**, avec une valeur par défaut **0**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_dropmergepullsubscription** est utilisé dans la réplication de fusion.  
  
 **sp_dropmergepullsubscription** supprime l’Agent de fusion pour cet abonnement par extraction de fusion, bien que l’Agent de fusion n’est pas créé dans **sp_addmergepullsubscription**.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropmergepullsubscrip_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou l’utilisateur qui a créé l’abonnement par extraction de fusion peut exécuter **sp_dropmergepullsubscription**. Le **db_owner** rôle de base de données fixe n’est en mesure d’exécuter **sp_dropmergepullsubscription** si l’utilisateur qui a créé l’abonnement par extraction de fusion appartient à ce rôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer un abonnement par extraction](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)  
  
  
