---
title: sp_grant_proxy_to_subsystem (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_subsystem_TSQL
- sp_grant_login_to_subsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grant_proxy_to_subsystem
ms.assetid: 866aaa27-a1e0-453a-9b1b-af39431ad9c2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 96e044b94244492202058d6dc2b2f048a9c1db6c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68123820"
---
# <a name="sp_grant_proxy_to_subsystem-transact-sql"></a>sp_grant_proxy_to_subsystem (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Accorde à un proxy le droit d'accéder à un sous-système.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_grant_proxy_to_subsystem  
     { [ @proxy_id = ] proxy_id | [ @proxy_name = ] 'proxy_name' },  
     { [ @subsystem_id = ] subsystem_id | [ @subsystem_name = ] 'subsystem_name' }  
```  
  
## <a name="arguments"></a>Arguments  
`[ @proxy_id = ] id`Numéro d’identification du proxy auquel accorder l’accès. *Proxy_id* est de **type int**, avec NULL comme valeur par défaut. *Proxy_id* ou *proxy_name* doivent être spécifiés, mais ne peuvent pas être spécifiés.  
  
`[ @proxy_name = ] 'proxy_name'`Nom du proxy pour lequel l’accès doit être accordé. *Proxy_name* est de **type sysname**, avec NULL comme valeur par défaut. *Proxy_id* ou *proxy_name* doivent être spécifiés, mais ne peuvent pas être spécifiés.  
  
`[ @subsystem_id = ] id`Numéro d’identification du sous-système auquel accorder l’accès. *Subsystem_id* est de **type int**, avec NULL comme valeur par défaut. *Subsystem_id* ou *subsystem_name* doivent être spécifiés, mais ne peuvent pas être spécifiés. Le tableau suivant répertorie les valeurs possibles pour chaque sous-système.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**2**|[!INCLUDE[msCoName](../../includes/msconame-md.md)]Script ActiveX<br /><br /> ** \* Important \* \* ** Le sous-système de script ActiveX sera supprimé de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’agent dans une version future [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité.|  
|**1,3**|Système d’exploitation (**CmdExec**)|  
|**4**|Agent d'instantané de réplication|  
|**5,5**|Agent de lecture du journal des réplications|  
|**6**|Agent de distribution de réplication|  
|**7**|Replication Merge Agent|  
|**version8**|Agent de lecture de la file d'attente de réplication|  
|**0,9**|Requête Analysis Services|  
|**10**|Commandes Analysis Services|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)]exécution du package|  
|**12**|Script PowerShell|  
| &nbsp; | &nbsp; |
  
`[ @subsystem_name = ] 'subsystem_name'`Nom du sous-système auquel accorder l’accès. **Subsystem_name** est de **type sysname**, avec NULL comme valeur par défaut. *Subsystem_id* ou *subsystem_name* doivent être spécifiés, mais ne peuvent pas être spécifiés. Le tableau suivant répertorie les valeurs possibles pour chaque sous-système.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**ActiveScripting**|Script ActiveX|  
|**CmdExec**|Système d’exploitation (**CmdExec**)|  
|**Instantané**|Agent d'instantané de réplication|  
|**Lecteur**|Agent de lecture du journal des réplications|  
|**Distribution**|Agent de distribution de réplication|  
|**Fusionner**|Replication Merge Agent|  
|**QueueReader**|Agent de lecture de la file d'attente de réplication|  
|**ANALYSISQUERY**|Requête Analysis Services|  
|**ANALYSISCOMMAND**|Commandes Analysis Services|  
|**DTS**|Exécution des packages SSIS|  
|**PowerShell**|Script PowerShell|  
| &nbsp; | &nbsp; |
  
## <a name="remarks"></a>Notes  
 Autoriser un proxy à accéder à un sous-système ne modifie pas les autorisations pour le principal spécifié dans le proxy.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_grant_proxy_to_subsystem**.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-granting-access-to-a-subsystem-by-id"></a>R. Octroi du droit d'accès à un sous-système par numéro d'identification  
 L'exemple suivant accorde au proxy `Catalog application proxy` le droit d'accès au sous-système ActiveX Scripting.  
  
```sql
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_id = 2;  
GO  
```  
  
### <a name="b-granting-access-to-a-subsystem-by-name"></a>B. Octroi du droit d'accès à un sous-système par nom  
 L'exemple suivant accorde au proxy `Catalog application proxy` le droit d'accès au sous-système d'exécution du package SSIS.  
  
```sql
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
  
  
