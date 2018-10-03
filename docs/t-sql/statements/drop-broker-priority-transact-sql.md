---
title: DROP BROKER PRIORITY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_BROKER_PRIORITY_TSQL
- DROP BROKER PRIORITY
dev_langs:
- TSQL
helpviewer_keywords:
- DROP BROKER PRIORITY statement
ms.assetid: 09ee6c5b-af94-4a4b-a0e2-f9eac50e43aa
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c922d50bdac99ad39fe9057a2c5091a2a389a849
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684277"
---
# <a name="drop-broker-priority-transact-sql"></a>DROP BROKER PRIORITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
## <a name="see-also"></a> Voir aussi  
 [ALTER BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [CREATE BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/create-broker-priority-transact-sql.md)   
 [sys.conversation_priorities &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-conversation-priorities-transact-sql.md)  
  
  
