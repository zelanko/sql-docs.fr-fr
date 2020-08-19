---
description: catalog.environments (base de données SSISDB)
title: catalog.environments (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 7014c0e3-65dc-4a46-842e-4decf3737748
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 426199180acf6aafc609250638d00d1deb9231ec
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88495273"
---
# <a name="catalogenvironments-ssisdb-database"></a>catalog.environments (base de données SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Affiche les détails de l'environnement pour tous les environnements dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Les environnements contiennent des variables qui peuvent être référencées par les projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|environment_id|**bigint**|Identificateur (ID) unique de l'environnement.|  
|name|**sysname**|Nom de l’environnement.|  
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
  
  
