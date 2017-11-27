---
title: Sys.sql_modules (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sql_modules_TSQL
- sql_modules
- sql_modules_TSQL
- sys.sql_modules
dev_langs: TSQL
helpviewer_keywords: sys.sql_modules catalog view
ms.assetid: 23d3ccd2-f356-4d89-a2cd-bee381243f99
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 496ed3e4d3aad1cea7a0b9c153f4e85da1a46489
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="syssqlmodules-transact-sql"></a>sys.sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une ligne pour chaque objet qui est un module de définie par le langage SQL dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], y compris en mode natif compilé fonction scalaire définie par l’utilisateur. Les objets de type P, RF, V, TR, FN, IF, TF et R possèdent un module SQL associé. Les valeurs par défaut autonomes, les objets de type D, possèdent également une définition de module SQL dans cette vue. Pour obtenir une description de ces types, consultez le **type** colonne dans la [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) affichage catalogue.  
  
 Pour plus d’informations, consultez [Scalar User-Defined des fonctions pour l’OLTP en mémoire](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID d'objet de l'objet conteneur. Unique dans une base de données.|  
|**définition**|**nvarchar(max)**|Texte SQL qui définit ce module.<br /><br /> NULL = chiffré|  
|**uses_ansi_nulls**|**bit**|Le module a été créé avec SET ANSI_NULLS ON.<br /><br /> Sera toujours = 0 pour les règles et les valeurs par défaut.|  
|**uses_quoted_identifier**|**bit**|Le module a été créé avec SET QUOTED_IDENTIFIER ON.|  
|**is_schema_bound**|**bit**|Module créé avec l'option SCHEMABINDING.<br /><br /> Contient toujours la valeur 1 pour les procédures stockées compilées en mode natif.|  
|**uses_database_collation**|**bit**|1 = La définition d'un module lié au schéma dépend du classement par défaut de la base de données pour une évaluation correcte ; dans tous les autres cas, 0. Une telle dépendance évite la modification du classement par défaut de la base de données.|  
|**is_recompiled**|**bit**|Procédure créée avec l'option WITH RECOMPILE.|  
|**null_on_null_input**|**bit**|Le module a été déclaré pour produire une sortie NULL sur n'importe quelle entrée NULL.|  
|**execute_as_principal_id**|**Int**|ID du principal de base de données EXECUTE AS.<br /><br /> Valeur NULL par défaut ou dans le cas de l'instruction EXECUTE AS CALLER.<br /><br /> ID du principal spécifié si EXECUTE AS SELF ou EXECUTE AS \<principal >.<br /><br /> -2 = EXECUTE AS OWNER.|  
|**uses_native_compilation**|**bit**|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].<br /><br /> 0 = Non compilé en mode natif<br /><br /> 1 = Compilé en mode natif<br /><br /> La valeur par défaut est 0 :|  
  
## <a name="remarks"></a>Notes  
 L’expression SQL pour une contrainte par défaut, l’objet de type D, se trouve dans le [sys.default_constraints](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md) affichage catalogue. L’expression SQL pour une contrainte CHECK, objet de type C, se trouve dans le [sys.check_constraints](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md) affichage catalogue.  
  
 Cette information est également décrit dans [sys.dm_db_uncontained_entities &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne le nom, le type et la définition de chaque module dans la base de données actuelle.  
  
```  
SELECT sm.object_id, OBJECT_NAME(sm.object_id) AS object_name, o.type, o.type_desc, sm.definition  
FROM sys.sql_modules AS sm  
JOIN sys.objects AS o ON sm.object_id = o.object_id  
ORDER BY o.type;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Interrogation des catalogues système SQL Server FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
