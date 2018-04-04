---
title: Sys.routes (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- routes
- routes_TSQL
- sys.routes
- sys.routes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.routes catalog view
ms.assetid: 8fc65915-8bd6-425b-95d9-6a8468cb1e48
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 21420e923b4120f547026c6a6a0d96d86deac782
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2018
---
# <a name="sysroutes-transact-sql"></a>sys.routes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Cet affichage catalogue contient une ligne par itinéraire. Service Broker utilise des itinéraires pour localiser l'adresse réseau d'un service.   

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom de l'itinéraire, unique dans la base de données. Cette colonne n'accepte pas la valeur NULL.|  
|**route_id**|**int**|Identificateur de l'itinéraire. Cette colonne n'accepte pas la valeur NULL.|  
|**principal_id**|**int**|Identificateur du principal de base de données propriétaire de cet itinéraire. Accepte la valeur NULL.|  
|**remote_service_name**|**nvarchar (256)**|Nom du service distant. Accepte la valeur NULL.|  
|**broker_instance**|**nvarchar(128)**|Identificateur du Service Broker qui héberge le service distant. Accepte la valeur NULL.|  
|**lifetime**|**datetime**|Date et heure d’expiration de l’itinéraire. Notez que cette valeur n'utilise pas le fuseau horaire. Elle indique l'heure d'expiration au format UTC. Accepte la valeur NULL.|  
|**address**|**nvarchar (256)**|Adresse réseau à laquelle Service Broker envoie des messages pour le service distant. Accepte la valeur NULL. Pour l’Instance gérée de base de données SQL, l’adresse doit être local.|  
|**mirror_address**|**nvarchar (256)**|Adresse réseau du partenaire de mise en miroir pour le serveur spécifié dans l'adresse. Accepte la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
