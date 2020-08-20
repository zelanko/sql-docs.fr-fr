---
description: sys.filetable_system_defined_objects (Transact-SQL)
title: sys. filetable_system_defined_objects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7076e365989a9ceeac69ed9025f579edd8071a1f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482122"
---
# <a name="sysfiletable_system_defined_objects-transact-sql"></a>sys.filetable_system_defined_objects (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Affiche une liste des objets définis par le système en rapport avec les FileTables. Contient une ligne pour chaque objet défini par le système.  
  
 Lorsque vous créez un FileTable, les objets connexes tels que les contraintes et les index sont créés en même temps. Vous ne pouvez pas modifier ou supprimer ces objets ; ils disparaissent uniquement lorsque le FileTable lui-même est supprimé.  
  
 Pour plus d’informations sur les FileTables, consultez [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md).  
  
|Colonne|Type de données|Description|  
|------------|---------------|-----------------|  
|**object_id**|**int**|ID d'objet de l'objet défini par le système associé à un FileTable.<br /><br /> Fait référence à l’objet dans **sys. Objects**.|  
|**parent_object_id**|**int**|ID d'objet du FileTable parent.<br /><br /> Fait référence à l’objet dans **sys. Objects**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, modifier et supprimer des FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)  
  
  
