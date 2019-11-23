---
title: sp_update_proxy (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_proxy
- sp_update_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER PROXY statement
- sp_update_proxy
ms.assetid: 864fd0e6-9d61-4f07-92ef-145318d2f881
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ec6c40abd080c86722565762fab3b4f9d30bd0c0
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305309"
---
# <a name="sp_update_proxy-transact-sql"></a>sp_update_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés d'un proxy existant.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_update_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @new_name = ] 'new_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @proxy_id = ] id` le numéro d’identification du proxy à modifier. *Proxy_id* est de **type int**, avec NULL comme valeur par défaut.  
  
`[ @proxy_name = ] 'proxy_name'` le nom du proxy à modifier. *Proxy_name* est de **type sysname**, avec NULL comme valeur par défaut.  
  
`[ @credential_name = ] 'credential_name'` le nom des nouvelles informations d’identification pour le proxy. *Credential_name* est de **type sysname**, avec NULL comme valeur par défaut. *Credential_name* ou *credential_id* peuvent être spécifiés.  
  
`[ @credential_id = ] credential_id` le numéro d’identification des nouvelles informations d’identification pour le proxy. *Credential_id* est de **type int**, avec NULL comme valeur par défaut. *Credential_name* ou *credential_id* peuvent être spécifiés.  
  
`[ @new_name = ] 'new_name'` le nouveau nom du proxy. *New_name* est de **type sysname**, avec NULL comme valeur par défaut. Lorsqu’elle est fournie, la procédure modifie le nom du proxy en *new_name*. Si cet argument est NULL, le nom du proxy reste inchangé.  
  
`[ @enabled = ] is_enabled` est si le proxy est activé. L’indicateur de *is_enabled* est de **type tinyint**, avec NULL comme valeur par défaut. Lorsque *is_enabled* a la **valeur 0**, le proxy n’est pas activé et ne peut pas être utilisé par une étape de travail. Si cet argument est NULL, l'état du proxy reste inchangé.  
  
`[ @description = ] 'description'` la nouvelle description du proxy. La *Description* est de type **nvarchar (512)** , avec NULL comme valeur par défaut. Si cet argument est NULL, la description du proxy reste inchangé.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **\@proxy_name** ou **\@proxy_id** doit être spécifié. Si ces deux arguments sont spécifiés, ils doivent tous les deux référencer le même proxy, sinon la procédure stockée échoue.  
  
 **\@credential_name** ou **\@credential_id** doivent être spécifiés pour modifier les informations d’identification du proxy. Si ces deux arguments sont spécifiés, ils doivent tous les deux référencer les mêmes informations d'identification, sinon la procédure stockée échoue.  
  
 Cette procédure modifie le proxy sans modifier son accès. Pour modifier l’accès à un proxy, utilisez **sp_grant_login_to_proxy** et **sp_revoke_login_from_proxy**.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle de sécurité fixe **sysadmin** peuvent exécuter cette procédure.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant définit la valeur enabled pour le proxy `Catalog application proxy` sur `0`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 0;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures &#40;stockées SQL Server Agent Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Implémenter SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md)  de sécurité  
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
