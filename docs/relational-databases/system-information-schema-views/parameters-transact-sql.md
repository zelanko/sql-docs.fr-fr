---
description: PARAMETERS (Transact-SQL)
title: PARAMÈTRES (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- PARAMETERS_TSQL
- PARAMETERS
dev_langs:
- TSQL
helpviewer_keywords:
- PARAMETERS view
- INFORMATION_SCHEMA.PARAMETERS view
ms.assetid: 06ded0ca-7d21-4400-864a-b801e855b257
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 481e104f4762638fb4c71a548c3a390e1babe762
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97478930"
---
# <a name="parameters-transact-sql"></a>PARAMETERS (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Retourne une ligne pour chaque paramètre d'une fonction définie par l'utilisateur ou d'une procédure stockée accessible à l'utilisateur actuel dans la base de données active. Pour les fonctions, cette vue renvoie également une ligne avec des informations sur les valeurs de retour.  
  
 Pour récupérer des informations de ces vues, spécifiez le nom complet de **INFORMATION_SCHEMA.** _view_name_.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**SPECIFIC_CATALOG**|**nvarchar (** 128 **)**|Nom de catalogue de la routine pour laquelle cet élément constitue un paramètre|  
|**SPECIFIC_SCHEMA**|**nvarchar (** 128 **)**|Nom du schéma de la routine pour laquelle cet élément constitue un paramètre<br /><br /> Important n’utilisez pas les vues de INFORMATION_SCHEMA pour déterminer le schéma d’un objet. <strong> \* \* \* \* </strong> Les vues de INFORMATION_SCHEMA représentent seulement un sous-ensemble des métadonnées d’un objet. La seule méthode fiable pour rechercher le schéma d’un objet consiste à interroger l’affichage catalogue sys. Objects.|  
|**SPECIFIC_NAME**|**nvarchar (** 128 **)**|Nom de la routine pour laquelle cet élément constitue un paramètre|  
|**ORDINAL_POSITION**|**int**|Position ordinale du paramètre en commençant à 1. Dans le cas de la valeur de retour d'une fonction, il s'agit d'un 0.|  
|**PARAMETER_MODE**|**nvarchar (** 10 **)**|Retourne IN pour un paramètre d'entrée, OUT pour un paramètre de sortie et INOUT pour un paramètre d'entrée/sortie.|  
|**IS_RESULT**|**nvarchar (** 10 **)**|Retourne YES s'il s'agit du résultat de la routine qui est une fonction. Dans le cas contraire, la valeur retournée est NO.|  
|**AS_LOCATOR**|**nvarchar (** 10 **)**|Retourne YES si l'élément est déclaré comme localisateur. Dans le cas contraire, la valeur retournée est NO.|  
|**PARAMETER_NAME**|**nvarchar (** 128 **)**|Nom du paramètre. NULL si ceci correspond à la valeur retournée d'une fonction.|  
|**DATA_TYPE**|**nvarchar (** 128 **)**|Type de données fourni par le système.|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|Longueur maximale en caractères des données de type binaire ou caractère.<br /><br /> -1 pour les données de type **XML** et de valeur élevée. Dans le cas contraire, la valeur NULL est retournée.|  
|**CHARACTER_OCTET_LENGTH**|**int**|Longueur maximale en octets des données de type binaire ou caractère.<br /><br /> -1 pour les données de type **XML** et de valeur élevée. Dans le cas contraire, la valeur NULL est retournée.|  
|**COLLATION_CATALOG**|**nvarchar (** 128 **)**|Retourne toujours la valeur Null.|  
|**COLLATION_SCHEMA**|**nvarchar (** 128 **)**|Retourne toujours la valeur Null.|  
|**COLLATION_NAME**|**nvarchar (** 128 **)**|Nom du classement du paramètre. Retourne la valeur NULL si ce nom n'utilise pas l'un des types de caractères.|  
|**CHARACTER_SET_CATALOG**|**nvarchar (** 128 **)**|Nom de catalogue du jeu de caractères du paramètre. Retourne la valeur NULL si ce nom n'utilise pas l'un des types de caractères.|  
|**CHARACTER_SET_SCHEMA**|**nvarchar (** 128 **)**|Retourne toujours la valeur Null.|  
|**CHARACTER_SET_NAME**|**nvarchar (** 128 **)**|Nom du jeu de caractères du paramètre. Retourne la valeur NULL si ce nom n'utilise pas l'un des types de caractères.|  
|**NUMERIC_PRECISION**|**tinyint**|Précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Dans le cas contraire, la valeur NULL est retournée.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Base de précision des données numériques approchées ou exactes, des données de type entier ou monétaire. Dans le cas contraire, la valeur NULL est retournée.|  
|**NUMERIC_SCALE**|**tinyint**|Échelle des données numériques approchées ou exactes, des données de type entier ou monétaire. Dans le cas contraire, la valeur NULL est retournée.|  
|**DATETIME_PRECISION**|**smallint**|Précision en fractions de seconde si le type de paramètre est **DateTime** ou **smalldatetime**. Dans le cas contraire, la valeur NULL est retournée.|  
|**INTERVAL_TYPE**|**nvarchar (** 30 **)**|NULL. Réservé à un usage ultérieur.|  
|**INTERVAL_PRECISION**|**smallint**|NULL. Réservé à un usage ultérieur.|  
|**USER_DEFINED_TYPE_CATALOG**|**nvarchar (** 128 **)**|NULL. Réservé à un usage ultérieur.|  
|**USER_DEFINED_TYPE_SCHEMA**|**nvarchar (** 128 **)**|NULL. Réservé à un usage ultérieur.|  
|**USER_DEFINED_TYPE_NAME**|**nvarchar (** 128 **)**|NULL. Réservé à un usage ultérieur.|  
|**SCOPE_CATALOG**|**nvarchar (** 128 **)**|NULL. Réservé à un usage ultérieur.|  
|**SCOPE_SCHEMA**|**nvarchar (** 128 **)**|NULL. Réservé à un usage ultérieur.|  
|**SCOPE_NAME**|**nvarchar (** 128 **)**|NULL. Réservé à un usage ultérieur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues système &#40;&#41;Transact-SQL ](../../t-sql/language-reference.md)   
 [Vues de schémas d’informations &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)  
  
