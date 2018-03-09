---
title: Sys.FileGroups (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/24/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.filegroups_TSQL
- filegroups
- sys.filegroups
- filegroups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filegroups catalog view
ms.assetid: 9e851f72-1f8e-4515-a25d-152ebc12ed56
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 91198ea3ed94496ff116014e0df2b1b067e4bf16
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysfilegroups-transact-sql"></a>sys.filegroups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne pour chaque espace de données représentant un groupe de fichiers.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**\<héritée de colonnes >**|--|Pour obtenir la liste des colonnes qui hérite de cette vue, consultez [sys.data_spaces &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md).|  
|**filegroup_guid**|**uniqueidentifier**|GUID du groupe de fichiers.<br /><br /> NULL = groupe de fichiers PRIMARY|  
|**log_filegroup_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la valeur est NULL.|  
|**is_read_only**|**bit**|1 = Le groupe de fichiers est en lecture seule.<br /><br /> 1 = le groupe de fichiers est accessible en lecture/écriture.|  
|**is_autogrow_all_files**|**bit**|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> 1 = lorsqu’un fichier dans le satisfait aux fichiers que le seuil de croissance automatique, tous les fichiers dans le groupe de fichiers augmente.<br /><br /> 0 = lorsqu’un fichier dans le satisfait aux groupe de fichiers que le seuil de croissance automatique, seul ce fichier se développe. Il s'agit du paramètre par défaut.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Espaces de données &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)  
  
  
