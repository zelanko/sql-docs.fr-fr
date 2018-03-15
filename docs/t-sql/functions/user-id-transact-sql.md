---
title: USER_ID (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
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
- USER_ID
- USER_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- USER_ID function
- identification numbers [SQL Server]
- IDs [SQL Server], databases
- users [SQL Server], database ID numbers
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
ms.assetid: 67fd29bc-eda9-4d4d-b148-5d3659181a43
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c8c8e07d6d58b6615ff5e4528556bf08e0b72c13
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="userid-transact-sql"></a>USER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne le numéro d'identification d'un utilisateur de la base de données.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez [DATABASE_PRINCIPAL_ID](../../t-sql/functions/database-principal-id-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
USER_ID ( [ 'user' ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *user*  
 Nom d'utilisateur à utiliser. *user* est de type **nchar**. Si une valeur **char** est spécifiée, elle est implicitement convertie en **nchar**. Les parenthèses sont obligatoires.  
  
## <a name="return-types"></a>Types de retour  
 **Int**  
  
## <a name="remarks"></a>Notes   
 Si *user* est omis, l’utilisateur actuel est pris en compte. Si le paramètre contient le mot NULL, retourne NULL. Lorsque USER_ID est appelé après EXECUTE AS, USER_ID retourne l'ID du contexte représenté.  
  
 Lorsqu'un principal Windows qui n'est pas mappé à un utilisateur spécifique accède à une base de données parce qu'il appartient à un groupe, USER_ID retourne 0 (l'identificateur de public). Si un tel principal crée un objet sans spécifier de schéma, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créera un utilisateur implicite et un schéma mappés au principal Windows. L'utilisateur ainsi créé ne peut pas être utilisé pour une connexion à la base de données. Les appels à USER_ID effectués par un principal Windows mappé à un utilisateur implicite retourneront l'identificateur de cet utilisateur implicite.  
  
 USER_ID peut être utilisé dans une liste de sélection, dans une clause WHERE, et partout où une expression est autorisée. Pour plus d’informations, consultez [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, la valeur retournée est le numéro d'identification de l'utilisateur `AdventureWorks2012` de `Harold`.  
  
```  
USE AdventureWorks2012;  
SELECT USER_ID('Harold');  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [USER_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/user-name-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [DATABASE_PRINCIPAL_ID &#40;Transact-SQL&#41;](../../t-sql/functions/database-principal-id-transact-sql.md)   
 [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
