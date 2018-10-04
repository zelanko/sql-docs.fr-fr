---
title: sp_replcmds (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_replcmds_TSQL
- sp_replcmds
helpviewer_keywords:
- sp_replcmds
ms.assetid: 7e932f80-cc6e-4109-8db4-2b7c8828df73
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 00fec83a709b1c3bfba352663784b5018134769d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47783490"
---
# <a name="spreplcmds-transact-sql"></a>sp_replcmds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les commandes pour les transactions signalées pour la réplication. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
> [!IMPORTANT]  
>  Le **sp_replcmds** procédure doit être uniquement exécutée pour résoudre les problèmes de réplication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@maxtrans=**] *maxtrans*  
 Nombre de transactions au sujet desquelles des informations sont retournées. *maxtrans* est **int**, avec une valeur par défaut **1**, qui spécifie la prochaine transaction en attente de distribution.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id d’article**|**Int**|L’ID de l’article.|  
|**commande_partielle**|**bit**|Indique s'il s'agit d'une commande partielle|  
|**commande**|**varbinary(1024)**|La valeur de commande.|  
|**xactid**|**binary(10)**|ID de transaction.|  
|**xact_seqno**|**varbinary(16)**|Numéro de séquence de transaction.|  
|**publication_id**|**Int**|ID de la publication.|  
|**command_id**|**Int**|ID de la commande dans [MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md).|  
|**command_type**|**Int**|Type de commande.|  
|**originator_srvname**|**sysname**|Serveur d'origine de la transaction.|  
|**originator_db**|**sysname**|Base de données d'origine de la transaction.|  
|**pkHash**|**Int**|À usage interne uniquement|  
|**originator_publication_id**|**Int**|ID de la publication d'origine de la transaction.|  
|**originator_db_version**|**Int**|Version de la base de données d'origine de la transaction.|  
|**originator_lsn**|**varbinary(16)**|Identifie le numéro séquentiel dans le journal (LSN) de la commande dans la publication d'origine.|  
  
## <a name="remarks"></a>Notes  
 **sp_replcmds** est utilisé par le processus du lecteur de journal dans la réplication transactionnelle.  
  
 La réplication traite le premier client qui exécute **sp_replcmds** au sein d’une base de données en tant que le lecteur de journal.  
  
 Cette procédure peut générer des commandes pour des tables propriétaires qualifiées, ou ne pas qualifier le nom de la table (valeur par défaut). L'ajout de noms de table qualifiés autorise la réplication des données à partir de tables appartenant à un utilisateur spécifique dans une base de données, vers des tables appartenant à ce même utilisateur dans une autre base de données.  
  
> [!NOTE]  
>  Étant donné que le nom de table figurant dans la base de données source est qualifié par le nom du propriétaire, le propriétaire de la table dans la base de données cible doit porter le même nom de propriétaire.  
  
 Les clients qui tentent d’exécuter **sp_replcmds** au sein de la même base de données l’erreur 18752 jusqu'à ce que le premier client se déconnecte. Une fois le premier client déconnecté, un autre client peut exécuter **sp_replcmds**, et devient le nouveau lecteur de journal.  
  
 Un message d’alerte numéro 18759 est ajouté à la fois à la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] journal des erreurs et le [!INCLUDE[msCoName](../../includes/msconame-md.md)] journal des applications de Windows si **sp_replcmds** est incapable de répliquer une commande de texte, car le pointeur de texte n’a pas été récupéré dans la même transaction.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_replcmds**.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
