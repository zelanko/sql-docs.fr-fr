---
title: sp_helpdistributor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistributor_TSQL
- sp_helpdistributor
helpviewer_keywords:
- sp_helpdistributor
ms.assetid: 37b0983e-3b69-4f0f-977e-20efce0a0b97
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42c350876037c83505860c65b26f4302d75b6eed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122555"
---
# <a name="sphelpdistributor-transact-sql"></a>sp_helpdistributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie des informations sur le serveur de distribution, la base de données de distribution, le répertoire de travail, et [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte d’utilisateur de l’Agent. Cette procédure stockée est exécutée sur la base de données de publication du serveur de publication ou sur n'importe quelle base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpdistributor [ [ @distributor= ] 'distributor' OUTPUT ]  
    [ , [ @distribdb= ] 'distribdb' OUTPUT ]  
    [ , [ @directory= ] 'directory' OUTPUT ]  
    [ , [ @account= ] 'account' OUTPUT ]  
    [ , [ @min_distretention= ] min_distretention OUTPUT ]  
    [ , [ @max_distretention= ] max_distretention OUTPUT ]  
    [ , [ @history_retention= ] history_retention OUTPUT ]  
    [ , [ @history_cleanupagent= ] 'history_cleanupagent' OUTPUT ]  
    [ , [ @distrib_cleanupagent = ] 'distrib_cleanupagent' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @local = ] 'local' ]  
    [ , [ @rpcsrvname= ] 'rpcsrvname' OUTPUT ]  
    [ , [ @publisher_type = ] 'publisher_type' OUTPUT ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @distributor = ] 'distributor' OUTPUT` Est le nom du serveur de distribution. Serveur de distribution est **sysname**, avec une valeur par défaut **%** , qui est la seule valeur qui retourne un jeu de résultats.  
  
`[ @distribdb = ] 'distribdb' OUTPUT` Est le nom de la base de données de distribution. *base_de_données_de_distribution* est **sysname**, avec une valeur par défaut **%** , qui est la seule valeur qui retourne un jeu de résultats.  
  
`[ @directory = ] 'directory' OUTPUT` Est le répertoire de travail. *répertoire* est **nvarchar (255)** , avec une valeur par défaut **%** , qui est la seule valeur qui retourne un jeu de résultats.  
  
`[ @account = ] 'account' OUTPUT` Est le [!INCLUDE[msCoName](../../includes/msconame-md.md)] compte d’utilisateur Windows. *compte*est **nvarchar (255)** , avec une valeur par défaut **%** , qui est la seule valeur qui retourne un jeu de résultats.  
  
`[ @min_distretention = ] _min_distretentionOUTPUT` Est la période de rétention de distribution minimale, en heures. *rétention_de_distribution_minimale* est **int**, avec une valeur par défaut **-1**.  
  
`[ @max_distretention = ] _max_distretentionOUTPUT` Est la période de rétention de distribution maximale, en heures. *max_distretention* est **int**, avec une valeur par défaut **-1**.  
  
`[ @history_retention = ] _history_retentionOUTPUT` Est la période de rétention de l’historique, en heures. *history_retention* est **int**, avec une valeur par défaut **-1**.  
  
`[ @history_cleanupagent = ] 'history_cleanupagent' OUTPUT` Est le nom de l’agent de nettoyage d’historique. *history_cleanupagent* est **nvarchar (100)** , avec une valeur par défaut **%** , qui est la seule valeur qui retourne un jeu de résultats.  
  
`[ @distrib_cleanupagent = ] 'distrib_cleanupagent' OUTPUT` Est le nom de l’agent de nettoyage de distribution. *agent_de_nettoyage_de_distribution* est **nvarchar (100)** , avec une valeur par défaut **%** , qui est la seule valeur qui retourne un jeu de résultats.  
  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @local = ] 'local'` Est si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit obtenir les valeurs de serveur local. *local* est **nvarchar (5)** , avec NULL comme valeur par défaut.  
  
`[ @rpcsrvname = ] 'rpcsrvname' OUTPUT` Est le nom du serveur qui émet des appels de procédure distante. *nom_rpcsrv* est **sysname**, avec une valeur par défaut **%** , qui est la seule valeur qui retourne un jeu de résultats.  
  
`[ @publisher_type = ] 'publisher_type' OUTPUT` Est le type de serveur de publication du serveur de publication. *publisher_type* est **sysname**, avec une valeur par défaut **%** , qui est la seule valeur qui retourne un jeu de résultats.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**distributor**|**sysname**|Nom du serveur de distribution.|  
|**base de données de distribution**|**sysname**|Nom de la base de données de distribution.|  
|**directory**|**nvarchar(255)**|Nom du répertoire de travail.|  
|**account**|**nvarchar(255)**|Nom du compte d'utilisateur Windows.|  
|**rétention de distrib min**|**int**|Période de rétention de distribution minimale.|  
|**rétention de distrib max**|**int**|Période maximale de rétention de distribution.|  
|**rétention de l’historique**|**int**|Période de rétention de l'historique.|  
|**agent de nettoyage d’historique**|**nvarchar(100)**|Nom de l'Agent de nettoyage de l'historique|  
|**agent de nettoyage de distribution**|**nvarchar(100)**|Nom de l'Agent de nettoyage de distribution.|  
|**nom du serveur RPC**|**sysname**|Nom du serveur de distribution local ou distant.|  
|**nom de connexion RPC**|**sysname**|Connexion utilisée pour les appels de procédure à distance au serveur de distribution distant.|  
|**type de serveur de publication**|**sysname**|Type de serveur de publication ; il peut s'agir d'une des valeurs suivantes :<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpdistributor** est utilisée dans tous les types de réplication.  
  
 Si un ou plusieurs paramètres de sortie sont spécifiés lors de l’exécution **sp_helpdistributor**, tous les paramètres de sortie la valeur NULL sont affectées des valeurs à la sortie et aucun jeu de résultats n’est renvoyée. Si aucun paramètre de sortie n'est spécifié, un ensemble de résultats est retourné.  
  
## <a name="permissions"></a>Autorisations  
 Le résultat suivant définie les colonnes ou paramètres de sortie sont retournés aux membres de la **sysadmin** rôle serveur fixe sur le serveur de publication et la **db_owner** rôle de base de données fixe sur la base de données de publication :  
  
|Colonne de l'ensemble de résultats|Paramètre de sortie|  
|-----------------------|----------------------|  
|account|**@account**|  
|min distrib retention|**@min_distretention**|  
|max distrib retention|**@max_distretention**|  
|history retention|**@history_retention**|  
|history cleanup agent|**@history_cleanupagent**|  
|distribution cleanup agent|**@distrib_cleanupagent**|  
|rpc login name|none|  
  
 La colonne de l'ensemble de résultats suivante est retournée aux utilisateurs dans la liste d'accès aux publications sur le serveur de distribution :  
  
-   directory  
  
 Les colonnes de l'ensemble de résultats suivantes sont retournées à tous les utilisateurs.  
  
|Colonne de l'ensemble de résultats|Paramètre de sortie|  
|-----------------------|----------------------|  
|distributor|**@distributor**|  
|distribution database|**@distribdb**|  
|rpc server name|**@rpcsrvname**|  
|publisher type|**@publisher_type**|  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
