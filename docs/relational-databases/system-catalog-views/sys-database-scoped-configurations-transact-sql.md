---
title: Sys.database_scoped_configurations (Transact-SQL) | Microsoft Docs
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 350f3af1bfd6e2765f74d074727577541378d2e2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733833"
---
# <a name="sysdatabasescopedconfigurations-transact-sql"></a>Sys.database_scoped_configurations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Contient une ligne par configuration. 
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**configuration_id**|**Int**|ID de l’option de configuration.|  
|**nom**|**nvarchar(60)**|Le nom de l’option de configuration. Pour plus d’informations sur les configurations possibles, consultez [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|  
|**value**|**sqlvariant**|La valeur définie pour cette option de configuration pour le réplica principal.|  
|**value_for_secondary**|**sqlvariant**|La valeur définie pour cette option de configuration pour les réplicas secondaires.|  
|**elevate_online**|**nvarchar(60)** |La base de données étendue ensemble par défaut pour l’option online pour les opérations d’index |
|**elevate_resumable**|nvarchar(60)|La base de données étendue ensemble par défaut pour l’option pouvant être reprise des opérations d’index| 
  
##  <a name="Permissions"></a> Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="remarks"></a>Notes  
 Lorsque la valeur NULL est retournée comme valeur pour **value_for_secondary**, cela signifie que la base de données secondaire est défini dans la région primaire.  
 
 Les paramètres configurés au niveau de la base de données sont reportés avec la base de données. Cela signifie que lorsqu’une base de données est restaurée ou jointe, les paramètres de configuration existants sont conservés.
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)  
  
  
