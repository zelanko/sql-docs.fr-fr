---
title: "SUPPRIMER l’abonnement aux notifications de requête (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- KILL QUERY NOTIFICATION SUBSCRIPTION
- KILL_QUERY_NOTIFICATION_SUBSCRIPTION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- KILL QUERY NOTIFICATION SUBSCRIPTION statement
- removing subscriptions
- subscriptions [SQL Server query notifications], stopping
- query notifications [SQL Server], subscriptions
ms.assetid: 8aeadf51-286c-4748-bef2-d25858b250bf
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e9c1a2a3af3ce113573fe743aa2325ae0b49cc18
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
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
 Supprime l’abonnement avec l’id d’abonnement *ID_ABONNEMENT*.  
  
## <a name="remarks"></a>Notes  
 L'instruction KILL QUERY NOTIFICATION SUBSCRIPTION supprime les abonnements aux notifications de requêtes sans produire de message de notification.  
  
 *subscription_id* est l’id de l’abonnement, comme indiqué dans la vue de gestion dynamique [sys.dm_qn_subscriptions &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md).  
  
 Si l'identificateur d'abonnement spécifié n'existe pas, l'instruction aboutit à une erreur.  
  
## <a name="permissions"></a>Autorisations  
 Autorisation d’exécuter cette instruction est limitée aux membres de la **sysadmin** rôle serveur fixe.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_qn_subscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md)  
  
  
