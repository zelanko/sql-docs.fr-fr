---
title: catalog.folders (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 21a37c16-60aa-4b3f-8bca-ac90ad1697ac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 14930bfd90b242f30a8b3f265f6ed3b367bd07f9
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "71296538"
---
# <a name="catalogfolders-ssisdb-database"></a>catalog.folders (base de données SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les dossiers dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|id|**bigint**|Identificateur unique du dossier.|  
|name|**sysname(nvarchar(128)**|Nom du dossier, qui est unique dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|  
|description|**nvarchar(1024)**|Description du dossier.|  
|created_by_sid|**varbinary(85)**|Identificateur de sécurité (SID) unique de l'utilisateur qui a créé le dossier.|  
|created_by_name|**nvarchar(128)**|Nom de l'utilisateur qui a créé le dossier.|  
|created_time|**datetimeoffset(7)**|Date et heure de création du dossier.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche une ligne pour chaque dossier dans le catalogue.  
  
## <a name="permissions"></a>Autorisations  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur le dossier  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
> [!NOTE]  
>  Lorsque vous avez l'autorisation pour effectuer une opération sur le serveur, vous avez également l'autorisation pour consulter les informations de l'opération. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  
