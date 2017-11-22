---
title: sp_add_proxy (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_add_proxy
- sp_add_proxy_TSQL
dev_langs: TSQL
helpviewer_keywords:
- CREATE PROXY statement
- sp_add_proxy
ms.assetid: cb59df37-f103-439b-bec1-2871fb669a8b
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 40c2684a017c7b6da34bb945499b04bbff5bc5f7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="spaddproxy-transact-sql"></a>sp_add_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute le proxy [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent spécifié.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_add_proxy  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description' ,  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @proxy_id = ] id OUTPUT   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@proxy_name** =] **'***proxy_name***'**  
 Nom du proxy à créer. Le *proxy_name* est **sysname**, avec NULL comme valeur par défaut. Lorsque le *proxy_name* est NULL ou une chaîne vide, le nom du proxy par défaut, la *nom_utilisateur* fourni.  
  
 [  **@enabled**  =] *is_enabled*  
 Indique si le proxy est activé. Le *is_enabled* indicateur est **tinyint**, avec 1 comme valeur par défaut. Lorsque *is_enabled* est **0**, le proxy n’est pas activé et ne peut pas être utilisé par une étape de travail.  
  
 [  **@description** =] **'***description***'**  
 Description du proxy. La description est **nvarchar (512)**, avec NULL comme valeur par défaut. La description vous permet de documenter le proxy, mais elle n'est pas utilisée à d'autres fins par l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cet argument est donc facultatif.  
  
 [  **@credential_name**  =] **'***credential_name***'**  
 Nom relatif aux informations d'identification du proxy. Le *credential_name* est **sysname**, avec NULL comme valeur par défaut. Soit *credential_name* ou *credential_id* doit être spécifié.  
  
 [  **@credential_id**  =] *credential_id*  
 Numéro d'identification relatif aux informations d'identification du proxy. Le *credential_id* est **int**, avec NULL comme valeur par défaut. Soit *credential_name* ou *credential_id* doit être spécifié.  
  
 [  **@proxy_id** =] *id* sortie  
 Numéro d'identification attribué au proxy en cas de création réussie.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="remarks"></a>Notes  
 Cette procédure stockée doit être exécutée le **msdb** base de données.  
  
 Un proxy de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère la sécurité des étapes de travail qui impliquent des sous-systèmes autres que le sous-système [!INCLUDE[tsql](../../includes/tsql-md.md)]. Chaque proxy correspond à des informations d'identification de sécurité. Un proxy peut avoir accès à plusieurs sous-systèmes.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle de sécurité fixe peut exécuter cette procédure.  
  
 Membres de la **sysadmin** rôle de sécurité fixe peut créer des étapes de travail qui utilisent n’importe quel proxy. Utilisez la procédure stockée [sp_grant_login_to_proxy &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md) accorder d’autres connexions à accéder au proxy.  
  
## <a name="examples"></a>Exemples  
 Cet exemple crée un proxy pour les informations d'identification `CatalogApplicationCredential`. Le code part du principe que les informations d'identification existent déjà. Pour plus d’informations sur les informations d’identification, consultez [CREATE CREDENTIAL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-credential-transact-sql.md).  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 1,  
    @description = 'Maintenance tasks on catalog application.',  
    @credential_name = 'CatalogApplicationCredential' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_grant_login_to_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
