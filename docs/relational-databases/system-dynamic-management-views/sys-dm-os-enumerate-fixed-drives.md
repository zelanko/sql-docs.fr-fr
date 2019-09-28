---
title: sys. DM _os_enumerate_fixed_drives (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/18/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_enumerate_fixed_drives
- sys.dm_os_enumerate_fixed_drives_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_enumerate_fixed_drives dynamic management view
ms.assetid: 2e27489e-cf69-4a89-9036-77723ac3de66
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fa5834c14bfb1fafe3123c28a60359d64d059dfc
ms.sourcegitcommit: c4875c097e3aae1b76233777d15e0a0ec8e0d681
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342514"
---
# <a name="sysdm_os_enumerate_fixed_drives-transact-sql"></a>sys. DM _os_enumerate_fixed_drives (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Introduite dans SQL Server 2019.

Énumère les volumes montés sur des lettres de lecteur comme `C:\`.

|Nom de la colonne|Type de données|Description|
|-----------------|---------------|-----------------|  
|`fixed_drive_path`|`nvarchar(512)`|Chemin d’accès au volume, par exemple `C:\`.|  
|`drive_type`|`int`|Code pour le type de lecteur. Consultez [@no__t fonction-1](/windows/win32/api/fileapi/nf-fileapi-getdrivetypew).|
|`drive_type_desc`|`nvarchar(512)`|Description du type de lecteur. Consultez [@no__t fonction-1](/windows/win32/api/fileapi/nf-fileapi-getdrivetypew).|
|`free_space_in_bytes`|`bigint`|Espace libre du disque en octets.|

## <a name="permissions"></a>Autorisations

L’utilisateur doit disposer de l’autorisation `VIEW SERVER STATE` sur le serveur.

## <a name="see-also"></a>Voir aussi  

 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Vues et fonctions &#40;de gestion dynamique liées aux e/s, Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
