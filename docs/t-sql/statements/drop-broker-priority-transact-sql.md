---
title: "SUPPRIMER la priorité de service BROKER (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_BROKER_PRIORITY_TSQL
- DROP BROKER PRIORITY
dev_langs:
- TSQL
helpviewer_keywords:
- DROP BROKER PRIORITY statement
ms.assetid: 09ee6c5b-af94-4a4b-a0e2-f9eac50e43aa
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 254914f3b92289faf19a37b4651e7c95804ac791
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="drop-broker-priority-transact-sql"></a>DROP BROKER PRIORITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime une priorité de conversation de la base de données active.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP BROKER PRIORITY ConversationPriorityName  
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *ConversationPriorityName*  
 Spécifie le nom de la priorité de conversation à supprimer.  
  
## <a name="remarks"></a>Notes  
 Lorsque vous supprimez une priorité de conversation, toutes les conversations existantes continuent de fonctionner avec les niveaux de priorité qui leur ont été attribués par la priorité de conversation.  
  
## <a name="permissions"></a>Permissions  
 L'autorisation de création d'une priorité de conversation est accordée par défaut aux membres du rôle de base de données fixe db_ddladmin ou db_owner, ainsi qu'aux membres du rôle serveur fixe sysadmin. Nécessite l'autorisation ALTER sur la base de données.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime la priorité de conversation nommée `InitiatorAToTargetPriority`.  
  
```  
DROP BROKER PRIORITY InitiatorAToTargetPriority;  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER BROKER PRIORITY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [CRÉER une priorité de service BROKER &#40; Transact-SQL &#41;](../../t-sql/statements/create-broker-priority-transact-sql.md)   
 [Sys.conversation_priorities &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-conversation-priorities-transact-sql.md)  
  
  

