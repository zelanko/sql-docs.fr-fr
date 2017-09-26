---
title: "Catalog.Environments (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 7014c0e3-65dc-4a46-842e-4decf3737748
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6e7ba1ba0bd8a444e4609a2f3d011da9cd233b73
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogenvironments-ssisdb-database"></a>catalog.environments (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les détails de l'environnement pour tous les environnements dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Les environnements contiennent des variables qui peuvent être référencées par les projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|environment_id|**bigint**|Identificateur (ID) unique de l'environnement.|  
|name|**sysname**|Nom de l'environnement.|  
|folder_id|**bigint**|ID unique du dossier dans lequel l'environnement réside.|  
|description|**nvarchar (1024)**|Description de l'environnement. Cette valeur est facultative.|  
|created_by_sid|**varbinary(85)**|Identificateur de sécurité (SID) unique de l'utilisateur qui a créé l'environnement.|  
|created_by_name|**nvarchar (128)**|Nom de l'utilisateur qui a créé l'environnement.|  
|created_time|**datetimeoffset**|Date et heure de création de l'environnement.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche une ligne pour chaque environnement dans le catalogue. Les noms d'environnement sont uniques uniquement en ce qui concerne le dossier dans lequel ils se trouvent. Par exemple, un environnement nommé `E1` peut exister dans plusieurs dossiers dans le catalogue, mais chaque dossier peut avoir un seul environnement nommé `E1`.  
  
## <a name="permissions"></a>Permissions  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'environnement  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
> [!NOTE]  
>  La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  
