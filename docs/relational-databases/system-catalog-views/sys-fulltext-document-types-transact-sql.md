---
title: sys. fulltext_document_types (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_document_types_TSQL
- fulltext_document_types
- fulltext_document_types_TSQL
- sys.fulltext_document_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_document_types catalog view
ms.assetid: 156fcfa4-7304-4a5c-b96f-1c3e061e5df0
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 454b1460b0f1db0da7298e640b7b4cf081bb90b3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85790538"
---
# <a name="sysfulltext_document_types-transact-sql"></a>sys.fulltext_document_types (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Retourne une ligne pour chaque type de document qui est disponible pour des opérations d'indexation de texte intégral. Chaque ligne représente l'interface IFilter inscrite dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**document_type**|**sysname**|Extension de fichier du type de document pris en charge.<br /><br /> Cette valeur peut être utilisée pour identifier le filtre qui sera utilisé pendant l’indexation de texte intégral des colonnes de type **varbinary (max)** ou **image**.|  
|**class_id**|**uniqueidentifier**|GUID de la classe IFilter qui prend en charge l'extension de fichier.|  
|**path**|**nvarchar(260)**|Chemin d'accès de la DLL IFilter. Le chemin d'accès n'est visible que pour les membres du rôle de serveur fixe **serveradmin** .|  
|**version**|**sysname**|Version de la DLL IFilter.|  
|**fécule**|**sysname**|Nom du fabricant de IFilter.<br /><br /> Remarque : seuls les documents avec le fabricant [!INCLUDE[msCoName](../../includes/msconame-md.md)] sont pris en charge sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
