---
description: sys. database_scoped_configurations (Transact-SQL)
title: sys. database_scoped_configurations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- database_scoped_configurations
- database_scoped_configurations_TSQL
- sys.database_scoped_configurations
- sys.database_scoped_configurations_TSQL
helpviewer_keywords:
- sys.database_scoped_configurations catalog view
ms.assetid: 8899310a-3464-4d38-9f2f-88396c4e7dc2
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current||= azure-sqldw-latest
ms.openlocfilehash: 6edd7864c127ea068e3017c7aa26ad5be86a4c8a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88323245"
---
# <a name="sysdatabase_scoped_configurations-transact-sql"></a>sys. database_scoped_configurations (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-addw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

Contient une ligne par configuration. 

|Nom de la colonne|Type de données|Description|
|-----------------|---------------|-----------------|
|**configuration_id**|**int**|ID de l’option de configuration.|
|**name**|**nvarchar(60)**|Nom de l’option de configuration. Pour plus d’informations sur les configurations possibles, consultez [ALTER DATABASE scoped configuration &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|
|**value**|**SQLVARIANT**|Valeur définie pour cette option de configuration pour le réplica principal.|
|**value_for_secondary**|**SQLVARIANT**|Valeur définie pour cette option de configuration pour les réplicas secondaires.|
|**is_value_default**|**bit** |Spécifie si la valeur définie est la valeur par défaut.|
|**dw_compatibility_level**|**int**|Niveau de compatibilité (version préliminaire) de la base de données.  Valeur par défaut = 0 (AUTO)|

## <a name="permissions"></a><a name="Permissions"></a> Autorisations

Nécessite l'appartenance au rôle **public** .

## <a name="remarks"></a>Notes

Lorsque la valeur NULL est retournée en tant que valeur pour **value_for_secondary**, cela signifie que la base de données secondaire est définie sur Primary.
 
Les paramètres configurés au niveau de la base de données sont reportés avec la base de données. Cela signifie que lorsqu’une base de données est restaurée ou jointe, les paramètres de configuration existants sont conservés.

## <a name="see-also"></a>Voir aussi

[ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)
