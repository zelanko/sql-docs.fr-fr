---
title: Object_id (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECT_ID
- OBJECT_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], IDs
- identification numbers [SQL Server], database objects
- checking object exists
- IDs [SQL Server], database objects
- OBJECT_ID function
- database objects [SQL Server], IDs
- displaying object IDs
- viewing object IDs
- verifying object exists
ms.assetid: f89286db-440f-4218-a828-30881ce3077a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4978a07401fa33e0244a61181e29cfd6146b695e
ms.sourcegitcommit: 60d0c9415630094a49d4ca9e4e18c3faa694f034
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="objectid-transact-sql"></a>OBJECT_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie le numéro d'identification d'un objet de la base de données pour un objet défini avec l'étendue d'un schéma.  
  
> [!IMPORTANT]  
>  Il n'est pas possible d'exécuter des requêtes sur des objets qui ne sont pas définis avec l'étendue d'un schéma, tels que des déclencheurs DDL, en utilisant OBJECT_ID. Pour les objets qui ne figurent pas dans le [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) affichage catalogue, obtenir les numéros d’identification en interrogeant l’affichage catalogue approprié. Par exemple, pour retourner le numéro d’identification d’un déclencheur DDL, utilisez `SELECT OBJECT_ID FROM sys.triggers WHERE name = 'DatabaseTriggerLog``'`.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
OBJECT_ID ( '[ database_name . [ schema_name ] . | schema_name . ]   
  object_name' [ ,'object_type' ] )  
```  
  
## <a name="arguments"></a>Arguments  
 **'** *nom_objet* **'**  
 Est l’objet à utiliser. *nom_objet* est **varchar** ou **nvarchar**. Si *nom_objet* est **varchar**, il est converti implicitement en **nvarchar**. La spécification des noms de la base de données et du schéma est facultative.  
  
 **'** *object_type* **'**  
 Type de l'objet défini avec l'étendue du schéma. *object_type* est **varchar** ou **nvarchar**. Si *object_type* est **varchar**, il est converti implicitement en **nvarchar**. Pour obtenir la liste des types d’objets, consultez la **type** colonne [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
## <a name="return-types"></a>Types de retour  
 **Int**  
  
## <a name="exceptions"></a>Exceptions  
 Pour un index spatial, OBJECT_ID retourne la valeur NULL.  
  
 Retourne NULL en cas d'erreur.  
  
 Un utilisateur peut voir uniquement les métadonnées des éléments sécurisables qui lui appartiennent ou pour lesquels il dispose d'une autorisation. Cela signifie que les fonctions intégrées générant des métadonnées, telles que OBJECT_ID, peuvent retourner la valeur NULL si l'utilisateur ne dispose d'aucune autorisation sur l'objet. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Notes   
 Quand le paramètre d'une fonction système est facultatif, la base de données active, l'ordinateur hôte, l'utilisateur du serveur ou l'utilisateur de la base de données sont pris implicitement en considération. Les fonctions intégrées doivent toujours être suivies de parenthèses.  
  
 Lorsqu’un nom de table temporaire est spécifié, le nom de la base de données doit être placée avant le nom de la table temporaire, sauf si la base de données actuelle est **tempdb**. Par exemple : `SELECT OBJECT_ID('tempdb..#mytemptable')`.  
  
 Les fonctions système peuvent être utilisées dans la liste de sélection, dans une clause WHERE, et partout où une expression est autorisée. Pour plus d’informations, consultez [Expressions &#40; Transact-SQL &#41; ](../../t-sql/language-elements/expressions-transact-sql.md) et [où &#40; Transact-SQL &#41; ](../../t-sql/queries/where-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-the-object-id-for-a-specified-object"></a>A. Renvoi de l'identificateur d'un objet spécifié  
 L'exemple suivant renvoie l'ID d'objet de la table `Production.WorkOrder` de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE master;  
GO  
SELECT OBJECT_ID(N'AdventureWorks2012.Production.WorkOrder') AS 'Object ID';  
GO  
```  
  
### <a name="b-verifying-that-an-object-exists"></a>B. Vérification de l'existence d'un objet  
 L'exemple suivant vérifie l'existence d'une table spécifiée en vérifiant que la table a un identificateur d'objet. Si la table existe, elle est supprimée. Si elle n'existe pas, l'instruction `DROP TABLE` n'est pas exécutée.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'dbo.AWBuildVersion', N'U') IS NOT NULL  
DROP TABLE dbo.AWBuildVersion;  
GO  
```  
  
### <a name="c-using-objectid-to-specify-the-value-of-a-system-function-parameter"></a>C. Utilisation de OBJECT_ID pour spécifier la valeur d'un paramètre d'une fonction système  
 L’exemple suivant retourne des informations pour tous les index et partitions de la `Person.Address` de table dans le [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données à l’aide de la [sys.dm_db_index_operational_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md) (fonction).  
  
> [!IMPORTANT]  
>  Lorsque vous utilisez les fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)] DB_ID et OBJECT_ID pour obtenir la valeur d'un paramètre, assurez-vous toujours que l'ID retourné est valide. Si le nom de la base de données ou de l'objet est introuvable, par exemple s'il n'existe pas ou n'est pas correctement orthographié, les deux fonctions retournent la valeur NULL. Le **sys.dm_db_index_operational_stats** fonction interprète NULL comme une valeur générique qui spécifie toutes les bases de données ou de tous les objets. Comme il peut s'agir d'une opération non intentionnelle, les exemples fournis dans cette section présentent une méthode sûre pour déterminer les ID de base de données et d'objet.  
  
```  
DECLARE @db_id int;  
DECLARE @object_id int;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');  
IF @db_id IS NULL   
  BEGIN;  
    PRINT N'Invalid database';  
  END;  
ELSE IF @object_id IS NULL  
  BEGIN;  
    PRINT N'Invalid object';  
  END;  
ELSE  
  BEGIN;  
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);  
  END;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-returning-the-object-id-for-a-specified-object"></a>D : retour de l’ID d’objet pour un objet spécifié  
 L'exemple suivant renvoie l'ID d'objet de la table `FactFinance` de la base de données [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].  
  
```  
SELECT OBJECT_ID('AdventureWorksPDW2012.dbo.FactFinance') AS 'Object ID';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de métadonnées &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [Sys.Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Sys.dm_db_index_operational_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [Nom_objet &#40; Transact-SQL &#41;](../../t-sql/functions/object-name-transact-sql.md)  
  
  

