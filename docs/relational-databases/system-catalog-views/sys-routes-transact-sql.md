---
title: sys.routes (Transact-SQL) | Microsoft Docs
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 098ff2a0a3e4827a9d80c3955cc6f2689c3fa53e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62446428"
---
# <a name="sysroutes-transact-sql"></a>sys.routes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Cet affichage catalogue contient une ligne par itinéraire. Service Broker utilise des itinéraires pour localiser l'adresse réseau d'un service.   

|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom de l'itinéraire, unique dans la base de données. Cette colonne n'accepte pas la valeur NULL.|  
|**route_id**|**Int**|Identificateur de l'itinéraire. Cette colonne n'accepte pas la valeur NULL.|  
|**principal_id**|**Int**|Identificateur du principal de base de données propriétaire de cet itinéraire. Accepte la valeur NULL.|  
|**remote_service_name**|**nvarchar (256)**|Nom du service distant. Accepte la valeur NULL.|  
|**broker_instance**|**nvarchar(128)**|Identificateur du Service Broker qui héberge le service distant. Accepte la valeur NULL.|  
|**lifetime**|**datetime**|Date et heure d’expiration de l’itinéraire. Notez que cette valeur n'utilise pas le fuseau horaire. Elle indique l'heure d'expiration au format UTC. Accepte la valeur NULL.|  
|**address**|**nvarchar (256)**|Adresse réseau à laquelle Service Broker envoie des messages pour le service distant. Accepte la valeur NULL. Pour SQL Database Managed Instance, l’adresse doit être local.|  
|**mirror_address**|**nvarchar (256)**|Adresse réseau du partenaire de mise en miroir pour le serveur spécifié dans l'adresse. Accepte la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
