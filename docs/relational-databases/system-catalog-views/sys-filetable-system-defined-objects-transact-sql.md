---
title: Sys.filetable_system_defined_objects (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3bd6bd8368525c94ce0d999af921c76c2cade96
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysfiletablesystemdefinedobjects-transact-sql"></a>sys.filetable_system_defined_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche une liste des objets définis par le système en rapport avec les FileTables. Contient une ligne pour chaque objet défini par le système.  
  
 Lorsque vous créez un FileTable, les objets connexes tels que les contraintes et les index sont créés en même temps. Vous ne pouvez pas modifier ou supprimer ces objets ; ils disparaissent uniquement lorsque le FileTable lui-même est supprimé.  
  
 Pour plus d’informations sur les FileTables, consultez [FileTables &#40; SQL Server &#41; ](../../relational-databases/blob/filetables-sql-server.md).  
  
|Colonne|Data type| Description|  
|------------|---------------|-----------------|  
|**object_id**|**int**|ID d'objet de l'objet défini par le système associé à un FileTable.<br /><br /> Fait référence à l’objet dans **sys.objects**.|  
|**parent_object_id**|**int**|ID d'objet du FileTable parent.<br /><br /> Fait référence à l’objet dans **sys.objects**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, modifier et supprimer des FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)  
  
  
