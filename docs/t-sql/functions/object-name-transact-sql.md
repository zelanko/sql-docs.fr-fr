---
title: Object_name (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- OBJECT_NAME
- OBJECT_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- OBJECT_NAME function
- viewing database object names
- objects [SQL Server], names
- database objects [SQL Server], names
- displaying database object names
- database objects [SQL Server]
- names [SQL Server], database objects
ms.assetid: 7d5b923f-0c3e-4af9-b39b-132807a6d5b3
caps.latest.revision: 45
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9960fb31a6f2805424797da5b25db2d391523b2e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="objectname-transact-sql"></a>OBJECT_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne le nom d'objet de base de données des objets de portée de schéma. Pour obtenir la liste d’objets de portée de schéma, consultez [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
OBJECT_NAME ( object_id [, database_id ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *object_id*  
 ID de l'objet à utiliser. *object_id* est **int** et est supposé pour être un objet de portée schéma dans la base de données spécifiée, ou dans le contexte actuel de la base de données.  
  
 *database_id*  
 ID de la base de données où l'objet est à rechercher. *database_id* est **int**.  
  
## <a name="return-types"></a>Types de retour  
 **sysname**  
  
## <a name="exceptions"></a>Exceptions  
 Retourne la valeur NULL en cas d'erreur ou si un appelant n'est pas autorisé à afficher l'objet. Si l'option AUTO_CLOSE de la base de données cible a pour valeur ON, la fonction ouvre la base de données.  
  
 Un utilisateur peut voir uniquement les métadonnées des éléments sécurisables qui lui appartiennent ou pour lesquels il dispose d'une autorisation. Cela signifie que les fonctions intégrées générant des métadonnées, telles que OBJECT_NAME, peuvent retourner la valeur NULL si l'utilisateur ne dispose d'aucune autorisation sur l'objet. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ANY sur l'objet. Pour spécifier un ID de base de données, l'autorisation CONNECT à la base de données est également nécessaire ou le compte Invité doit être activé.  
  
## <a name="remarks"></a>Notes  
 Les fonctions système peuvent être utilisées dans la liste de sélection, dans une clause WHERE, et partout où une expression est autorisée. Pour plus d’informations, consultez [Expressions](../../t-sql/language-elements/expressions-transact-sql.md) et [où](../../t-sql/queries/where-transact-sql.md).  
  
 La valeur retournée par cette fonction système utilise le classement de la base de données active.  
  
 Par défaut, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] suppose que *object_id* est dans le contexte de la base de données actuelle. Une requête qui fait référence à un *object_id* dans une autre base de données renvoie NULL ou des résultats incorrects. Par exemple, dans la requête suivante, le contexte de la base de données active est [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] essaie de retourner un nom d’objet pour l’ID d’objet spécifié dans cette base de données au lieu de la base de données spécifiée dans la clause FROM de la requête. Par conséquent, des informations incorrectes sont retournées.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT DISTINCT OBJECT_NAME(object_id)  
FROM master.sys.objects;  
GO  
```  
  
 Vous pouvez résoudre les noms d'objet dans le contexte d'une autre base de données en spécifiant un ID de base de données. L'exemple suivant spécifie l'ID de base de données pour la base de données `master` dans la fonction `OBJECT_SCHEMA_NAME` et retourne les résultats corrects.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id, 1) AS schema_name  
FROM master.sys.objects;  
GO  
```  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-objectname-in-a-where-clause"></a>A. Utilisation d'OBJECT_NAME dans une clause WHERE  
 L'exemple suivant retourne les colonnes de l'affichage catalogue `sys.objects` correspondant à l'objet spécifié par `OBJECT_NAME` dans la clause `WHERE` de l'instruction `SELECT`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @MyID int;  
SET @MyID = (SELECT OBJECT_ID('AdventureWorks2012.Production.Product',  
    'U'));  
SELECT name, object_id, type_desc  
FROM sys.objects  
WHERE name = OBJECT_NAME(@MyID);  
GO  
```  
  
### <a name="b-returning-the-object-schema-name-and-object-name"></a>B. Retour du nom de schéma d'objet et du nom d'objet  
 L'exemple suivant retourne le nom de schéma d'objet, le nom d'objet et le texte SQL pour tous les plans de requête mis en cache qui ne sont pas des instructions ad hoc ou préparées.  
  
```  
SELECT DB_NAME(st.dbid) AS database_name,   
    OBJECT_SCHEMA_NAME(st.objectid, st.dbid) AS schema_name,  
    OBJECT_NAME(st.objectid, st.dbid) AS object_name,   
    st.text AS query_text  
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
WHERE st.objectid IS NOT NULL;  
GO  
```  
  
### <a name="c-returning-three-part-object-names"></a>C. Retour de noms d'objet en trois parties  
 L'exemple suivant retourne le nom d'objet, de schéma et de base de données ainsi que toutes les autres colonnes dans la vue de gestion dynamique `sys.dm_db_index_operational_stats` pour tous les objets de l'ensemble des bases de données.  
  
```  
SELECT QUOTENAME(DB_NAME(database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_SCHEMA_NAME(object_id, database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_NAME(object_id, database_id))  
    , *   
FROM sys.dm_db_index_operational_stats(null, null, null, null);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-objectname-in-a-where-clause"></a>D. Utilisation d'OBJECT_NAME dans une clause WHERE  
 L'exemple suivant retourne les colonnes de l'affichage catalogue `sys.objects` correspondant à l'objet spécifié par `OBJECT_NAME` dans la clause `WHERE` de l'instruction `SELECT`. (Votre numéro de l’objet (274100017 dans l’exemple ci-dessous) seront différents.  Pour tester cet exemple, rechercher un numéro d’objet valide en exécutant `SELECT name, object_id FROM sys.objects;` dans votre base de données.)  
  
```  
SELECT name, object_id, type_desc  
FROM sys.objects  
WHERE name = OBJECT_NAME(274100017);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de métadonnées &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)  
  
  


