---
title: sp_replmonitorsubscriptionpendingcmds (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorsubscriptionpendingcmds_TSQL
- sp_replmonitorsubscriptionpendingcmds
helpviewer_keywords:
- sp_replmonitorsubscriptionpendingcmds
ms.assetid: df5b955a-feb0-4863-9b3b-7f71e9653b3d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6059c4834c37c3c61227fdaf3c9ea3c94e1b5b9a
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770899"
---
# <a name="sp_replmonitorsubscriptionpendingcmds-transact-sql"></a>sp_replmonitorsubscriptionpendingcmds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Renvoie des informations sur le nombre de commandes en attente pour un abonnement à une publication transactionnelle et une estimation approximative de la durée de leur traitement. Cette procédure stockée renvoie une ligne pour chaque abonnement renvoyé. Cette procédure stockée, utilisée pour surveiller la réplication, est exécutée sur la base de données du serveur de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replmonitorsubscriptionpendingcmds [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @subscriber_db = ] 'subscriber_db'   
        , [ @subscription_type = ] subscription_type  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'`Nom de la base de données publiée. *publisher_db* est de **type sysname**, sans valeur par défaut.  
  
`[ @publication = ] 'publication'`Nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @subscriber = ] 'subscriber'`Nom de l’abonné. Subscriber est de **type sysname**, sans valeur par défaut.  
  
`[ @subscriber_db = ] 'subscriber_db'`Nom de la base de données d’abonnement. *subscriber_db* est de **type sysname**, sans valeur par défaut.  
  
`[ @subscription_type = ] subscription_type`Si le type d’abonnement. *publication_type* est de **type int**, sans valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**0**|Abonnement par envoi de données (push)|  
|**1**|Abonnement par extraction de données (pull)|  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**pendingcmdcount**|**Int**|Nombre de commandes en attente pour l'abonnement.|  
|**estimatedprocesstime**|**int**|Estimation du nombre de secondes nécessaires pour envoyer toutes les commandes en attente à l'Abonné.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_replmonitorsubscriptionpendingcmds** est utilisé avec la réplication transactionnelle.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** sur le serveur de distribution ou les membres du rôle de base de données fixe **db_owner** dans la base de données de distribution peuvent exécuter **sp_replmonitorsubscriptionpendingcmds**. Les membres de la liste d’accès à la publication pour une publication qui utilise la base de données de distribution peuvent exécuter **sp_replmonitorsubscriptionpendingcmds** pour retourner des commandes en attente pour cette publication.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller la réplication par programmation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
