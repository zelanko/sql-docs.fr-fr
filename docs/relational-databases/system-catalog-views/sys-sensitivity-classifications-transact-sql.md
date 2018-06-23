---
title: Sys.sensitivity_classifications (Transact-SQL) | Documents Microsoft
ms.date: 06/17/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: t-sql
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: giladm
author: giladmit
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
ms.openlocfilehash: d0adbbeb82c06d6a44f3a7439bcbf479d7358401
ms.sourcegitcommit: 70882926439a63ab9d812809429c63040eb9a41b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36262884"
---
# <a name="syssensitivityclassifications-transact-sql"></a>Sys.sensitivity_classifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Retourne une ligne pour chaque élément classé dans la base de données.

|Nom de colonne|Type de données|Description|
|-----------------|---------------|-----------------|  
|**class**|**Int**|Identifie la classe de l’élément sur lequel se trouve la classification|  
|**class_desc**|**varchar (16)**|Une description de la classe de l’élément sur lequel se trouve la classification|  
|**major_id**|**Int**|ID de l’élément sur lequel se trouve la classification. < br \>< br \>si la classe est 0, major_id est toujours 0.<br>Si la valeur de class est 1, 2 ou 7, major_id est object_id.|  
|**minor_id**|**Int**|ID secondaire de l’élément sur lequel la classification existe, interprété en fonction de sa classe.<br><br>Si classe = 1, minor_id est le paramètre column_id (Si colonne), ou 0 (si objet).<br>Si class = 2, minor_id est parameter_id.<br>Si classe = 7, minor_id est index_id. |  
|**label**|**sysname**|L’étiquette (lisibles par l’utilisateur) attribué pour la classification de sensibilité|  
|**label_id**|**sysname**|Un ID associé à l’étiquette, qui peut être utilisée par un système de protection des informations telles que Azure Information Protection administrative.|  
|**information_type**|**sysname**|Le type d’informations (lisibles par l’utilisateur) attribué pour la classification de sensibilité|  
|**information_type_id**|**sysname**|Un ID associé au type d’informations, qui peut être utilisé par un système de protection des informations telles que Azure Information Protection administrative.|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Notes  

- Cet affichage offre une visibilité de l’état de la classification de la base de données. Il peut être utilisé pour gérer les classifications de base de données, ainsi que pour la génération de rapports.
- Actuellement, seul classement des colonnes de la base de données est prise en charge. Par conséquent :
    - **classe** -aura toujours la valeur 1 (représentant une colonne)
    - **class_desc** -aura toujours la valeur *OBJECT_OR_COLUMN*
    - **major_id** -représente l’ID de la table contenant la colonne classée, correspondant avec sys.all_objects.object_id
    - **minor_id** -représente l’ID de la colonne sur lequel existe la classification, correspondante avec sys.all_columns.column_id

## <a name="examples"></a>Exemples

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. Liste classée de toutes les colonnes et leur classement correspondant

L’exemple suivant retourne un tableau qui répertorie le nom de la table, le nom de colonne, l’étiquette, l’étiquette ID, type d’information, ID du type d’informations pour chaque colonne classée dans la base de données.

```sql
SELECT
    sys.all_objects.name AS TableName, sys.all_columns.name As ColumnName,
    Label, Label_ID, Information_Type, Information_Type_ID
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="see-also"></a>Voir aussi  

[AJOUTER la sensibilité CLASSIFICTION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[SUPPRIMER la sensibilité CLASSIFICTION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[Prise en main de la Protection des informations SQL](http://aka.ms/sqlip)
