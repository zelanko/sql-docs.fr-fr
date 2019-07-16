---
title: sp_revoke_proxy_from_subsystem (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revoke_login_from_subsystem
- sp_revoke_login_from_subsystem_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revoke_proxy_from_subsystem
ms.assetid: b87bc8ba-3ea8-4aed-b54b-32c3d82d9d2a
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8901c46c5654b6c633e03d62e8eaec2a3e903e02
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022272"
---
# <a name="sprevokeproxyfromsubsystem-transact-sql"></a>sp_revoke_proxy_from_subsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Interdit à un proxy d'accéder à un sous-système.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_revoke_proxy_from_subsystem   
    [ @proxy_id = ] proxy_id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @subsystem_id = ] subsystem_id,  
    [ @subsystem_name = ] 'subsystem_name'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @proxy_id = ] id` Le numéro d’identification du proxy à révoquer l’accès à partir de. Le *proxy_id* est **int**, avec NULL comme valeur par défaut. Soit *proxy_id* ou *proxy_name* doit être spécifié, mais ne peut pas être spécifiés.  
  
`[ @proxy_name = ] 'proxy_name'` Le nom du proxy à révoquer l’accès à partir de. Le *proxy_name* est **sysname**, avec NULL comme valeur par défaut. Soit *proxy_id* ou *proxy_name* doit être spécifié, mais ne peut pas être spécifiés.  
  
`[ @subsystem_id = ] id` Numéro d’identification du sous-système auquel révoquer l’accès à. Le *subsystem_id* est **int**, avec NULL comme valeur par défaut. Soit *subsystem_id* ou *subsystem_name* doit être spécifié, mais ne peut pas être spécifiés. Le tableau suivant répertorie les valeurs possibles pour chaque sous-système.  
  
|Value|Description|  
|-----------|-----------------|  
|**2**|Script ActiveX<br /><br /> **\*\* Important \* \***  sous-système de la création de scripts ActiveX sera supprimé à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans une future version de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité.|  
|**3**|Système d'exploitation (CmdExec)|  
|**4**|Agent d'instantané de réplication|  
|**5**|Agent de lecture du journal des réplications|  
|**6**|Agent de distribution de réplication|  
|**7**|Replication Merge Agent|  
|**8**|Agent de lecture de la file d'attente de réplication|  
|**9**|Commandes Analysis Services|  
|**10**|Requête Analysis Services|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)] Exécution du package|  
|**12**|script PowerShell|  
  
`[ @subsystem_name = ] 'subsystem_name'` Le nom du sous-système auquel révoquer l’accès à. Le *subsystem_name* est **sysname**, avec NULL comme valeur par défaut. Soit *subsystem_id* ou *subsystem_name* doit être spécifié, mais ne peut pas être spécifiés. Le tableau suivant répertorie les valeurs possibles pour chaque sous-système.  
  
|Value|Description|  
|-----------|-----------------|  
|ActiveScripting|Script ActiveX|  
|CmdExec|Système d'exploitation (CmdExec)|  
|Instantané|Agent d'instantané de réplication|  
|LogReader|Agent de lecture du journal des réplications|  
|Distribution|Agent de distribution de réplication|  
|Fusion|Replication Merge Agent|  
|QueueReader|Agent de lecture de la file d'attente de réplication|  
|ANALYSISQUERY|Commandes Analysis Services|  
|ANALYSISCOMMAND|Requête Analysis Services|  
|Dts|[!INCLUDE[ssIS](../../includes/ssis-md.md)] Exécution du package|  
|PowerShell|script PowerShell|  
  
## <a name="remarks"></a>Notes  
 Refuser l'accès à un sous-système ne change en rien les autorisations accordées au principal spécifié dans le proxy.  
  
> [!NOTE]  
>  Pour déterminer les étapes de travail référencent un proxy, cliquez sur le **proxys** nœud sous **Agent SQL Server** dans Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis cliquez sur **propriétés**. Dans le **propriétés du compte Proxy** boîte de dialogue, sélectionnez le **références** page pour afficher toutes les étapes de travail qui font référence à ce proxy.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_revoke_proxy_from_subsystem**.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant refuse l'accès au sous-système [!INCLUDE[ssIS](../../includes/ssis-md.md)] au proxy `Catalog application proxy`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_revoke_proxy_from_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_name = N'Dts';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de SQL Server Agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Implémenter la sécurité SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
