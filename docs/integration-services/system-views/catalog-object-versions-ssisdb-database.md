---
description: catalog.object_versions (base de données SSISDB)
title: catalog.object_versions (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 2fd8c020-1c77-4702-8e6b-efa6a348daab
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a2371508c40e60ebacbe60d656d4d9ffa3f70ce
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422033"
---
# <a name="catalogobject_versions-ssisdb-database"></a>catalog.object_versions (base de données SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Affiche les versions d'objets dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Dans cette version, seules les versions des projets sont prises en charge par cette vue.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|object_version_lsn|**bigint**|Identificateur unique (ID) de la version de l'objet. Ce nombre n'est pas obligatoirement séquentiel.|  
|object_id|**bigint**|ID unique de l'objet.|  
|object_type|**smallint**|Type d'objet. Une valeur de `20` sera affichée pour les projets.|  
|object_name|**sysname(nvarchar(128))**|Nom de l'objet.|  
|description|**nvarchar(1024)**|Description du projet.|  
|created_by|**nvarchar(128)**|Nom de l'utilisateur qui a ajouté l'objet au catalogue.|  
|created_time|**datetimeoffset**|Date et heure auxquelles l'objet a été ajouté au catalogue.|  
|restored_by|**nvarchar(128)**|Nom de l'utilisateur qui a restauré l'objet.|  
|last_restored_time|**datetimeoffset**|Date et heure auxquelles l'objet a été restauré dernièrement.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche une ligne pour chaque version d'un objet dans le catalogue.  
  
## <a name="permissions"></a>Autorisations  
 Pour consulter des lignes dans cette vue, vous devez avoir l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'objet  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
> [!NOTE]  
>  La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  
