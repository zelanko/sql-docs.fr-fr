---
title: ALTER SCHEMA (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/01/2017
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
- ALTER SCHEMA
- ALTER_SCHEMA_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], transferring
- transferring objects between schemas
- ALTER SCHEMA statement
- schemas [SQL Server], modifying
- modifying schemas
ms.assetid: 0a760138-460e-410a-a3c1-d60af03bf2ed
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ad157c7d4d7b92bc199c4a490d4387acc0af0908
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-schema-transact-sql"></a>ALTER SCHEMA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Transfère un élément sécurisable d'un schéma à un autre.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ALTER SCHEMA schema_name   
   TRANSFER [ <entity_type> :: ] securable_name   
[;]  
  
<entity_type> ::=  
    {  
    Object | Type | XML Schema Collection  
    }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER SCHEMA schema_name   
   TRANSFER [ OBJECT :: ] securable_name   
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *schema_name*  
 Est le nom d’un schéma de base de données active, où l’élément sécurisable doit être transféré. Ne peut pas être SYS ou INFORMATION_SCHEMA.  
  
 \<entity_type >  
 Classe de l'entité pour laquelle il y a un changement de propriétaire. Object est la valeur par défaut.  
  
 *securable_name*  
 Nom composé d'une ou deux parties, qui désigne l'élément sécurisable de schéma à transférer.  
  
## <a name="remarks"></a>Notes  
 Les utilisateurs et les schémas sont complètement distincts.  
  
 L'instruction ALTER SCHEMA ne peut être utilisée que pour transférer des éléments sécurisables entre des schémas de la même base de données. Pour modifier ou supprimer un élément sécurisable au sein du même schéma, utilisez l'instruction ALTER ou DROP propre à cet élément sécurisable.  
  
 Si un nom en une partie est utilisé pour *securable_name*, les règles de résolution de noms actuellement en vigueur seront utilisés pour localiser l’élément sécurisable.  
  
 Toutes les autorisations associées à cet élément sécurisable sont supprimées après le transfert de l'élément sécurisable vers le nouveau schéma. Si le propriétaire de l'élément sécurisable a été défini explicitement, il reste inchangé. Si la valeur SCHEMA OWNER a été attribuée au propriétaire de l'élément sécurisable, celui-ci reste SCHEMA OWNER ; une fois le transfert effectué, la valeur de SCHEMA OWNER est le propriétaire du nouveau schéma. L'identification principal_id du nouveau propriétaire sera NULL.  
  
 Pour modifier le schéma d’une table ou vue à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, cliquez sur la table ou vue, puis sur **conception**. Appuyez sur **F4** pour ouvrir la fenêtre Propriétés. Dans le **schéma** , sélectionnez un nouveau schéma.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 Pour transférer un élément sécurisable provenant d'un autre schéma, l'utilisateur actuel doit bénéficier de l'autorisation CONTROL sur l'élément sécurisable (et non sur le schéma) et de l'autorisation ALTER sur le schéma cible.  
  
 Si l'élément sécurisable en question est soumis à une spécification EXECUTE AS OWNER et que le propriétaire est défini à SCHEMA OWNER, l'utilisateur doit également bénéficier de l'autorisation IMPERSONATION sur le propriétaire du schéma cible.  
  
 Toutes les autorisations associées à l'élément sécurisable soumis à un transfert sont supprimées lors du déplacement de cet élément.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-transferring-ownership-of-a-table"></a>A. Transfert de la propriété d'une table  
 L'exemple suivant modifie le schéma `HumanResources` en y transférant la table `Address` du schéma `Person`.  
  
```  
USE AdventureWorks2012;  
GO  
ALTER SCHEMA HumanResources TRANSFER Person.Address;  
GO  
```  
  
### <a name="b-transferring-ownership-of-a-type"></a>B. Transfert de propriété d'un type  
 L'exemple suivant crée un type dans le schéma `Production`, puis transfère le type vers le schéma `Person`.  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TYPE Production.TestType FROM [varchar](10) NOT NULL ;  
GO  
  
-- Check the type owner.  
SELECT sys.types.name, sys.types.schema_id, sys.schemas.name  
    FROM sys.types JOIN sys.schemas   
        ON sys.types.schema_id = sys.schemas.schema_id   
    WHERE sys.types.name = 'TestType' ;  
GO  
  
-- Change the type to the Person schema.  
ALTER SCHEMA Person TRANSFER type::Production.TestType ;  
GO  
  
-- Check the type owner.  
SELECT sys.types.name, sys.types.schema_id, sys.schemas.name  
    FROM sys.types JOIN sys.schemas   
        ON sys.types.schema_id = sys.schemas.schema_id   
    WHERE sys.types.name = 'TestType' ;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-transferring-ownership-of-a-table"></a>C. Transfert de la propriété d'une table  
 L’exemple suivant crée une table `Region` dans les `dbo` crée de schéma, un `Sales` schéma, puis déplace le `Region` de table à partir de la `dbo` schéma à la `Sales` schéma.  
  
```  
CREATE TABLE dbo.Region   
    (Region_id int NOT NULL,  
    Region_Name char(5) NOT NULL)  
WITH (DISTRIBUTION = REPLICATE);  
GO  
  
CREATE SCHEMA Sales;  
GO  
  
ALTER SCHEMA Sales TRANSFER OBJECT::dbo.Region;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER des schémas &#40; Transact-SQL &#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [SUPPRIMER les schémas &#40; Transact-SQL &#41;](../../t-sql/statements/drop-schema-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  


