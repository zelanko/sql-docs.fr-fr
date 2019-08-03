---
title: sp_browsereplcmds (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsereplcmds_TSQL
- sp_browsereplcmds
helpviewer_keywords:
- sp_browsereplcmds
ms.assetid: 30abcb41-1d18-4f43-a692-4c80914c0450
author: stevestein
ms.author: sstein
ms.openlocfilehash: d049a5e96d9c7212467595aa70cd44db727bdf6e
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768997"
---
# <a name="spbrowsereplcmds-transact-sql"></a>sp_browsereplcmds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Retourne un jeu de résultats, dans une version lisible, des commandes répliquées et stockées dans la base de données de distribution. Également utilisé en tant qu'outil de diagnostic. Cette procédure stockée est exécutée au niveau du serveur de distribution sur la base de données de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_browsereplcmds [ [ @xact_seqno_start = ] 'xact_seqno_start' ]  
    [ , [ @xact_seqno_end = ] 'xact_seqno_end' ]   
    [ , [ @originator_id = ] 'originator_id' ]  
    [ , [ @publisher_database_id = ] 'publisher_database_id' ]  
    [ , [ @article_id = ] 'article_id' ]  
    [ , [ @command_id= ] command_id ]  
    [ , [ @agent_id = ] agent_id ]  
    [ , [ @compatibility_level = ] compatibility_level ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @xact_seqno_start = ] 'xact_seqno_start'`Spécifie le numéro de séquence exact à valeur la plus faible à retourner. *xact_seqno_start* est de valeur **nchar (22)** , avec 0x00000000000000000000 comme comme valeur par défaut.  
  
`[ @xact_seqno_end = ] 'xact_seqno_end'`Spécifie le numéro de séquence exact le plus élevé à retourner. *xact_seqno_end* est de valeur **nchar (22)** , avec 0xFFFFFFFFFFFFFFFFFFFF comme valeur comme valeur par défaut.  
  
`[ @originator_id = ] 'originator_id'`Spécifie si les commandes avec le *originator_id* spécifié sont retournées. *originator_id* est de **type int**, avec NULL comme valeur par défaut.  
  
`[ @publisher_database_id = ] 'publisher_database_id'`Spécifie si les commandes avec le *publisher_database_id* spécifié sont retournées. *publisher_database_id* est de **type int**, avec NULL comme valeur par défaut.  
  
`[ @article_id = ] 'article_id'`Spécifie si les commandes avec le *article_id* spécifié sont retournées. *article_id* est de **type int**, avec NULL comme valeur par défaut.  
  
`[ @command_id = ] command_id`Est l’emplacement de la commande dans [MSrepl_commands &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msrepl-commands-transact-sql.md) à décoder. *command_id* est de **type int**, avec NULL comme valeur par défaut. Si ce paramètre est spécifié, tous les autres paramètres doivent également être spécifiés et *xact_seqno_start*doit être identique à *xact_seqno_end*.  
  
`[ @agent_id = ] agent_id`Spécifie que seules les commandes d’un agent de réplication spécifique sont renvoyées. *agent_id* est de **type int**, avec NULL comme valeur par défaut.  
  
`[ @compatibility_level = ] compatibility_level`[!INCLUDE[msCoName](../../includes/msconame-md.md)] Version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur laquelle *COMPATIBILITY_LEVEL* est de **type int**, avec une valeur par défaut de 9 millions.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**varbinary(16)**|Numéro de séquence de la commande.|  
|**originator_srvname**|**sysname**|Serveur d'origine de la transaction.|  
|**originator_db**|**sysname**|Base de données d'origine de la transaction.|  
|**article_id**|**int**|ID de l’article.|  
|**type**|**int**|Type de commande.|  
|**partial_command**|**bit**|Indique s'il s'agit d'une commande partielle.|  
|**hashkey**|**int**|À usage interne uniquement|  
|**originator_publication_id**|**int**|ID de la publication d'origine de la transaction.|  
|**originator_db_version**|**int**|Version de la base de données d'origine de la transaction.|  
|**originator_lsn**|**varbinary(16)**|Identifie le numéro séquentiel dans le journal (LSN) de la commande dans la publication d'origine. Utilisé dans la réplication transactionnelle d’égal à égal.|  
|**commande**|**nvarchar(1024)**|[!INCLUDE[tsql](../../includes/tsql-md.md)]commande.|  
|**command_id**|**int**|ID de la commande dans [MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md).|  
  
 Les commandes longues peuvent être réparties entre plusieurs lignes dans l'ensemble de résultats.  
  
## <a name="remarks"></a>Notes  
 **sp_browsereplcmds** est utilisé dans la réplication transactionnelle.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou des membres des rôles de base de données fixes **db_owner** ou **replmonitor** sur la base de données de distribution peuvent exécuter **sp_browsereplcmds**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
