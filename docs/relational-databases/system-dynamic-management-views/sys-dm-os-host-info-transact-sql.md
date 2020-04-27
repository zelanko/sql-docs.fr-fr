---
title: sys. dm_os_host_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/10/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_os_host_info
- sys.dm_os_host_info_TSQL
- dm_os_host_info
- dm_os_host_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_host_info dynamic management view
ms.assetid: 9bb6ef86-957b-4ca1-ad20-ca2f8460a86d
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 052402d3a394e8da3e08828992127d3cd89b95ea
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67900165"
---
# <a name="sysdm_os_host_info-transact-sql"></a>sys. dm_os_host_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Retourne une ligne qui affiche les informations sur la version du système d’exploitation.  
  
|Nom de la colonne |Type de données |Description |  
|-----------------|---------------|-----------------|  
|**host_platform** |**nvarchar(256)** |Type de système d’exploitation : Windows ou Linux |
|**host_distribution** |**nvarchar(256)** |Description du système d’exploitation. |
|**host_release**|**nvarchar(256)**|Version du système d'exploitation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows (numéro de version). Pour obtenir la liste des valeurs et des descriptions, consultez [version du système d’exploitation (Windows)](/windows/desktop/SysInfo/operating-system-version). <br> Pour Linux, retourne une chaîne vide. |  
|**host_service_pack_level**|**nvarchar(256)**|Niveau du Service Pack du système d'exploitation Windows. <br> Pour Linux, retourne une chaîne vide. |  
|**host_sku**|**int**|ID de référence (SKU) Windows. Pour obtenir la liste des ID et des descriptions des références SKU, consultez [fonction GetProductInfo](https://msdn.microsoft.com/library/ms724358.aspx). Autorise la valeur NULL. <br> Pour Linux, retourne la valeur NULL. |  
|**os_language_version**|**int**|Identificateur des paramètres régionaux (LCID) du système d'exploitation. Pour obtenir la liste des valeurs et des descriptions des LCID, consultez [ID de paramètres régionaux attribués par Microsoft](https://go.microsoft.com/fwlink/?LinkId=208080). Ne peut pas avoir la valeur null.|  

## <a name="remarks"></a>Notes  
Cette vue est similaire à [sys. dm_os_windows_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md), qui ajoute des colonnes pour différencier Windows et Linux.
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
L' `SELECT` autorisation sur `sys.dm_os_host_info` est accordée par défaut `public` au rôle. En cas de révocation `VIEW SERVER STATE` , nécessite l’autorisation sur le serveur.   
 
> [!CAUTION]
>  Depuis la version [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1,3, [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] la version 17 `SELECT` requiert une `sys.dm_os_host_info` autorisation pour se connecter à [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Si `SELECT` l’autorisation est révoquée `public`de, seules les connexions `VIEW SERVER STATE` avec l’autorisation peuvent se connecter à la version la plus récente de SSMS. (D’autres outils, tels `sqlcmd.exe` que, peuvent `SELECT` se connecter `sys.dm_os_host_info`sans autorisation sur.)

  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne toutes les colonnes de la vue **sys. dm_os_host_info** .  
  
```  
SELECT host_platform, host_distribution, host_release, 
    host_service_pack_level, host_sku, os_language_version  
FROM sys.dm_os_host_info;  
```  

Voici un exemple de jeu de résultats sur Windows :
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Windows   |Windows Server 2012 R2 Standard    |6.3    |   |7  |1033 |  

Voici un exemple de jeu de résultats sur Linux :
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Linux |Ubuntu |16.04  |   |NULL   |1033 |  

  
## <a name="see-also"></a>Voir aussi  
 [sys. dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_windows_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)  
 

