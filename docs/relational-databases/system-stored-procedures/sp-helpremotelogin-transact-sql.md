---
title: sp_helpremotelogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpremotelogin_TSQL
- sp_helpremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpremotelogin
ms.assetid: 93f50869-2627-4642-899f-8f626f8833f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 11d71139786ac1442588f016bf8c576b92853cf3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67997582"
---
# <a name="sp_helpremotelogin-transact-sql"></a>sp_helpremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur les connexions distantes d'un serveur distant spécifique ou de tous les serveurs distants, définis sur le serveur local.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Utilisez des serveurs liés et des procédures stockées de serveur lié à la place.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpremotelogin [ [ @remoteserver = ] 'remoteserver' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @remoteserver **=** ] **'***serveur_distant***'**  
 Nom du serveur distant sur lequel les informations relatives à la connexion distante sont retournées. *serveur_distant* est de **type sysname**, avec NULL comme valeur par défaut. Si *serveur_distant* n’est pas spécifié, des informations sur tous les serveurs distants définis sur le serveur local sont renvoyées.  
  
 [ @remotename **=** ] **'***remote_name***'**  
 Connexion distante spécifique du serveur distant. *remote_name* est de **type sysname**, avec NULL comme valeur par défaut. Si *remote_name* n’est pas spécifié, des informations sur tous les utilisateurs distants définis pour *serveur_distant* sont retournées.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|server|**sysname**|Nom d'un serveur distant défini sur le serveur local.|  
|local_user_name|**sysname**|Connexion du serveur local à laquelle sont mappées les connexions distantes.|  
|remote_user_name|**sysname**|Connexion sur le serveur distant qui est mappée à local_user_name.|  
|options|**sysname**|Trusted = La connexion distante n'a pas à fournir de mot de passe lors de la connexion au serveur local à partir du serveur distant.<br /><br /> Untrusted (ou vide) = La connexion distante doit fournir un mot de passe lors de la connexion au serveur local à partir du serveur distant.|  
  
## <a name="remarks"></a>Notes  
 Utilisez sp_helpserver pour afficher la liste des noms des serveurs distants définis sur le serveur local.  
  
## <a name="permissions"></a>Autorisations  
 Aucune autorisation n’est vérifiée.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-reporting-help-on-a-single-server"></a>R. Affichage de l'aide sur un seul serveur  
 L'exemple suivant affiche des informations sur tous les utilisateurs distants du serveur distant `Accounts`.  
  
```  
EXEC sp_helpremotelogin 'Accounts';  
```  
  
### <a name="b-reporting-help-on-all-remote-users"></a>B. Affichage de l'aide sur tous les utilisateurs distants  
 L'exemple suivant affiche des informations sur tous les utilisateurs distants de tous les serveurs distants connus sur le serveur local.  
  
```  
EXEC sp_helpremotelogin;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
