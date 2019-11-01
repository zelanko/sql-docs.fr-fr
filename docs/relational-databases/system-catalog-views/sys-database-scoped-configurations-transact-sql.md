---
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: da115c8d4cf48cfbcd6190c88a83bee4e61ae5a1
ms.sourcegitcommit: 27c267bf2a3cfaf2abcb5f3777534803bf4cffe5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73240771"
---
# <a name="sysdatabase_scoped_configurations-transact-sql"></a>sys. database_scoped_configurations (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Contient une ligne par configuration. 

|Nom de colonne|Data type|Description|
|-----------------|---------------|-----------------|
|**configuration_id**|**Int**|ID de l’option de configuration.|
|**nom**|**nvarchar(60)**|Nom de l’option de configuration. Pour plus d’informations sur les configurations possibles, consultez [ALTER DATABASE scoped &#40;configuration Transact-&#41;SQL](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|
|**valeur**|**SQLVARIANT**|Valeur définie pour cette option de configuration pour le réplica principal.|
|**value_for_secondary**|**SQLVARIANT**|Valeur définie pour cette option de configuration pour les réplicas secondaires.|
|**is_value_default**|**bit** |Spécifie si la valeur définie est la valeur par défaut.|

## <a name="Permissions"></a> Permissions

Nécessite l'appartenance au rôle **public** .

## <a name="remarks"></a>Notes

Lorsque la valeur NULL est retournée comme valeur pour **value_for_secondary**, cela signifie que la base de données secondaire est définie sur Primary.
 
Les paramètres configurés au niveau de la base de données sont reportés avec la base de données. Cela signifie que lorsqu’une base de données est restaurée ou jointe, les paramètres de configuration existants sont conservés.

## <a name="see-also"></a>Voir aussi

[ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)
