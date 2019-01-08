---
title: sp_replshowcmds (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replshowcmds
- sp_replshowcmds_TSQL
helpviewer_keywords:
- sp_replshowcmds
ms.assetid: 199f5a74-e08e-4d02-a33c-b8ab0db20f44
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 18ccbda41c5b7683c33bc0258a05738ab227ec69
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52813314"
---
# <a name="spreplshowcmds-transact-sql"></a>sp_replshowcmds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie les commandes pour les transactions signalées pour la réplication dans un format lisible. **sp_replshowcmds** peut être exécuté que quand les connections clientes (y compris la connexion actuelle) ne lisent pas les transactions répliquées à partir du journal. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replshowcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@maxtrans** =] *maxtrans*  
 Nombre de transactions à propos desquelles retourner des informations. *maxtrans* est **int**, avec une valeur par défaut **1**, qui spécifie le nombre maximal de transactions en attente de réplication pour lequel **sp_replshowcmds** Retourne des informations.  
  
## <a name="result-sets"></a>Jeux de résultats  
 **sp_replshowcmds** est une procédure de diagnostic qui retourne des informations sur la base de données de publication à partir de laquelle elle est exécutée.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**binary(10)**|Numéro de séquence de la commande.|  
|**originator_id**|**Int**|ID de l’émetteur de commande, toujours **0**.|  
|**publisher_database_id**|**Int**|ID de la base de données serveur de publication, toujours **0**.|  
|**article_id**|**Int**|ID de l’article.|  
|**type**|**Int**|Type de commande.|  
|**commande**|**nvarchar(1024)**|[!INCLUDE[tsql](../../includes/tsql-md.md)] commande.|  
  
## <a name="remarks"></a>Notes  
 **sp_replshowcmds** est utilisé dans la réplication transactionnelle.  
  
 À l’aide de **sp_replshowcmds**, vous pouvez afficher les transactions qui ne sont pas distribuées (les transactions qui demeurent dans le journal des transactions qui n’ont pas été envoyées au serveur de distribution).  
  
 Les clients qui exécutent **sp_replshowcmds** et **sp_replcmds** au sein de la base de données même recevoir le message d’erreur 18752.  
  
 Pour éviter cette erreur, le premier client doit se déconnecter ou le rôle du client comme lecteur du journal doit être libéré par l’exécution **sp_replflush**. Une fois tous les clients déconnectés du lecteur de journal, **sp_replshowcmds** peut être exécuté avec succès.  
  
> [!NOTE]  
>  **sp_replshowcmds** doit être uniquement exécutée pour résoudre les problèmes de réplication.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_replshowcmds**.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
