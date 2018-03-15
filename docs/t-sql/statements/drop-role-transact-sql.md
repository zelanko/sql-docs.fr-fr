---
title: DROP ROLE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP ROLE
- DROP_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting roles
- database roles [SQL Server], removing
- removing roles
- DROP ROLE statement
- roles [SQL Server], removing
- dropping roles
ms.assetid: 1f6f13ae-56a2-4ef1-93f5-8e6151b83e1d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d3ab74cca51d7fc52edb134d29887bb30abb4499
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="drop-role-transact-sql"></a>DROP ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Supprime un rôle de la base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server  
  
DROP ROLE [ IF EXISTS ] role_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP ROLE role_name  
```  
  
## <a name="arguments"></a>Arguments  
 *IF EXISTS*  
 **S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu’à la [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Supprime, de manière conditionnelle, le rôle uniquement s’il existe déjà.  
  
 *role_name*  
 Spécifie le rôle à supprimer de la base de données.  
  
## <a name="remarks"></a>Notes   
 Les rôles qui possèdent des éléments sécurisables ne peuvent pas être supprimés de la base de données. Pour supprimer un rôle de base de données qui possède des éléments sécurisables, vous devez tout d'abord transférer la propriété de ces éléments ou supprimer ces derniers de la base de données. Les rôles qui comprennent des membres ne peuvent pas être supprimés de la base de données. Pour supprimer un rôle qui comprend des membres, vous devez au préalable supprimer les membres du rôle.  
  
 Pour supprimer des membres d’un rôle de base de données, utilisez [ALTER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-role-transact-sql.md).  
  
 Vous ne pouvez pas utiliser DROP ROLE pour supprimer un rôle de base de données fixe.  
  
 Vous pouvez consulter les informations relatives aux membres des rôles dans la vue de catalogue sys.database_role_members.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
 Pour supprimer un rôle serveur, utilisez [DROP SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-role-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation **ALTER ANY ROLE** sur la base de données, ou l’autorisation **CONTROL** sur le rôle, ou l’appartenance au rôle **db_securityadmin**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant supprime le rôle de base de données `purchasing` de la base de données `AdventureWorks2012`.  
  
```  
DROP ROLE purchasing;  
GO  
```  
  
  
## <a name="see-also"></a> Voir aussi  
 [CREATE ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [ALTER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  


