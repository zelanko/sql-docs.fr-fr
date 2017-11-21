---
title: SET ANSI_NULL_DFLT_OFF (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ANSI_NULL_DFLT_OFF_TSQL
- ANSI_NULL_DFLT_OFF
- SET ANSI_NULL_DFLT_OFF
- SET_ANSI_NULL_DFLT_OFF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- default nullability
- ANSI_NULL_DFLT_OFF option
- null values [SQL Server], overriding
- overriding default nullability
- SET ANSI_NULL_DFLT_OFF statement
ms.assetid: 8ed5c512-f5de-4741-a18a-de85a3041295
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1eeb95a4fdeb8e0db5ed08f3f5728a38f512bc2f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansinulldfltoff-transact-sql"></a>SET ANSI_NULL_DFLT_OFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Modifie le comportement de la session pour remplacer la possibilité de valeur NULL par défaut des nouvelles colonnes lorsque l’option ANSI null default de la base de données est **true**. Pour plus d’informations sur la définition de la valeur de la valeur par défaut ANSI null, consultez [ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET ANSI_NULL_DFLT_OFF { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_NULL_DFLT_OFF OFF  
```  
  
## <a name="remarks"></a>Notes  
 Ce paramètre affecte l'acceptation des valeurs NULL dans une nouvelle colonne, uniquement si celle-ci n'est pas spécifiée dans les instructions CREATE TABLE et ALTER TABLE. Si l'option SET ANSI_NULL_DFLT_OFF est activée (ON), les nouvelles colonnes créées à l'aide de l'instruction ALTER TABLE ou CREATE TABLE sont de type NOT NULL par défaut, si l'acceptation des valeurs NULL n'est pas explicitement spécifiée pour ces dernières. SET ANSI_NULL_DFLT_OFF ne pas les colonnes qui sont créés à l’aide d’une valeur NULL explicite ou non NULL.  
  
 SET ANSI_NULL_DFLT_OFF et SET ANSI_NULL_DFLT_ON ne peuvent pas être activées (valeur ON) simultanément. Si l'une des options a la valeur ON, l'autre a automatiquement la valeur OFF. Par conséquent, SET ANSI_NULL_DFLT_OFF ou SET ANSI_NULL_DFLT_ON peut avoir la valeur ON, ou les deux options peuvent avoir la valeur OFF. Si l'une des deux options a la valeur ON, ce paramètre (SET ANSI_NULL_DFLT_OFF ou SET ANSI_NULL_DFLT_ON) prend effet. Si les deux options sont OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise la valeur de la colonne is_ansi_null_default_on dans le [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vue de catalogue.  
  
 Pour une opération plus fiable de [!INCLUDE[tsql](../../includes/tsql-md.md)] des scripts qui sont utilisés dans les bases de données avec les paramètres des valeurs NULL différentes, il est préférable de toujours spécifier NULL ou NOT NULL dans les instructions CREATE TABLE et ALTER TABLE.  
  
 La valeur de SET ANSI_NULL_DFLT_OFF est définie lors de l'exécution et non durant l'analyse.  
  
 Pour afficher la valeur actuelle de ce paramètre, exécutez la requête suivante.  
  
```  
DECLARE @ANSI_NULL_DFLT_OFF VARCHAR(3) = 'OFF';  
IF ( (2048 & @@OPTIONS) = 2048 ) SET @ANSI_NULL_DFLT_OFF = 'ON';  
SELECT @ANSI_NULL_DFLT_OFF AS ANSI_NULL_DFLT_OFF;  
  
```  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle public.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre les effets de `SET ANSI_NULL_DFLT_OFF` lorsque la valeur de l'option de base de données ANSI null default est ON et OFF, respectivement.  
  
```  
USE AdventureWorks2012;  
GO  
  
-- Set the 'ANSI null default' database option to true by executing   
-- ALTER DATABASE.  
GO  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT ON;  
GO  
-- Create table t1.  
CREATE TABLE t1 (a TINYINT);  
GO  
-- NULL INSERT should succeed.  
INSERT INTO t1 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to ON and create table t2.  
SET ANSI_NULL_DFLT_OFF ON;  
GO  
CREATE TABLE t2 (a TINYINT);  
GO   
-- NULL INSERT should fail.  
INSERT INTO t2 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to OFF and create table t3.  
SET ANSI_NULL_DFLT_OFF OFF;  
GO  
CREATE TABLE t3 (a TINYINT) ;  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t3 (a) VALUES (NULL);  
GO  
  
-- This illustrates the effect of having both the database  
-- option and SET option disabled.  
-- Set the 'ANSI null default' database option to false.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT OFF;  
GO  
-- Create table t4.  
CREATE TABLE t4 (a tinyint) ;  
GO   
-- NULL INSERT should fail.  
INSERT INTO t4 (a) VALUES (null);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to ON and create table t5.  
SET ANSI_NULL_DFLT_OFF ON;  
GO  
CREATE TABLE t5 (a tinyint);  
GO   
-- NULL insert should fail.  
INSERT INTO t5 (a) VALUES (null);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to OFF and create table t6.  
SET ANSI_NULL_DFLT_OFF OFF;  
GO  
CREATE TABLE t6 (a tinyint);   
GO   
-- NULL insert should fail.  
INSERT INTO t6 (a) VALUES (null);  
GO  
  
-- Drop tables t1 through t6.  
DROP TABLE t1, t2, t3, t4, t5, t6;  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_NULL_DFLT_ON &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)  
  
  

