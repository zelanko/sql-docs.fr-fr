---
title: "Catalog.object_versions (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 2fd8c020-1c77-4702-8e6b-efa6a348daab
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3ea7c5ae054a002b9bb4f150e60f323ae03d702a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogobjectversions-ssisdb-database"></a>catalog.object_versions (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les versions d'objets dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Dans cette version, seules les versions des projets sont prises en charge par cette vue.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|object_version_lsn|**bigint**|Identificateur unique (ID) de la version de l'objet. Ce nombre n'est pas obligatoirement séquentiel.|  
|object_id|**bigint**|ID unique de l'objet.|  
|object_type|**smallint**|Type de l'objet. Une valeur de `20` sera affichée pour les projets.|  
|object_name|**sysname(nvarchar(128))**|Nom de l'objet.|  
|description|**nvarchar (1024)**|Description du projet.|  
|created_by|**nvarchar (128)**|Nom de l'utilisateur qui a ajouté l'objet au catalogue.|  
|created_time|**datetimeoffset**|Date et heure auxquelles l'objet a été ajouté au catalogue.|  
|restored_by|**nvarchar (128)**|Nom de l'utilisateur qui a restauré l'objet.|  
|last_restored_time|**datetimeoffset**|Date et heure auxquelles l'objet a été restauré dernièrement.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche une ligne pour chaque version d'un objet dans le catalogue.  
  
## <a name="permissions"></a>Permissions  
 Pour consulter des lignes dans cette vue, vous devez avoir l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'objet  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur.  
  
> [!NOTE]  
>  La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  

