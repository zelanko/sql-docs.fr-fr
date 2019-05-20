---
title: catalog.environments (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 7014c0e3-65dc-4a46-842e-4decf3737748
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9c3660f7314ce9514b4dc03ee2d6fb1490a4eab7
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65715261"
---
# <a name="catalogenvironments-ssisdb-database"></a>catalog.environments (base de données SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les détails de l'environnement pour tous les environnements dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Les environnements contiennent des variables qui peuvent être référencées par les projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|environment_id|**bigint**|Identificateur (ID) unique de l'environnement.|  
|NAME|**sysname**|Nom de l'environnement.|  
|folder_id|**bigint**|ID unique du dossier dans lequel l'environnement réside.|  
|description|**nvarchar(1024)**|Description de l'environnement. Cette valeur est facultative.|  
|created_by_sid|**varbinary(85)**|Identificateur de sécurité (SID) unique de l'utilisateur qui a créé l'environnement.|  
|created_by_name|**nvarchar(128)**|Nom de l'utilisateur qui a créé l'environnement.|  
|created_time|**datetimeoffset**|Date et heure de création de l'environnement.|  
  
## <a name="remarks"></a>Notes   
 Cette vue affiche une ligne pour chaque environnement dans le catalogue. Les noms d'environnement sont uniques uniquement en ce qui concerne le dossier dans lequel ils se trouvent. Par exemple, un environnement nommé `E1` peut exister dans plusieurs dossiers dans le catalogue, mais chaque dossier peut avoir un seul environnement nommé `E1`.  
  
## <a name="permissions"></a>Autorisations  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'environnement  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
> [!NOTE]  
>  La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  
