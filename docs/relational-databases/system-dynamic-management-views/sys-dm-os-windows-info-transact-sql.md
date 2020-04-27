---
title: sys. dm_os_windows_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_windows_info
- dm_os_windows_info_TSQL
- sys.dm_os_windows_info
- sys.dm_os_windows_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_windows_info dynamic management view
ms.assetid: adc81283-fdc2-46c0-bb48-abe82bbf2459
author: stevestein
ms.author: sstein
ms.openlocfilehash: d25713ba8fb298ce465910eae786befb710961d7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67899591"
---
# <a name="sysdm_os_windows_info-transact-sql"></a>sys.dm_os_windows_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne qui affiche les informations relatives à la version du système d'exploitation Windows.  
  
  S’applique uniquement aux SQL Server s’exécutant sur Windows. Pour voir des instructions similaires pour les SQL Server s’exécutant sur un hôte non-Windows, par exemple Linux, utilisez [sys. dm_os_host_info &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**windows_release**|**nvarchar(256)**|Pour Windows, retourne le numéro de version. Pour obtenir la liste des valeurs et des descriptions, consultez [version du système d’exploitation (Windows)](/windows/desktop/SysInfo/operating-system-version). Ne peut pas avoir la valeur NULL.|  
|**windows_service_pack_level**|**nvarchar(256)**| Pour Windows, retourne le nombre de Service Pack. Ne peut pas avoir la valeur NULL. |  
|**windows_sku**|**int**|Pour Windows, retourne l’ID de référence (SKU) Windows. Pour obtenir la liste des ID et des descriptions des références SKU, consultez [fonction GetProductInfo](https://msdn.microsoft.com/library/ms724358.aspx). Accepte la valeur null. |  
|**os_language_version**|**int**| Pour Windows, retourne l’identificateur de paramètres régionaux (LCID) Windows du système d’exploitation. Pour obtenir la liste des valeurs et des descriptions des LCID, consultez [ID de paramètres régionaux attribués par Microsoft](https://go.microsoft.com/fwlink/?LinkId=208080). Ne peut pas avoir la valeur NULL.|  
  
  
## <a name="permissions"></a>Autorisations  
L’autorisation SELECT sur sys. dm_os_windows_info est accordée au rôle public par défaut. En cas de révocation, requiert l’autorisation VIEW SERVER STATE sur le serveur.  

## <a name="limitations-and-restrictions"></a>Limitations et restrictions
Pour afficher les instructions relatives à SQL exécuté sur un hôte non-Windows, par exemple Linux, utilisez [sys. dm_os_host_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md). 
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne toutes les colonnes de la vue **sys. dm_os_windows_info** .  
  
```  
SELECT windows_release, windows_service_pack_level, windows_sku, os_language_version  
FROM sys.dm_os_windows_info;  
```  
  
 Un exemple d'ensemble de résultats est présenté ci-dessous.  
  
 `windows_release  windows_service_pack_level   windows_sku   os_language_version`  
  
 `---------------  ---------------------------  ------------  -------------------`  
  
 `6.0              Service Pack 2                4            1033`  
  
## <a name="see-also"></a>Voir aussi  
 [sys. dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)  
  
  

