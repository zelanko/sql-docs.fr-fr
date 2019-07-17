---
title: sp_deletetracertokenhistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletetracertokenhistory
- sp_deletetracertokenhistory_TSQL
helpviewer_keywords:
- sp_deletetracertokenhistory
ms.assetid: 9ae1be14-0d2f-40b1-9d6e-22d79726abf4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a7f70f5cd56867add98150d471d61cbc70faad0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111921"
---
# <a name="spdeletetracertokenhistory-transact-sql"></a>sp_deletetracertokenhistory (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Supprime les enregistrements de jeton de suivi le [MStracer_tokens &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) et [MStracer_history &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-history-transact-sql.md) tables système. Cette procédure stockée est exécutée sur la base de données de publication du serveur de publication ou sur la base de données de distribution du serveur de distribution.

![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Syntaxe

```
sp_deletetracertokenhistory [ @publication = ] 'publication'
    [ , [ @tracer_id = ] tracer_id ]
    [ , [ @cutoff_date = ] cutoff_date ]
    [ , [ @publisher = ] 'publisher' ]
    [ , [ @publisher_db = ] 'publisher_db' ]
```

## <a name="arguments"></a>Arguments

`@publication= 'publication'`  
Nom de la publication dans laquelle le jeton de suivi a été inséré. Le type de données est **sysname**. Ce paramètre est obligatoire.

`[ @tracer_id= ] tracer_id`  
ID du jeton de suivi à supprimer. Le type de données est **int**. La valeur par défaut est *null*. Si *null*, tous les jetons de suivi appartenant à la publication sont supprimés.

`[ @cutoff_date= ] cutoff_date`  
Jetons de suivi insérés dans la publication avant cette date soient supprimés. Le type de données est **datetime**. La valeur par défaut est *null*.

`[ @publisher= ] 'publisher'`  
Nom du serveur de publication. Le type de données est **sysname**. La valeur par défaut est *null*.

> [!NOTE]
> Ce paramètre ne doit être spécifié pour les non - [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication ou de l’exécution de la procédure stockée à partir du serveur de distribution.

`[ @publisher_db= ] 'publisher_db'`  
Nom de la base de données de publication. Le type de données est **sysname**. La valeur par défaut est NULL. Ce paramètre est ignoré si la procédure stockée est exécutée sur le serveur de publication.

> [!NOTE]
> Ce paramètre doit être spécifié lors de l’exécution de la procédure stockée à partir du serveur de distribution.

## <a name="return-code-values"></a>Valeurs des codes de retour

**0** (réussite) ou **1** (échec)

## <a name="remarks"></a>Notes

**sp_deletetracertokenhistory** est utilisé dans la réplication transactionnelle.  

Une erreur se produit si vous spécifiez les deux paramètres *tracer_id* et *cutoff_date*.

Si vous n’exécutez pas **sp_deletetracertokenhistory** pour supprimer les métadonnées de jeton de suivi, les informations sont supprimées lorsque le nettoyage d’historique se produit.

ID de jeton de suivi peuvent être déterminées en exécutant [sp_helptracertokens &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) ou en interrogeant le [MStracer_tokens &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) (table système).

## <a name="permissions"></a>Autorisations

Seul le personnel suivant a l’autorité nécessaire pour exécuter **sp_deletetracertokenhistory**:

- Membres de la **replmonitor** rôles, dans la base de données de distribution
- Membres de la **sysadmin** rôle serveur fixe.
- Membres de la **db_owner** rôle de base de données fixe, dans la base de données de publication.
- Le **db_owner** de la base de données fixe.

## <a name="see-also"></a>Voir aussi

[Mesurer la latence et valider les connexions pour la réplication transactionnelle](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)

[sp_helptracertokenhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)
