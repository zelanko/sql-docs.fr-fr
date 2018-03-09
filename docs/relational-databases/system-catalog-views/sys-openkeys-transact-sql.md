---
title: Sys.openkeys (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- openkeys_TSQL
- sys.openkeys_TSQL
- openkeys
- sys.openkeys
dev_langs:
- TSQL
helpviewer_keywords:
- sys.openkeys catalog view
ms.assetid: 719a1259-2398-4fcb-ba05-aeabba7aec21
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 948e769e00448b859e5a36a175dd1fb77e222a65
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysopenkeys-transact-sql"></a>sys.openkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Cette vue de catalogue retourne des informations sur les clés de chiffrement qui sont ouvertes dans la session en cours.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID de la base de données qui contient la clé.|  
|**database_name**|**sysname**|Nom de la base de données qui contient la clé.|  
|**ID**|**int**|ID de la clé. L'ID est unique dans la base de données.|  
|**key_name**|**sysname**|Nom de la clé. Unique dans la base de données.|  
|**key_guid**|**varbinary**|GUID de la clé. Unique dans la base de données.|  
|**opened_date**|**datetime**|Date et heure d'ouverture de la clé.|  
|**status**|**int**|1 si la clé est valide dans les métadonnées. 0 si la clé est introuvable dans les métadonnées.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)  
  
  
