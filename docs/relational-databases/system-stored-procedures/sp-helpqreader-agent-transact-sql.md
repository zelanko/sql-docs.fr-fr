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
manager: craigg
ms.openlocfilehash: f40856b20a76abdb7a3788f2564c02fe2e090619
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529341"
---
# <a name="sphelpqreaderagent-transact-sql"></a>sp_helpqreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les propriétés de l'Agent de lecture de la file d'attente. Cette procédure stockée est exécutée sur la base de données de distribution du serveur de distribution ou sur toute base de données du serveur de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpqreader_agent [ [ @frompublisher = ] frompublisher ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @frompublisher = ] frompublisher` Indique si la procédure stockée est appelée sur le serveur de publication ou sur le serveur de distribution. *frompublisher* est de type bit, avec 0 comme valeur par défaut. **1** signifie que la procédure stockée est appelée depuis le serveur de publication, et **0** signifie que la procédure stockée est appelée depuis le serveur de distribution.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|ID de l’agent.|  
|**nom**|**nvarchar(100)**|Nom de l'Agent.|  
|**job_id**|**uniqueidentifier**|ID unique du travail de l'Agent.|  
|**job_login**|**nvarchar(512)**|Est le compte Windows sous lequel l’agent de Distribution s’exécute, ce qui est retourné sous la forme *domaine*\\*nom d’utilisateur*.|  
|**job_password**|**sysname**|Pour des raisons de sécurité, la valeur **\* \* \* \* \* \* \* \* \* \*** est toujours retourné.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpqreader_agent** est utilisé dans la réplication transactionnelle.  
  
## <a name="permissions"></a>Autorisations  
 Lorsque la valeur de *frompublisher* est **1**, seuls les membres de la **sysadmin** rôle serveur fixe sur le serveur de publication ou les membres de la **db_owner**rôle de base de données fixe sur la base de données de publication peut exécuter **sp_helpqreader_agent**. Sinon, seuls les membres de la **sysadmin** rôle serveur fixe sur le serveur de distribution ou les membres de la **db_owner** rôle de base de données fixe sur la base de données de distribution peut exécuter **sp_helpqreader_ Agent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Activer les abonnements de mise à jour pour les publications transactionnelles](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
  
