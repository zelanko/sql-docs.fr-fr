---
title: sp_helpmergesubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergesubscription
- sp_helpmergesubscription_TSQL
helpviewer_keywords:
- sp_helpmergesubscription
ms.assetid: da564112-f769-4e67-9251-5699823e8c86
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0e5f044482d3e46e4e20279a437b8d9459d1d3bd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002641"
---
# <a name="sphelpmergesubscription-transact-sql"></a>sp_helpmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie des informations sur un abonnement à une publication de fusion, par envoi (push) et par extraction (pull) de données. Cette procédure stockée est exécutée sur la base de données de publication du serveur de publication ou sur la base de données d'abonnement d'un Abonné de republication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpmergesubscription [ [ @publication=] 'publication']  
    [ , [ @subscriber=] 'subscriber']  
    [ , [ @subscriber_db=] 'subscriber_db']  
    [ , [ @publisher=] 'publisher']  
    [ , [ @publisher_db=] 'publisher_db']  
    [ , [ @subscription_type=] 'subscription_type']  
    [ , [ @found=] 'found' OUTPUT]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, avec une valeur par défaut **%** . La publication doit déjà exister et se conformer aux règles des identificateurs. Si NULL ou **%** , plus d’informations sur toutes les publications de fusion et les abonnements dans la base de données actuelle sont retournées.  
  
`[ @subscriber = ] 'subscriber'` Est le nom de l’abonné. *abonné* est **sysname**, avec une valeur par défaut **%** . Si le paramètre a la valeur NULL ou %, des informations sur tous les abonnements à la publication donnée sont renvoyées.  
  
`[ @subscriber_db = ] 'subscriber_db'` Est le nom de la base de données d’abonnement. *bd_abonné*est **sysname**, avec une valeur par défaut **%** , qui retourne des informations sur toutes les données d’abonnement.  
  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication. Le serveur de publication doit être un serveur valide. *serveur de publication*est **sysname**, avec une valeur par défaut **%** , qui retourne des informations sur tous les serveurs de publication.  
  
`[ @publisher_db = ] 'publisher_db'` Est le nom de la base de données du serveur de publication. *publisher_db*est **sysname**, avec une valeur par défaut **%** , qui retourne des informations sur toutes les bases de données de serveur de publication.  
  
`[ @subscription_type = ] 'subscription_type'` Est le type d’abonnement. *subscription_type*est **nvarchar (15)** , et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**push** (valeur par défaut)|Abonnement par envoi de données (push)|  
|**pull**|Abonnement par extraction de données (pull)|  
|**both** (les deux)|Abonnement par envoi (push) et par extraction (pull) de données|  
  
`[ @found = ] 'found'OUTPUT` Est un indicateur pour indiquer les lignes renvoyées. *trouvé*est **int** d’un paramètre OUTPUT, avec NULL comme valeur par défaut. **1** indique la publication a été trouvée. **0** indique que la publication est introuvable.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**sysname**|Nom de l'abonnement.|  
|**publication**|**sysname**|Nom de la publication.|  
|**publisher** (serveur de publication)|**sysname**|Nom du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données du serveur de publication.|  
|**subscriber** (Abonné)|**sysname**|Nom de l'Abonné.|  
|**bd_abonné**|**sysname**|Nom de la base de données d'abonnement.|  
|**status**|**Int**|État de l’abonnement :<br /><br /> **0** = tous les travaux sont en attente de démarrage<br /><br /> **1** = une ou plusieurs travaux commencent<br /><br /> **2** = tous les travaux ont été correctement exécutées.<br /><br /> **3** = au moins un travail s’exécute.<br /><br /> **4** = tous les travaux sont planifiés et inactifs<br /><br /> **5** = au moins un travail est relancée après un échec<br /><br /> **6** = au moins un travail n’a pas pu s’exécuter avec succès|  
|**subscriber_type**|**int**|Type d'Abonné.|  
|**subscription_type**|**int**|Type d'abonnement :<br /><br /> **0** = push<br /><br /> **1** = par extraction<br /><br /> **2** = Both|  
|**priority**|**float(8)**|Numéro indiquant la priorité de l'abonnement.|  
|**sync_type**|**tinyint**|Type de synchronisation d'abonnement|  
|**description**|**nvarchar(255)**|Brève description de cet abonnement de fusion.|  
|**merge_jobid**|**binary(16)**|ID de travail de l'Agent de fusion.|  
|**full_publication**|**tinyint**|Indique si l'abonnement concerne une publication complète ou filtrée.|  
|**offload_enabled**|**bit**|Indique si le déchargement d'un Agent de réplication est configuré pour être exécuté sur l'Abonné. Si la valeur est NULL, l'exécution a lieu sur le serveur de publication.|  
|**offload_server**|**sysname**|Nom du serveur sur lequel s'exécute l'Agent.|  
|**use_interactive_resolver**|**Int**|Indique si le composant résolveur interactif est utilisé ou non au cours de la réconciliation. Si **0**, pas le résolveur interactif est utilisé.|  
|**Nom d’hôte**|**sysname**|Valeur fournie lorsqu’un abonnement est filtré par la valeur de la [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) (fonction).|  
|**subscriber_security_mode**|**smallint**|Mode de sécurité sur l’abonné, où **1** signifie que l’authentification Windows, et **0** signifie [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.|  
|**subscriber_login**|**sysname**|Nom de connexion sur l'Abonné.|  
|**subscriber_password**|**sysname**|Le mot de passe réel de l'Abonné n'est jamais renvoyé. Le résultat est masqué par un « **\*\*\*\*\*\*** » chaîne.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpmergesubscription** est utilisé dans la réplication de fusion pour retourner des informations d’abonnement stockées sur le serveur de publication ou un abonné de republication.  
  
 Pour les abonnements anonymes, le *subscription_type*valeur est toujours **1** (pull). Toutefois, vous devez exécuter [sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md) sur l’abonné pour plus d’informations sur les abonnements anonymes.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe le **db_owner** rôle de base de données fixe ou de la liste d’accès à la publication à laquelle appartient l’abonnement peut exécuter **sp_ helpmergesubscription**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
