---
title: BEGIN... FIN (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BEGIN
- BEGIN_TSQL
dev_langs: TSQL
helpviewer_keywords:
- enclosing statements [SQL Server]
- BEGIN statement
- control-of-flow language [SQL Server], BEGIN...END statement
- BEGIN...END keyword
- grouping statements, BEGIN...END statement
- executing Transact-SQL statements together [SQL Server]
- statements [SQL Server], grouping
ms.assetid: fc2c7f76-f1f9-4f91-beef-bc8ef0da2feb
caps.latest.revision: "30"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: b00ceec423103a1f53a1b6434aaf6da0598fba20
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="beginend-transact-sql"></a>BEGIN...END (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Délimite une série d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] pour permettre l'exécution groupée d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)]. BEGIN et END sont des mots clés du langage de contrôle de flux.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BEGIN  
    { sql_statement | statement_block }   
END  
```  
  
## <a name="arguments"></a>Arguments  
 { *sql_statement* | *statement_block* }  
 Représente toute instruction ou tout groupe d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] valide tel que défini dans un bloc d'instructions.  
  
## <a name="remarks"></a>Notes  
 Les blocs BEGIN...END peuvent être imbriqués.  
  
 Bien que tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions sont valides dans un BEGIN... FIN bloquer certains [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions ne doivent pas être regroupées dans le même lot, ou le bloc d’instructions.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, `BEGIN` et `END` délimitent une série d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui sont exécutées ensemble. Si le bloc `BEGIN...END` ne figurait pas dans l'exemple, les deux instructions `ROLLBACK TRANSACTION` seraient exécutées et les deux messages `PRINT` seraient renvoyés.  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
GO  
IF @@TRANCOUNT = 0  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM Person.Person WHERE LastName = 'Adams';  
    ROLLBACK TRANSACTION;  
    PRINT N'Rolling back the transaction two times would cause an error.';  
END;  
ROLLBACK TRANSACTION;  
PRINT N'Rolled back the transaction.';  
GO  
/*  
Rolled back the transaction.  
*/  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Dans l’exemple suivant, `BEGIN` et `END` définir une série de [!INCLUDE[DWsql](../../includes/dwsql-md.md)] les instructions qui s’exécutent ensemble. Si le `BEGIN...END` bloc ne sont pas inclus, l’exemple suivant sera dans une boucle continue.  
  
```  
-- Uses AdventureWorks  
  
DECLARE @Iteration Integer = 0  
WHILE @Iteration <10  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM dbo.DimCustomer WHERE LastName = 'Adams';  
SET @Iteration += 1  
END;  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [Langage de contrôle de flux &#40; Transact-SQL &#41;](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [FIN &#40; BEGIN... FIN &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/end-begin-end-transact-sql.md)  
  
  


