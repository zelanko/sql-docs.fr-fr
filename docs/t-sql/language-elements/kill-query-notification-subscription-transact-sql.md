---
title: KILL QUERY NOTIFICATION SUBSCRIPTION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/27/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- KILL QUERY NOTIFICATION SUBSCRIPTION
- KILL_QUERY_NOTIFICATION_SUBSCRIPTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- KILL QUERY NOTIFICATION SUBSCRIPTION statement
- removing subscriptions
- subscriptions [SQL Server query notifications], stopping
- query notifications [SQL Server], subscriptions
ms.assetid: 8aeadf51-286c-4748-bef2-d25858b250bf
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2cb16e1a8abe807149caed9e5b520cae0d8f44c7
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65982209"
---
# <a name="kill-query-notification-subscription-transact-sql"></a>KILL QUERY NOTIFICATION SUBSCRIPTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime les abonnements aux notifications de requêtes de l'instance. Cette instruction peut supprimer un abonnement spécifique, ou bien tous les abonnements.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
KILL QUERY NOTIFICATION SUBSCRIPTION   
   { ALL | subscription_id }  
```  
  
## <a name="arguments"></a>Arguments  
 ALL  
 Supprime tous les abonnements de l'instance.  
  
 *subscription_id*  
 Supprime l’abonnement doté de l’identificateur *subscription_id*.  
  
## <a name="remarks"></a>Notes   
 L'instruction KILL QUERY NOTIFICATION SUBSCRIPTION supprime les abonnements aux notifications de requêtes sans produire de message de notification.  
  
 *subscription_id* est l’ID de l’abonnement, comme indiqué dans la vue de gestion dynamique [sys.dm_qn_subscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md).  
  
 Si l'identificateur d'abonnement spécifié n'existe pas, l'instruction aboutit à une erreur.  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution de cette instruction sont limitées aux membres du rôle serveur fixe **sysadmin**.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-removing-all-query-notification-subscriptions-in-the-instance"></a>A. Suppression de tous les abonnements aux notifications de requêtes de l'instance  
 L'exemple suivant supprime tous les abonnements aux notifications de requêtes de l'instance.  
  
```  
KILL QUERY NOTIFICATION SUBSCRIPTION ALL ;  
```  
  
### <a name="b-removing-a-single-query-notification-subscription"></a>B. Suppression d'un seul abonnement aux notifications de requêtes  
 L'exemple suivant supprime l'abonnement aux notifications de requêtes doté de l'identificateur `73`.  
  
```  
KILL QUERY NOTIFICATION SUBSCRIPTION 73 ;  
```  
  
## <a name="see-also"></a> Voir aussi  
 [sys.dm_qn_subscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md)  
  
  
