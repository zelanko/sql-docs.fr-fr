---
title: sp_helpqreader_agent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpqreader_agent_TSQL
- sp_helpqreader_agent
helpviewer_keywords:
- sp_helpqreader_agent
ms.assetid: 8e74e1aa-e95b-4183-8017-bf123439b08d
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea01bd3eb765a0a5f7a85245090b79579f347b3a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771421"
---
# <a name="sp_helpqreader_agent-transact-sql"></a>sp_helpqreader_agent (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Retourne les propriétés de l'Agent de lecture de la file d'attente. Cette procédure stockée est exécutée sur la base de données de distribution du serveur de distribution ou sur toute base de données du serveur de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpqreader_agent [ [ @frompublisher = ] frompublisher ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @frompublisher = ] frompublisher`Spécifie si la procédure stockée est appelée sur le serveur de publication ou sur le serveur de distribution. *frompublisher* est de bits, avec 0 comme valeur par défaut. **1** signifie que la procédure stockée est appelée à partir du serveur de publication, et **0** signifie que la procédure stockée est appelée à partir du serveur de distribution.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**identifi**|**int**|ID de l’agent.|  
|**nomme**|**nvarchar(100**|Nom de l'Agent.|  
|**job_id**|**uniqueidentifier**|ID unique du travail de l'Agent.|  
|**job_login**|**nvarchar(512)**|Compte Windows sous lequel s’exécute l’agent de distribution, qui est retourné au format *domaine*\\*nom d’utilisateur*.|  
|**job_password**|**sysname**|Pour des raisons de sécurité, la ** \* \* \* \* \* \* \* \* valeur \* ** est toujours retournée.|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpqreader_agent** est utilisé dans la réplication transactionnelle.  
  
## <a name="permissions"></a>Autorisations  
 Lorsque la valeur de *frompublisher* est **1**, seuls les membres du rôle serveur fixe **sysadmin** sur le serveur de publication ou les membres du rôle de base de données fixe **db_owner** sur la base de données de publication peuvent exécuter **sp_helpqreader_agent**. Dans le cas contraire, seuls les membres du rôle serveur fixe **sysadmin** sur le serveur de distribution ou les membres du rôle de base de données fixe **db_owner** sur la base de données de distribution peuvent exécuter **sp_helpqreader_agent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Activer les abonnements pouvant être mis à jour pour les publications transactionnelles](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
  
