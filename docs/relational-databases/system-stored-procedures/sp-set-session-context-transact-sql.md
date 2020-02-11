---
title: sp_set_session_context (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/14/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_set_session_context
- sp_set_session_context_TSQL
- sys.sp_set_session_context
- sys.sp_set_session_context_TSQL
helpviewer_keywords:
- sp_set_session_context
ms.assetid: 7a3a3b2a-1408-4767-a376-c690e3c1fc5b
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a57bf4acff6f8d0d08f86852de5ecc0411211c67
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68104394"
---
# <a name="sp_set_session_context-transact-sql"></a>sp_set_session_context (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

Définit une paire clé-valeur dans le contexte de session.  
  

 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_set_session_context [ @key= ] N'key', [ @value= ] 'value'  
    [ , [ @read_only = ] { 0 | 1 } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @key= ] N'key'  
 Clé qui est définie, de type **sysname**. La taille de clé maximale est de 128 octets.  
  
 [ @value= ] ajoutée  
 Valeur de la clé spécifiée, de type **sql_variant**. La définition d’une valeur NULL libère la mémoire. La taille maximale est de 8 000 octets.  
  
 [ @read_only= ] {0 | 1}  
 Indicateur de type **bit**. Si la valeur est 1, la valeur de la clé spécifiée ne peut pas être modifiée à nouveau sur cette connexion logique. Si la valeur est 0 (valeur par défaut), la valeur peut être modifiée.  
  
## <a name="permissions"></a>Autorisations  
 N’importe quel utilisateur peut définir un contexte de session pour sa session.  
  
## <a name="remarks"></a>Notes  
 À l’instar des autres procédures stockées, seuls les littéraux et les variables (et non les expressions ou les appels de fonction) peuvent être passés en tant que paramètres.  
  
 La taille totale du contexte de session est limitée à 1 Mo. Si vous définissez une valeur qui entraîne le dépassement de cette limite, l’instruction échoue. Vous pouvez surveiller l’utilisation globale de la mémoire dans [sys. dm_os_memory_objects &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md).  
  
 Vous pouvez surveiller l’utilisation globale de la mémoire en interrogeant [sys. dm_os_memory_cache_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md) comme suit :`SELECT * FROM sys.dm_os_memory_cache_counters WHERE type = 'CACHESTORE_SESSION_CONTEXT';`  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre comment définir, puis retourner une clé de contexte de session nommée Language avec la valeur English.  
  
```  
EXEC sys.sp_set_session_context @key = N'language', @value = 'English';  
SELECT SESSION_CONTEXT(N'language');  
```  
  
 L’exemple suivant illustre l’utilisation de l’indicateur facultatif en lecture seule.  
  
```  
EXEC sys.sp_set_session_context @key = N'user_id', @value = 4, @read_only = 1;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CURRENT_TRANSACTION_ID &#40;Transact-SQL&#41;](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [SESSION_CONTEXT &#40;Transact-SQL&#41;](../../t-sql/functions/session-context-transact-sql.md)   
 [Sécurité au niveau des lignes](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO  &#40;Transact-SQL&#41;](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO &#40;Transact-SQL&#41;](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  
