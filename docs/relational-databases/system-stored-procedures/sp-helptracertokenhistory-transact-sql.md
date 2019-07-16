---
title: sp_helptracertokenhistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helptracertokenhistory_TSQL
- sp_helptracertokenhistory
helpviewer_keywords:
- sp_helptracertokenhistory
ms.assetid: 96910d1c-be76-43eb-9c93-4477e6761749
author: stevestein
ms.author: sstein
ms.openlocfilehash: a73c8e45803bc10d47ef042acebf0650ea183f61
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68048279"
---
# <a name="sphelptracertokenhistory-transact-sql"></a>sp_helptracertokenhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations de latence détaillées pour des jetons de suivi donnés, avec une ligne retournée par abonné. Cette procédure stockée est exécutée sur la base de données de publication du serveur de publication ou sur la base de données de distribution du serveur de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helptracertokenhistory [ @publication = ] 'publication'   
        , [ @tracer_id = ] tracer_id  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication dans laquelle le jeton de suivi a été inséré. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @tracer_id = ] tracer_id` Est l’ID de jeton de suivi dans le [MStracer_tokens &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) table quel l’historique des informations sont renvoyées. *tracer_id* est **int**, sans valeur par défaut.  
  
`[ @publisher = ] 'publisher'` Le nom du serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]
>  Ce paramètre ne doit être spécifié pour les non - [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication.  
  
`[ @publisher_db = ] 'publisher_db'` Le nom de la base de données de publication. *publisher_db* est **sysname**, avec NULL comme valeur par défaut. Ce paramètre est ignoré si la procédure stockée est exécutée sur le serveur de publication.  
  
## <a name="result-set"></a>Jeu de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**distributor_latency**|**bigint**|Nombre de secondes s'écoulant entre la validation de l'enregistrement du jeton de suivi sur le serveur de publication et la validation de l'enregistrement sur le serveur de distribution.|  
|**subscriber** (Abonné)|**sysname**|Nom de l'Abonné qui a reçu le jeton de suivi.|  
|**bd_abonné**|**sysname**|Nom de la base de données d'abonnement dans laquelle l'enregistrement du jeton de suivi a été inséré.|  
|**subscriber_latency**|**bigint**|Nombre de secondes s'écoulant entre la validation de l'enregistrement du jeton de suivi sur le serveur de distribution et la validation de l'enregistrement sur l'Abonné.|  
|**overall_latency**|**bigint**|Nombre de secondes s'écoulant entre la validation de l'enregistrement du jeton de suivi sur le serveur de publication et la validation de l'enregistrement du jeton sur l'Abonné.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helptracertokenhistory** est utilisé dans la réplication transactionnelle.  
  
 Exécutez [sp_helptracertokens &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) pour obtenir une liste des jetons de suivi pour la publication.  
  
 Si le jeu de résultats contient la valeur NULL, les statistiques de latence ne peuvent pas être calculées. Cela est dû au fait que le jeton de suivi n'a pas été reçu sur le serveur de distribution ou sur l'un des Abonnés.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-helptracertokenhistor_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe le **db_owner** fixe du rôle de base de données dans la base de données de publication, ou **db_owner** base de données fixe ou  **replmonitor** rôles dans la base de données de distribution peuvent exécuter **sp_helptracertokenhistory**.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesurer la latence et valider les connexions pour la réplication transactionnelle](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_deletetracertokenhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)  
  
  
