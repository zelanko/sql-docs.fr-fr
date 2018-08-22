---
title: sp_grant_proxy_to_subsystem (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_subsystem_TSQL
- sp_grant_login_to_subsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grant_proxy_to_subsystem
ms.assetid: 866aaa27-a1e0-453a-9b1b-af39431ad9c2
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6c8764394ad12a3080a03970a252bfc5a7f56099
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394670"
---
# <a name="spgrantproxytosubsystem-transact-sql"></a>sp_grant_proxy_to_subsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Accorde à un proxy le droit d'accéder à un sous-système.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_grant_proxy_to_subsystem  
     { [ @proxy_id = ] proxy_id | [ @proxy_name = ] 'proxy_name' },  
     { [ @subsystem_id = ] subsystem_id | [ @subsystem_name = ] 'subsystem_name' }  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@proxy_id =** ] *id*  
 Numéro d'identification du proxy pour lequel le droit l'accès est octroyé. Le *proxy_id* est **int**, avec NULL comme valeur par défaut. Soit *proxy_id* ou *proxy_name* doit être spécifié, mais ne peut pas être spécifiés.  
  
 [  **@proxy_name =** ] **'***proxy_name***'**  
 Nom du proxy pour lequel le droit d'accès est octroyé. Le *proxy_name* est **sysname**, avec NULL comme valeur par défaut. Soit *proxy_id* ou *proxy_name* doit être spécifié, mais ne peut pas être spécifiés.  
  
 [  **@subsystem_id =** ] *id*  
 Numéro d'identification du sous-système auquel le droit d'accès est octroyé. Le *subsystem_id* est **int**, avec NULL comme valeur par défaut. Soit *subsystem_id* ou *subsystem_name* doit être spécifié, mais ne peut pas être spécifiés. Le tableau suivant répertorie les valeurs possibles pour chaque sous-système.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**2**|Script [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX<br /><br /> **\*\* Important \* \***  sous-système de la création de scripts ActiveX sera supprimé à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans une future version de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité.|  
|**3**|Système d’exploitation (**CmdExec**)|  
|**4**|Agent d'instantané de réplication|  
|**5**|Agent de lecture du journal des réplications|  
|**6**|Agent de distribution de réplication|  
|**7**|Replication Merge Agent|  
|**8**|Agent de lecture de la file d'attente de réplication|  
|**9**|Requête Analysis Services|  
|**10**|Commandes Analysis Services|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)] Exécution du package|  
|**12**|script PowerShell|  
  
 [  **@subsystem_name =** ] **'***subsystem_name***'**  
 Nom du sous-système auquel le droit d'accès est octroyé. Le **subsystem_name** est **sysname**, avec NULL comme valeur par défaut. Soit *subsystem_id* ou *subsystem_name* doit être spécifié, mais ne peut pas être spécifiés. Le tableau suivant répertorie les valeurs possibles pour chaque sous-système.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**ActiveScripting**|Script ActiveX|  
|**CmdExec**|Système d’exploitation (**CmdExec**)|  
|**Snapshot**|Agent d'instantané de réplication|  
|**LogReader**|Agent de lecture du journal des réplications|  
|**Distribution**|Agent de Distribution de réplication|  
|**Fusion**|Replication Merge Agent|  
|**QueueReader**|Agent de lecture de la file d'attente de réplication|  
|**ANALYSISQUERY**|Requête Analysis Services|  
|**ANALYSISCOMMAND**|Commandes Analysis Services|  
|**Dts**|Exécution de package SSIS|  
|**PowerShell**|script PowerShell|  
  
## <a name="remarks"></a>Notes  
 Autoriser un proxy à accéder à un sous-système ne modifie pas les autorisations pour le principal spécifié dans le proxy.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_grant_proxy_to_subsystem**.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-granting-access-to-a-subsystem-by-id"></a>A. Octroi du droit d'accès à un sous-système par numéro d'identification  
 L'exemple suivant accorde au proxy `Catalog application proxy` le droit d'accès au sous-système ActiveX Scripting.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_id = 2;  
GO  
```  
  
### <a name="b-granting-access-to-a-subsystem-by-name"></a>B. Octroi du droit d'accès à un sous-système par nom  
 L'exemple suivant accorde au proxy `Catalog application proxy` le droit d'accès au sous-système d'exécution du package SSIS.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = N'Catalog application proxy',  
    @subsystem_name = N'Dts' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter la sécurité SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_revoke_proxy_from_subsystem &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-proxy-from-subsystem-transact-sql.md)   
 [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_update_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-proxy-transact-sql.md)  
  
  
