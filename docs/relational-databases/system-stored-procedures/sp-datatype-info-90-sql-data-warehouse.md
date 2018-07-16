---
title: sp_datatype_info_90 (SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1d043964-dc6e-4c3e-ab61-bc444d5e25ae
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 349297399955dd9b3f43f4507f38918507f64cff
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926720"
---
# <a name="spdatatypeinfo90-sql-data-warehouse"></a>sp_datatype_info_90 (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Retourne des informations sur les types de données pris en charge par l'environnement actuel.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_datatype_info_90 [ [ @data_type = ] data_type ]   
     [ , [ @ODBCVer = ] odbc_version ]   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@data_type=** ] *data_type*  
 Numéro de code du type de données spécifié. Pour obtenir une liste de tous les types de données, omettez ce paramètre. *data_type* est **int**, avec 0 comme valeur par défaut.  
  
 [  **@ODBCVer=** ] *le paramètre odbc_version*  
 Version d'ODBC utilisée. *le paramètre version_odbc* est **tinyint**, avec une valeur par défaut 2.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 None  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|TYPE_NAME|**sysname**|Type de données dépendant du SGBD (système de gestion de base de données)|  
|DATA_TYPE|**smallint**|Code pour le type ODBC sur lequel toutes les colonnes de ce type sont mappées.|  
|PRECISION|**Int**|Précision maximale du type de données de la source de données. La valeur NULL est retournée pour les types de données pour lesquels la précision n'est pas applicable. La valeur de retour pour la colonne PRECISION est en base 10.|  
|LITERAL_PREFIX|**varchar(** 32 **)**|Caractères utilisés devant une constante. Par exemple, un guillemet unique (**'**) pour les types de caractères et 0 x pour le fichier binaire.|  
|LITERAL_SUFFIX|**varchar(** 32 **)**|Caractères utilisés pour terminer une constante. Par exemple, un guillemet unique (**'**) pour les types de caractères et pas de guillemets pour fichier binaire.|  
|CREATE_PARAMS|**varchar(** 32 **)**|Description des paramètres de création de ce type de données. Par exemple, **décimal** est « precision, scale », **float** est NULL, et **varchar** correspond à « max_length ».|  
|NULLABLE|**smallint**|Spécifie la possibilité de contenir une valeur NULL.<br /><br /> 1 = Autorise les valeurs NULL<br /><br /> 0 = N'autorise pas les valeurs NULL|  
|CASE_SENSITIVE|**smallint**|Spécifie le respect de la casse.<br /><br /> 1 = Toutes les colonnes de ce type respectent la casse (pour les classements).<br /><br /> 0 = Toutes les colonnes de ce type ne respectent pas la casse.|  
|SEARCHABLE|**smallint**|Spécifie la capacité de recherche du type de colonne :<br /><br /> 1 = Recherche impossible.<br /><br /> 2 = Recherche possible avec LIKE.<br /><br /> 3 = Recherche possible avec WHERE.<br /><br /> 4 = Recherche possible avec WHERE ou LIKE.|  
|UNSIGNED_ATTRIBUTE|**smallint**|Spécifie la signature du type de données.<br /><br /> 1 = Type de données non signé.<br /><br /> 0 = Type de données signé.|  
|MONEY|**smallint**|Spécifie le **money** type de données.<br /><br /> 1 = **money** type de données.<br /><br /> 0 ne = pas un **money** type de données.|  
|AUTO_INCREMENT|**smallint**|Spécifie l'auto-incrémentation.<br /><br /> 1 = Auto-incrémentation<br /><br /> 0 = Pas d'auto-incrémentation<br /><br /> NULL = Attribut non applicable<br /><br /> Une application peut insérer des valeurs dans une colonne possédant cet attribut, mais elle ne peut pas mettre à jour les valeurs dans la colonne. À l’exception de la **bits** type de données, AUTO_INCREMENT est valide uniquement pour les types de données qui appartiennent à numériques exactes et catégories de types de données numériques approximatives.|  
|LOCAL_TYPE_NAME|**sysname**|Version localisée du nom de type de données dépendant de la source de données. Par exemple, DECIMAL est DECIMALE en français. La valeur NULL est retournée si un nom localisé n'est pas pris en charge par la source de données.|  
|MINIMUM_SCALE|**smallint**|Échelle minimale du type de données de la source de données. Si un type de données possède une échelle fixe, les colonnes MINIMUM_SCALE et MAXIMUM_SCALE contiennent toutes les deux cette valeur. La valeur NULL est retournée lorsque l'échelle n'est pas applicable.|  
|MAXIMUM_SCALE|**smallint**|Échelle maximale du type de données de la source de données. Si l'échelle maximale n'est pas définie séparément dans la source de données, mais si au contraire elle est définie comme étant identique à la précision maximale, cette colonne contient la même valeur que la colonne PRECISION.|  
|SQL_DATA_TYPE|**smallint**|Valeur du type de données SQL tel qu'il apparaît dans le champ TYPE du descripteur. Cette colonne est identique à la colonne DATA_TYPE, excepté pour le **datetime** et ANSI **intervalle** types de données. Ce champ retourne toujours une valeur.|  
|SQL_DATETIME_SUB|**smallint**|**date/heure** ou ANSI **intervalle** sous-code si la valeur de SQL_DATA_TYPE est SQL_DATETIME ou SQL_INTERVAL. Pour les données de types autres que **datetime** et ANSI **intervalle**, ce champ est NULL.|  
|NUM_PREC_RADIX|**Int**|Nombre de bits ou de chiffres pour calculer le nombre maximal qu’une colonne peut contenir. Si le type de données est un type de données numérique approximatif, cette colonne contient la valeur 2 pour indiquer plusieurs bits. Pour les types numériques exacts, cette colonne contient la valeur 10 pour indiquer plusieurs chiffres décimaux. Sinon, cette colonne est NULL. En combinant la précision et la base, l'application peut calculer le nombre maximal que la colonne peut contenir.|  
|INTERVAL_PRECISION|**smallint**|Valeur de précision interval si *data_type* est **intervalle**; sinon, NULL.|  
|USERTYPE|**smallint**|**usertype** valeur de la table systypes.|  
  
## <a name="remarks"></a>Notes  
 sp_datatype_info est équivalent à SQLGetTypeInfo dans ODBC. Les résultats retournés sont triés par DATA_TYPE, puis en fonction du niveau de précision de la concordance entre le type de données et le type de données ODBC SQL correspondant.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle public.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant récupère des informations pour le **sysname** et **nvarchar** des types de données en spécifiant le *data_type* valeur `-9`.  
  
```  
USE master;  
GO  
EXEC sp_datatype_info_90 -9;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de l’entrepôt de données SQL](../../relational-databases/system-stored-procedures/sql-data-warehouse-stored-procedures.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  

