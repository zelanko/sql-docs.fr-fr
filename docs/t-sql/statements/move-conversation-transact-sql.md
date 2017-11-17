---
title: MOVE CONVERSATION (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MOVE_CONVERSATION_TSQL
- MOVE CONVERSATION
- MOVE_TSQL
- MOVE
dev_langs:
- TSQL
helpviewer_keywords:
- moving conversations
- MOVE CONVERSATION statement
- relocating conversations
- conversations [Service Broker], groups
- conversations [Service Broker], moving
ms.assetid: 1da4d2c9-e767-434e-b49b-615711a7f626
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 31141afc0008b0c234a32c6c58d2d8d7b37ddadd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="move-conversation-transact-sql"></a>MOVE CONVERSATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Déplace une conversation vers un groupe de conversations différent.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
MOVE CONVERSATION conversation_handle  
   TO conversation_group_id  
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *conversation_handle*  
 Variable ou constante contenant le descripteur de conversation à déplacer. *conversation_handle* doit être de type **uniqueidentifier**.  
  
 POUR *conversation_group_id*  
 Variable ou constante contenant l'identificateur du groupe de conversations destinataire. *conversation_group_id* doit être de type **uniqueidentifier**.  
  
## <a name="remarks"></a>Notes  
 L’instruction MOVE CONVERSATION déplace la conversation spécifiée par *conversation_handle* au groupe de conversations identifié par *conversation_group_id*. Les dialogues ne peuvent être redirigés qu'entre des groupes de conversation associés à la même file d'attente.  
  
> [!IMPORTANT]  
>  Si l’instruction MOVE CONVERSATION n’est pas la première instruction dans un lot ou une procédure stockée, l’instruction précédente doit se terminer par un point-virgule (**;**), le [!INCLUDE[tsql](../../includes/tsql-md.md)] terminateur d’instruction.  
  
 L’instruction MOVE CONVERSATION verrouille le groupe de conversation associé *conversation_handle* et le groupe de conversations spécifié par *conversation_group_id* jusqu'à ce que la transaction contenant l’instruction est validée ou restaurée.  
  
 MOVE CONVERSATION n'est pas valide dans une fonction définie par l'utilisateur.  
  
## <a name="permissions"></a>Permissions  
 Pour déplacer une conversation, l'utilisateur actif doit être soit propriétaire de la conversation et du groupe de conversations, soit un membre du rôle serveur fixe sysadmin, soit un membre du rôle de base de données fixe db_owner.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant déplace une conversation vers un groupe de conversations différent.  
  
```  
DECLARE @conversation_handle UNIQUEIDENTIFIER,  
        @conversation_group_id UNIQUEIDENTIFIER ;  
  
SET @conversation_handle =  
    <retrieve conversation handle from database> ;  
SET @conversation_group_id =  
    <retrieve conversation group ID from database> ;  
  
MOVE CONVERSATION @conversation_handle TO @conversation_group_id ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [BEGIN DIALOG CONVERSATION &#40; Transact-SQL &#41;](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [GET CONVERSATION GROUP &#40; Transact-SQL &#41;](../../t-sql/statements/get-conversation-group-transact-sql.md)   
 [CONVERSATION de fin &#40; Transact-SQL &#41;](../../t-sql/statements/end-conversation-transact-sql.md)   
 [Sys.conversation_groups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-conversation-groups-transact-sql.md)   
 [Sys.conversation_endpoints &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)  
  
  

