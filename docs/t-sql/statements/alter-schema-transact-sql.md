---
title: ALTER SCHEMA (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 01/09/2018
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
- ALTER SCHEMA
- ALTER_SCHEMA_TSQL
dev_langs: TSQL
helpviewer_keywords:
- objects [SQL Server], transferring
- transferring objects between schemas
- ALTER SCHEMA statement
- schemas [SQL Server], modifying
- modifying schemas
ms.assetid: 0a760138-460e-410a-a3c1-d60af03bf2ed
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 30ef553ccfba1f30be9b75f8d0290115be395925
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
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
  
 \<entity_type>  
 Classe de l'entité pour laquelle il y a un changement de propriétaire. Object est la valeur par défaut.  
  
 *securable_name*  
 Est le nom d’une ou deux parties d’une portée de schéma sécurisable dans le schéma.  
  
## <a name="remarks"></a>Notes  
 Les utilisateurs et les schémas sont complètement distincts.  
  
 L'instruction ALTER SCHEMA ne peut être utilisée que pour transférer des éléments sécurisables entre des schémas de la même base de données. Pour modifier ou supprimer un élément sécurisable au sein du même schéma, utilisez l'instruction ALTER ou DROP propre à cet élément sécurisable.  
  
 Si un nom en une partie est utilisé pour *securable_name*, les règles de résolution de noms actuellement en vigueur seront utilisés pour localiser l’élément sécurisable.  
  
 Toutes les autorisations associées à cet élément sécurisable sont supprimées après le transfert de l'élément sécurisable vers le nouveau schéma. Si le propriétaire de l'élément sécurisable a été défini explicitement, il reste inchangé. Si la valeur SCHEMA OWNER a été attribuée au propriétaire de l'élément sécurisable, celui-ci reste SCHEMA OWNER ; une fois le transfert effectué, la valeur de SCHEMA OWNER est le propriétaire du nouveau schéma. L'identification principal_id du nouveau propriétaire sera NULL.  
  
 Déplacement d’une procédure stockée, fonction, vue ou au déclencheur ne modifie pas le nom de schéma, si présent, correspondantes de l’objet dans la colonne de définition de la [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) affichage catalogue ou obtenus à l’aide du [ OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md) fonction intégrée. Par conséquent, nous vous recommandons de ne pas être utilisé ALTER SCHEMA pour déplacer ces types d’objets. Au lieu de cela, supprimer et recréer l’objet dans son nouveau schéma.  
  
 Déplacement d’un objet tel qu’une table ou d’un synonyme ne met pas automatiquement à jour les références à cet objet. Vous devez modifier les objets qui font référence à l’objet transféré manuellement. Par exemple, si vous déplacez une table et que la table est référencée dans un déclencheur, vous devez modifier le déclencheur pour refléter le nouveau nom de schéma. Utilisez [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) pour répertorier les dépendances sur l’objet avant de le déplacer.  

 Pour modifier le schéma d’une table à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, cliquez sur la table, puis sur **conception**. Appuyez sur **F4** pour ouvrir la fenêtre Propriétés. Dans le **schéma** , sélectionnez un nouveau schéma.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Autorisations  
 Pour transférer un élément sécurisable provenant d'un autre schéma, l'utilisateur actuel doit bénéficier de l'autorisation CONTROL sur l'élément sécurisable (et non sur le schéma) et de l'autorisation ALTER sur le schéma cible.  
  
 Si l’élément sécurisable a une spécification EXECUTE AS OWNER sur celui-ci et le propriétaire est défini sur le propriétaire du schéma, l’utilisateur doit disposer également de l’autorisation IMPERSONATE sur le propriétaire du schéma cible.  
  
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
 [CREATE SCHEMA &#40;Transact-SQL&#41;](../../t-sql/statements/create-schema-transact-sql.md)   
 [DROP SCHEMA &#40;Transact-SQL&#41;](../../t-sql/statements/drop-schema-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

