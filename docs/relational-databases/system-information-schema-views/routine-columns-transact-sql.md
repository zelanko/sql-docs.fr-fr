---
title: ROUTINE_COLUMNS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- ROUTINE_COLUMNS_TSQL
- ROUTINE_COLUMNS
dev_langs:
- TSQL
helpviewer_keywords:
- ROUTINE_COLUMNS view
- INFORMATION_SCHEMA.ROUTINE_COLUMNS view
ms.assetid: 91dbc61b-e4c0-4826-976c-b2fce88b7793
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a64a34e0b127aba39b1fe38d7f42bd61c72ea411
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815067"
---
# <a name="routinecolumns-transact-sql"></a>ROUTINE_COLUMNS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque colonne retournée par les fonctions table, accessibles à l'utilisateur actuel de la base de données active.  
  
 Pour récupérer des informations à partir de cette vue, spécifiez le nom qualifié complet de **INFORMATION_SCHEMA. *** nom_vue*.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar(** 128 **)**|Nom du catalogue ou de la base de données de la fonction table|  
|**TABLE_SCHEMA**|**nvarchar(** 128 **)**|Nom du schéma qui contient la fonction table.<br /><br /> **\*\* Important \* \***  n’utilisez pas les vues INFORMATION_SCHEMA pour déterminer le schéma d’un objet. La seule méthode fiable pour rechercher le schéma d’un objet est d’interroger l’affichage catalogue sys.objects.|  
|**TABLE_NAME**|**nvarchar(** 128 **)**|Nom de la fonction table|  
|**COLUMN_NAME**|**nvarchar(** 128 **)**|Nom de colonne.|  
|**ORDINAL_POSITION**|**Int**|Numéro d’identification de colonne.|  
|**COLUMN_DEFAULT**|**nvarchar (** 4000 **)**|Valeur par défaut de la colonne.|  
|**IS_NULLABLE**|**varchar (** 3 **)**|Si cette colonne accepte la valeur NULL, elle retourne la valeur YES. Dans le cas contraire, la valeur retournée est NO.|  
|**DATA_TYPE**|**nvarchar(** 128 **)**|Type de données fourni par le système.|  
|**CHARACTER_MAXIMUM_LENGTH**|**Int**|Longueur maximale (en caractères) des données de type binaire, caractère, texte et image.<br /><br /> -1 pour **xml** et les données de type de valeur élevée. Dans le cas contraire, la valeur NULL est retournée. Pour plus d’informations, consultez [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).|  
|**CHARACTER_OCTET_LENGTH**|**Int**|Longueur maximale, en octets, des données de type binaire, caractère, texte et image.<br /><br /> -1 pour **xml** et les données de type de valeur élevée. Dans le cas contraire, la valeur NULL est retournée.|  
|**NUMERIC_PRECISION**|**tinyint**|Précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Dans le cas contraire, la valeur NULL est retournée.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Base de précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Dans le cas contraire, la valeur NULL est retournée.|  
|**NUMERIC_SCALE**|**tinyint**|Échelle des données numériques approchées ou exactes, des données de type entier ou monétaire. Dans le cas contraire, la valeur NULL est retournée.|  
|**DATETIME_PRECISION**|**smallint**|Code de sous-type pour **datetime** et ISO**entier** types de données. Retourne la valeur NULL pour les autres types de données.|  
|**CHARACTER_SET_CATALOG**|**varchar (** 6 **)**|Retourne **master**. Cela indique la base de données dans lequel le jeu de caractères se trouve si la colonne est de données de type caractère ou **texte** type de données. Dans le cas contraire, la valeur NULL est retournée.|  
|**CHARACTER_SET_SCHEMA**|**varchar (** 3 **)**|Retourne toujours la valeur Null.|  
|**CHARACTER_SET_NAME**|**nvarchar(** 128 **)**|Retourne le nom unique pour le jeu de caractères si cette colonne est de données de type caractère ou **texte** type de données. Dans le cas contraire, la valeur NULL est retournée.|  
|**COLLATION_CATALOG**|**varchar (** 6 **)**|Retourne toujours la valeur Null.|  
|**COLLATION_SCHEMA**|**varchar (** 3 **)**|Retourne toujours la valeur Null.|  
|**COLLATION_NAME**|**nvarchar(** 128 **)**|Retourne le nom unique pour l’ordre de tri si la colonne est de données de type caractère ou **texte** type de données. Dans le cas contraire, la valeur NULL est retournée.|  
|**DOMAIN_CATALOG**|**nvarchar(** 128 **)**|Si la colonne est un type de données alias, elle correspond au nom de la base de données dans laquelle le type de données défini par l'utilisateur a été créé. Dans le cas contraire, la valeur NULL est retournée.|  
|**DOMAIN_SCHEMA**|**nvarchar(** 128 **)**|Si la colonne est un type de données défini par l'utilisateur, elle représente le nom du schéma qui contient le type de données défini par l'utilisateur. Dans le cas contraire, la valeur NULL est retournée.<br /><br /> **\*\* Important \* \***  n’utilisez pas les vues INFORMATION_SCHEMA pour déterminer le schéma d’un objet. La seule méthode fiable pour rechercher le schéma d’un objet est d’interroger l’affichage catalogue sys.objects.|  
|**NOM_DOMAINE**|**nvarchar(** 128 **)**|Si la colonne est un type de données défini par l'utilisateur, elle représente le nom du type de données défini par l'utilisateur. Dans le cas contraire, la valeur NULL est retournée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues système &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Vues de schémas d’informations &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
