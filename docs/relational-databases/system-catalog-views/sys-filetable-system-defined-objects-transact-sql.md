---
title: Sys.filetable_system_defined_objects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.filetable_system_defined_objects_TSQL
- filetable_system_defined_objects
- filetable_system_defined_objects_TSQL
- sys.filetable_system_defined_objects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filetable_system_defined_objects catalog view
ms.assetid: 62022e6b-46f6-495f-b14b-53f41e040361
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 118646e7d12940291c0f4f6a79744495e596cf36
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031091"
---
# <a name="sysfiletablesystemdefinedobjects-transact-sql"></a>sys.filetable_system_defined_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche une liste des objets définis par le système en rapport avec les FileTables. Contient une ligne pour chaque objet défini par le système.  
  
 Lorsque vous créez un FileTable, les objets connexes tels que les contraintes et les index sont créés en même temps. Vous ne pouvez pas modifier ou supprimer ces objets ; ils disparaissent uniquement lorsque le FileTable lui-même est supprimé.  
  
 Pour plus d’informations sur les FileTables, consultez [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md).  
  
|colonne|Data type|Description|  
|------------|---------------|-----------------|  
|**object_id**|**Int**|ID d'objet de l'objet défini par le système associé à un FileTable.<br /><br /> Fait référence à l’objet dans **sys.objects**.|  
|**parent_object_id**|**Int**|ID d'objet du FileTable parent.<br /><br /> Fait référence à l’objet dans **sys.objects**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, modifier et supprimer des FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)  
  
  
