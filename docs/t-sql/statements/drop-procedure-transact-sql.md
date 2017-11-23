---
title: DROP PROCEDURE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP PROCEDURE
- DROP_PROCEDURE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- removing stored procedures
- dropping procedure groups
- deleting stored procedures
- deleting procedure groups
- DROP PROCEDURE statement
- dropping stored procedures
- stored procedures [SQL Server], removing
- removing procedure groups
ms.assetid: 1c2d7235-7b9b-4336-8f17-429e7d82c2c3
caps.latest.revision: "51"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a154c40a9ede59d808d0ad77af685d27b23db208
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="drop-procedure-transact-sql"></a>DROP PROCEDURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Supprime une ou plusieurs procédures stockées ou un ou plusieurs groupes de procédures de la base de données active dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP { PROC | PROCEDURE } [ IF EXISTS ] { [ schema_name. ] procedure } [ ,...n ]  
```  
  
```tsql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP { PROC | PROCEDURE } { [ schema_name. ] procedure_name }  
```  
  
## <a name="arguments"></a>Arguments  
 *S’IL EXISTE*  
 **S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Conditionnellement supprime la procédure uniquement s’il existe déjà.  
  
 *schema_name*  
 Le nom du schéma auquel appartient la procédure. Vous ne pouvez pas spécifier de nom de serveur ou de base de données.  
  
 *procédure*  
 Nom de la procédure stockée ou du groupe de procédures stockées à supprimer. Vous ne pouvez pas supprimer des procédures individuelles dans un groupe de procédures numérotées ; dans ce cas, tout le groupe de procédures est supprimé.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Avant de supprimer une procédure stockée, vérifiez les objets dépendants et modifiez-les en conséquence. La suppression d'une procédure stockée peut entraîner l'échec des scripts et des objets dépendants quand ceux-ci n'ont pas été mis à jour. Pour plus d’informations, consultez [afficher les dépendances d’une procédure stockée](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md)  
  
## <a name="metadata"></a>Métadonnées  
 Pour afficher une liste des procédures existantes, interrogez la **sys.objects** affichage catalogue. Pour afficher la définition de procédure, interrogez la **sys.sql_modules** affichage catalogue.  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 Requiert **contrôle** autorisation sur la procédure, ou **ALTER** l’autorisation sur le schéma auquel appartient la procédure ou l’appartenance à la **db_ddladmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime la procédure stockée `dbo.uspMyProc` de la base de données active.  
  
```  
DROP PROCEDURE dbo.uspMyProc;  
GO  
```  
  
 L'exemple suivant supprime plusieurs procédures stockées de la base de données active.  
  
```  
DROP PROCEDURE dbo.uspGetSalesbyMonth, dbo.uspUpdateSalesQuotes, dbo.uspGetSalesByYear;  
```  
  
 L’exemple suivant supprime le `dbo.uspMyProc` procédure stockée si elle existe, mais ne provoque pas d’erreur si la procédure n’existe pas. Cette syntaxe est une nouveauté de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
```  
DROP PROCEDURE IF EXISTS dbo.uspMyProc;  
GO  
```  
  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [Sys.Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Supprimer une procédure stockée](../../relational-databases/stored-procedures/delete-a-stored-procedure.md)  
  
  


