---
title: sp_helplogreader_agent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helplogreader_agent
- sp_helplogreader_agent_TSQL
helpviewer_keywords:
- sp_helplogreader_agent
ms.assetid: ff837209-e2b3-481a-a48f-8530bfe53d97
author: stevestein
ms.author: sstein
ms.openlocfilehash: b6ecac979077dd83d6549b408c8c9e4d2bd4402f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68122435"
---
# <a name="sp_helplogreader_agent-transact-sql"></a>sp_helplogreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie les propriétés du travail de l'Agent de lecture du journal pour la base de données de publication. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helplogreader_agent [ [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, avec NULL comme valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**identifi**|**int**|ID de l’agent.|  
|**nomme**|**nvarchar(100**|Nom de l'Agent.|  
|**publisher_security_mode**|**smallint**|Mode de sécurité utilisé par l'Agent lors de la connexion au serveur de publication. Il peut prendre l'une des valeurs suivantes :<br /><br /> **** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentification<br /><br /> **1** = authentification Windows.|  
|**publisher_login**|**sysname**|Nom de connexion utilisé lors de la connexion au serveur de publication.|  
|**publisher_password**|**nvarchar (524)**|Pour des raisons de sécurité, la ** \* \* \* \* \* \* \* \* valeur \* ** est toujours retournée.|  
|**job_id**|**uniqueidentifier**|ID unique du travail de l'Agent.|  
|**job_login**|**nvarchar(512)**|Compte Windows sous lequel s’exécute l’agent de lecture du journal, qui est retourné au format *domaine*\\*nom d’utilisateur*.|  
|**job_password**|**sysname**|Pour des raisons de sécurité, la ** \* \* \* \* \* \* \* \* valeur \* ** est toujours retournée.|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helplogreader_agent** est utilisé dans la réplication transactionnelle.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** sur le serveur de publication ou les membres du rôle de base de données fixe **db_owner** sur la base de données de publication peuvent exécuter **sp_helplogreader_agent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les paramètres de sécurité de la réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)   
 [sp_changelogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md)  
  
  
