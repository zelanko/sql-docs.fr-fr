---
title: sys.fulltext_document_types (Transact-SQL) | Microsoft Docs
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
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c11c21844b0709cf795375c4b8d17ee43847d06f
ms.sourcegitcommit: 04c031f7411aa33e2174be11dfced7feca8fbcda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2019
ms.locfileid: "64945594"
---
# <a name="sysfulltextdocumenttypes-transact-sql"></a>sys.fulltext_document_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque type de document qui est disponible pour des opérations d'indexation de texte intégral. Chaque ligne représente l'interface IFilter inscrite dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**document_type**|**sysname**|Extension de fichier du type de document pris en charge.<br /><br /> Cette valeur peut être utilisée pour identifier le filtre qui sera utilisé lors de l’indexation de texte intégral des colonnes de type **varbinary (max)** ou **image**.|  
|**class_id**|**uniqueidentifier**|GUID de la classe IFilter qui prend en charge l'extension de fichier.|  
|**path**|**nvarchar(260)**|Chemin d'accès de la DLL IFilter. Le chemin d'accès n'est visible que pour les membres du rôle de serveur fixe **serveradmin** .|  
|**version**|**sysname**|Version de la DLL IFilter.|  
|**manufacturer**|**sysname**|Nom du fabricant de IFilter.<br /><br /> Remarque : Seuls les documents avec le constructeur en tant que [!INCLUDE[msCoName](../../includes/msconame-md.md)] sont pris en charge sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vues catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
