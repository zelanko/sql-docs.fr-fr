---
title: "Catalog.packages (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
helpviewer_keywords:
- packages view [Integration Services]
- catalog.packages view [Integration Services]
ms.assetid: a634e94d-f492-4dfd-9611-a35f545106a1
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f836c2b1bdf59f157f10abb708ed55f99dfc9f0f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogpackages-ssisdb-database"></a>catalog.packages (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les détails pour tous les packages qui s’affichent dans le **SSISDB** catalogue.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|package_id|**bigint**|Identificateur (ID) unique du package.|  
|name|**nvarchar (256)**|Nom unique du package.|  
|package_guid|**uniqueidentifier**|Identificateur global unique (GUID) qui identifie le package.|  
|description|**nvarchar (1024)**|Description facultative du package.|  
|package_format_version|**int**|Version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée pour développer le package.|  
|version_major|**int**|Version principale du package.|  
|version_minor|**int**|Version secondaire du package.|  
|version_build|**int**|Version de la build du package.|  
|version_comments|**nvarchar (1024)**|Commentaires facultatifs sur la version du package.|  
|version_guid|**uniqueidentifier**|GUID qui identifie de manière unique la version du package.|  
|project_id|**bigint**|ID unique du projet.|  
|point_entrée|**bit**|Une valeur de `1` signifie que le package est destiné à être démarré directement. Une valeur `0` signifie que le package est destiné à être démarré par un autre package avec la tâche d'exécution du package. La valeur par défaut est `1`.|  
|validation_status|**char (1)**|État de la validation.|  
|last_validation_time|**DateTimeOffset(7)**|Heure de la dernière validation.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche une ligne pour chaque package dans le catalogue.  
  
## <a name="permissions"></a>Permissions  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur le projet correspondant  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur.  
  
> [!NOTE]  
>  Si vous avez l'autorisation READ sur un projet, vous avez également l'autorisation READ sur toutes les packages et les références environnementales associés à ce projet. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  

