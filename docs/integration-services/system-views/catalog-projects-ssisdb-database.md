---
title: "Catalog.Projects (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a6b595e1-5227-47ce-8ee2-a28c1e1d5645
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 668890ae464deb8dfa029eab38b608fee12af0ca
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogprojects-ssisdb-database"></a>catalog.projects (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les détails pour tous les projets qui s’affichent dans le **SSISDB** catalogue.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|project_id|**bigint**|Identificateur (ID) unique du projet.|  
|folder_id|**bigint**|ID unique du dossier où le projet réside.|  
|name|**sysname**|Nom du projet.|  
|description|**nvarchar (1024)**|Description facultative du projet.|  
|project_format_version|**int**|Version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée pour développer le projet.|  
|deployed_by_sid|**varbinary(85)**|Identificateur de sécurité (SID) de l'utilisateur qui a installé le projet.|  
|deployed_by_name|**nvarchar (128)**|Nom de l'utilisateur qui a installé le projet.|  
|last_deployed_time|**DateTimeOffset(7)**|Date et heure auxquelles le projet a été déployé ou a été redéployé.|  
|created_time|**DateTimeOffset(7)**|La date et l’heure à laquelle le projet a été créé.|  
|object_version_lsn|**bigint**|Version du projet. Ce nombre n'est pas obligatoirement séquentiel.|  
|validation_status|**char (1)**|État de validation.|  
|last_validation_time|**DateTimeOffset(7)**|Heure de la dernière validation.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche une ligne pour chaque projet dans le catalogue.  
  
## <a name="permissions"></a>Permissions  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur le projet  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur.  
  
> [!NOTE]  
>  Si vous avez l'autorisation READ sur un projet, vous avez également l'autorisation READ sur toutes les packages et les références environnementales associés à ce projet. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  
