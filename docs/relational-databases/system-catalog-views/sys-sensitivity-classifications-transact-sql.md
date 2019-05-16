---
title: sys.sensitivity_classifications (Transact-SQL) | Microsoft Docs
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: arib
author: vainolo
f1_keywords:
- 'sys.sensitivity_classifications '
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sensitivity_classifications statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: c87f0fd65f5657d2885a2c7ea078ecaea7a2c717
ms.sourcegitcommit: 4cb96c291529e9bdf0a95fb3610b350583eb36d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65709113"
---
# <a name="syssensitivityclassifications-transact-sql"></a>sys.sensitivity_classifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Retourne une ligne pour chaque élément classifiée dans la base de données.

|Nom de colonne|Type de données|Description|
|-----------------|---------------|-----------------|  
|**class**|**Int**|Identifie la classe de l’élément sur lequel se trouve la classification|  
|**class_desc**|**varchar(16)**|Une description de la classe de l’élément sur lequel se trouve la classification|  
|**major_id**|**Int**|ID de l’élément sur lequel se trouve la classification. < br \>< br \>si classe est 0, major_id est toujours 0.<br>Si la valeur de class est 1, 2 ou 7, major_id est object_id.|  
|**minor_id**|**Int**|ID secondaire de l’élément sur lequel la classification existe, interprété en fonction de sa classe.<br><br>Si classe = 1, minor_id est column_id (Si colonne), ou 0 (si objet).<br>Si class = 2, minor_id est parameter_id.<br>Si classe = 7, minor_id est index_id. |  
|**label**|**sysname**|L’étiquette (lisibles par l’homme) attribuée pour la classification de sensibilité|  
|**label_id**|**sysname**|Un ID associé à l’étiquette, qui peut être utilisé par un système de protection des informations telles que Azure Information Protection (AIP)|  
|**information_type**|**sysname**|Le type d’informations (lisibles par l’homme) assigné pour la classification de sensibilité|  
|**information_type_id**|**sysname**|Un ID associé au type d’informations, ce qui peut être utilisé par un système de protection des informations telles que Azure Information Protection (AIP)|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Notes  

- Cette vue fournit une visibilité sur l’état de classification de la base de données. Il peut être utilisé pour gérer les classifications de la base de données, ainsi que pour la génération de rapports.
- Actuellement, seul classement des colonnes de la base de données est prise en charge. Par conséquent :
    - **classe** -aura toujours la valeur 1 (représentant une colonne)
    - **class_desc** -aura toujours la valeur *OBJECT_OR_COLUMN*
    - **major_id** -représente l’ID de la table contenant la colonne classifiée, correspondant avec sys.all_objects.object_id
    - **minor_id** -représente l’ID de la colonne sur lequel existe la classification, correspondante avec sys.all_columns.column_id

## <a name="examples"></a>Exemples

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. Colonnes de la liste de toutes les classés et leur classement correspondant

L’exemple suivant renvoie un tableau qui répertorie le nom de la table, le nom de colonne, l’étiquette, l’étiquette ID, type d’information, ID de type d’informations pour chaque colonne classifiée dans la base de données.

> [!NOTE]
> Étiquette est un mot clé pour Azure SQL Data Warehouse.

```sql
SELECT
    sys.all_objects.name AS [TableName], sys.all_columns.name As [ColumnName],
    [Label], [Label_ID], [Information_Type], [Information_Type_ID]
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  

## <a name="see-also"></a>Voir aussi  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[Prise en main de SQL Information Protection](https://aka.ms/sqlip)
