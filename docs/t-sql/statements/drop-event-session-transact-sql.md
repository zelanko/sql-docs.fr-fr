---
title: DROP EVENT SESSION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_EVENT_SESSION_TSQL
- DROP EVENT SESSION
dev_langs:
- TSQL
helpviewer_keywords:
- event sessions [SQL Server]
- DROP EVENT SESSION statement
ms.assetid: 92eabe4b-24e2-43b1-978c-31a199964b90
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a1edffab8e94c9ee171b3be4203d08b23df83452
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52404444"
---
# <a name="drop-event-session-transact-sql"></a>DROP EVENT SESSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime une session d'événements.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```    
DROP EVENT SESSION event_session_name  
ON SERVER  
```  
  
## <a name="arguments"></a>Arguments  
 *event_session_name*  
 Nom d'une session d'événements existante.  
  
## <a name="remarks"></a>Notes   
 Lorsque vous supprimez une session d'événements, toutes les informations de configuration, telles que les cibles et les paramètres de session, sont totalement supprimées.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’autorisation `ALTER ANY EVENT SESSION`.  
  
## <a name="examples"></a>Exemples  
L'exemple suivant montre comment supprimer une session d'événements.  
  
```sql  
DROP EVENT SESSION evt_spin_lock_diagnosis ON SERVER;
GO
```  
  
## <a name="see-also"></a> Voir aussi  
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [sys.server_event_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)  
  
  
