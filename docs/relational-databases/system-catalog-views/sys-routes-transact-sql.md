---
title: sys. routes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 2769fcd0ec6dde419c9ebba2f3cfb0017cf74b0b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831385"
---
# <a name="sysroutes-transact-sql"></a>sys.routes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Cet affichage catalogue contient une ligne par itinéraire. Service Broker utilise des itinéraires pour localiser l'adresse réseau d'un service.   

|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom de l'itinéraire, unique dans la base de données. Cette colonne n'accepte pas la valeur NULL.|  
|**route_id**|**int**|Identificateur de l'itinéraire. Cette colonne n'accepte pas la valeur NULL.|  
|**principal_id**|**int**|Identificateur du principal de base de données propriétaire de cet itinéraire. Accepte la valeur NULL.|  
|**remote_service_name**|**nvarchar(256)**|Nom du service distant. Accepte la valeur NULL.|  
|**broker_instance**|**nvarchar(128)**|Identificateur du Service Broker qui héberge le service distant. Accepte la valeur NULL.|  
|**cycle**|**datetime**|Date et heure d’expiration de l’itinéraire. Notez que cette valeur n'utilise pas le fuseau horaire. Elle indique l'heure d'expiration au format UTC. Accepte la valeur NULL.|  
|**address**|**nvarchar(256)**|Adresse réseau à laquelle Service Broker envoie des messages pour le service distant. Accepte la valeur NULL. Pour SQL Database Managed Instance, l’adresse doit être locale.|  
|**mirror_address**|**nvarchar(256)**|Adresse réseau du partenaire de mise en miroir pour le serveur spécifié dans l'adresse. Accepte la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
