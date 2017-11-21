---
title: SESSION_CONTEXT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/22/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SESSION_CONTEXT
- sys.SESSION_CONTEXT
- SESSION_CONTEXT_TSQL
- sys.SESSION_CONTEXT_TSQL
helpviewer_keywords:
- SESSION_CONTEXT function
ms.assetid: b6bdbc54-331a-43cc-ab3d-3872d6a12100
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 23eea4b51009272ae06987ee2e9c1730750b3d6d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="sessioncontext-transact-sql"></a>SESSION_CONTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Retourne la valeur de la clé spécifiée dans le contexte de la session active. La valeur est définie à l’aide de la [sp_set_session_context &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md) procédure.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SESSION_CONTEXT(N'key')  
```  
  
## <a name="arguments"></a>Arguments  
 'key'  
 La clé (type sysname) de la valeur en cours de récupération.  
  
## <a name="return-type"></a>Type de retour  
 **sql_variant**  
  
## <a name="return-value"></a>Valeur retournée  
 La valeur associée à la clé spécifiée dans le contexte de session, ou NULL si aucune valeur n’a été définie pour cette clé.  
  
## <a name="permissions"></a>Permissions  
 N’importe quel utilisateur peut lire le contexte de session pour leur session.  
  
## <a name="remarks"></a>Notes  
 Comportement de MARS du SESSION_CONTEXT est similaire à celle de CONTEXT_INFO. Si un lot MARS définit une paire clé-valeur, la nouvelle valeur n’est retournée dans un autre lot MARS sur la même connexion, sauf si elles démarrées après traitement ayant défini la nouvelle valeur. Si plusieurs lots MARS sont actives sur une connexion, les valeurs ne peut pas être définies en tant que « read_only. » Cela empêche les conditions de concurrence et non-déterminisme sur la valeur « wins ».  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant définit la valeur de contexte de session pour la clé `user_id` à 4, puis utilise le **SESSION_CONTEXT** fonction pour récupérer la valeur.  
  
```  
EXEC sp_set_session_context 'user_id', 4;  
SELECT SESSION_CONTEXT(N'user_id');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_set_session_context &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md)   
 [CURRENT_TRANSACTION_ID &#40; Transact-SQL &#41;](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [Sécurité au niveau des lignes](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO &#40; Transact-SQL &#41;](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  

