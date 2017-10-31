---
title: OBJECT_SCHEMA_NAME (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECT_SCHEMA_NAME
- OBJECT_SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], names
- schemas [SQL Server], names
- displaying schema names
- database objects [SQL Server], names
- OBJECT_SCHEMA_NAME function
ms.assetid: 5ba90bb9-d045-4164-963e-e9e96c0b1e8b
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 621a58fcc00b95626f3e4eb7d34d79af608436fe
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="objectschemaname-transact-sql"></a>OBJECT_SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne le nom de schéma de base de données des objets de portée de schéma. Pour obtenir la liste d’objets de portée de schéma, consultez [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
OBJECT_SCHEMA_NAME ( object_id [, database_id ] )  
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
  
 Un utilisateur peut voir uniquement les métadonnées des éléments sécurisables qui lui appartiennent ou pour lesquels il dispose d'une autorisation. Cela signifie que les fonctions intégrées générant des métadonnées, telles que OBJECT_SCHEMA_NAME, peuvent retourner la valeur NULL si l'utilisateur ne dispose d'aucune autorisation sur l'objet. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ANY sur l'objet. Pour spécifier un ID de base de données, l'autorisation CONNECT à la base de données est également nécessaire ou le compte Invité doit être activé.  
  
## <a name="remarks"></a>Notes  
 Les fonctions système peuvent être utilisées dans la liste de sélection, dans une clause WHERE, et partout où une expression est autorisée. Pour plus d’informations, consultez [Expressions](../../t-sql/language-elements/expressions-transact-sql.md) et [où](../../t-sql/queries/where-transact-sql.md).  
  
 Le jeu de résultats retourné par cette fonction système utilise le classement de la base de données active.  
  
 Si *database_id* n’est pas spécifié, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] suppose que *object_id* est dans le contexte de la base de données actuelle. Une requête qui fait référence à un *object_id* dans une autre base de données renvoie NULL ou des résultats incorrects. Par exemple, dans la requête suivante, le contexte de la base de données active est [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] essaie de retourner un nom d'objet pour l'ID d'objet spécifié, à partir de cette base de données et non de la base de données indiquée dans la clause FROM de la requête. Par conséquent, des informations incorrectes sont retournées.  
  
```  
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id)  
FROM master.sys.objects;  
  
```  
  
 L'exemple suivant spécifie l'ID de base de données pour la base de données `master` dans la fonction `OBJECT_SCHEMA_NAME` et retourne les résultats corrects.  
  
```  
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id, 1) AS schema_name  
FROM master.sys.objects;  
  
```  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-the-object-schema-name-and-object-name"></a>A. Retour du nom de schéma d'objet et du nom d'objet  
 L'exemple suivant retourne le nom de schéma d'objet, le nom d'objet et le texte SQL pour tous les plans de requête mis en cache qui ne sont pas des instructions ad hoc ou préparées.  
  
```  
SELECT DB_NAME(st.dbid) AS database_name,   
    OBJECT_SCHEMA_NAME(st.objectid, st.dbid) AS schema_name,  
    OBJECT_NAME(st.objectid, st.dbid) AS object_name,   
    st.text AS query_statement  
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
WHERE st.objectid IS NOT NULL;  
GO  
```  
  
### <a name="b-returning-three-part-object-names"></a>B. Retour de noms d'objet en trois parties  
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
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de métadonnées &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [Object_id &#40; Transact-SQL &#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [Nom_objet &#40; Transact-SQL &#41;](../../t-sql/functions/object-name-transact-sql.md)   
 [Éléments sécurisables](../../relational-databases/security/securables.md)  
  
  

