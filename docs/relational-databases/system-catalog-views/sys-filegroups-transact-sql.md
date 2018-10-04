---
title: Sys.FileGroups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: beda60ee7178bee59705a6450351a87e931aa2cb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696397"
---
# <a name="sysfilegroups-transact-sql"></a>sys.filegroups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne pour chaque espace de données représentant un groupe de fichiers.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**\<héritée de colonnes >**|--|Pour obtenir la liste des colonnes qui hérite de cette vue, consultez [sys.data_spaces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md).|  
|**filegroup_guid**|**uniqueidentifier**|GUID du groupe de fichiers.<br /><br /> NULL = groupe de fichiers PRIMARY|  
|**log_filegroup_id**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la valeur est NULL.|  
|**is_read_only**|**bit**|1 = Le groupe de fichiers est en lecture seule.<br /><br /> 1 = le groupe de fichiers est accessible en lecture/écriture.|  
|**is_autogrow_all_files**|**bit**|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> 1 = quand un fichier dans le répond de groupe de fichiers à augmenter le seuil de croissance automatique, tous les fichiers dans le groupe de fichiers.<br /><br /> 0 = quand un fichier dans le satisfait de groupe de fichiers augmente le seuil de croissance automatique, seul ce fichier. Il s'agit du paramètre par défaut.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Espaces de données &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)  
  
  
