---
description: catalog.projects (base de données SSISDB)
title: catalog.projects (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: a6b595e1-5227-47ce-8ee2-a28c1e1d5645
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 874d4a89af11ab022ce2714334b9aefb506de1a6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421993"
---
# <a name="catalogprojects-ssisdb-database"></a>catalog.projects (base de données SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Affiche les détails pour tous les projets qui s’affichent dans le catalogue **SSISDB**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|project_id|**bigint**|Identificateur (ID) unique du projet.|  
|folder_id|**bigint**|ID unique du dossier où le projet réside.|  
|name|**sysname**|Nom du projet.|  
|description|**nvarchar(1024)**|Description facultative du projet.|  
|project_format_version|**int**|Version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée pour développer le projet.|  
|deployed_by_sid|**varbinary(85)**|Identificateur de sécurité (SID) de l'utilisateur qui a installé le projet.|  
|deployed_by_name|**nvarchar(128)**|Nom de l'utilisateur qui a installé le projet.|  
|last_deployed_time|**datetimeoffset(7)**|Date et heure auxquelles le projet a été déployé ou a été redéployé.|  
|created_time|**datetimeoffset(7)**|Date et heure de création du projet.|  
|object_version_lsn|**bigint**|Version du projet. Ce nombre n'est pas obligatoirement séquentiel.|  
|validation_status|**char(1)**|État de validation.|  
|last_validation_time|**datetimeoffset(7)**|Heure de la dernière validation.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche une ligne pour chaque projet dans le catalogue.  
  
## <a name="permissions"></a>Autorisations  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur le projet  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**.  
  
> [!NOTE]  
>  Si vous avez l'autorisation READ sur un projet, vous avez également l'autorisation READ sur toutes les packages et les références environnementales associés à ce projet. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  
