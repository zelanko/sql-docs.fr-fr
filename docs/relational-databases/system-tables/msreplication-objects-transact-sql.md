---
description: MSreplication_objects (Transact-SQL)
title: MSreplication_objects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_objects
- MSreplication_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_objects system table
ms.assetid: 08f9710d-976d-448e-bead-ac9835e87bc5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d3c582b495702a46c51519f56dee1e977980840f
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538259"
---
# <a name="msreplication_objects-transact-sql"></a>MSreplication_objects (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La table **MSreplication_objects** contient une ligne pour chaque objet associé à la réplication dans la base de données de l’abonné. Cette table est stockée dans la base de données d’abonnement.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Nom du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données du serveur de publication.|  
|**édition**|**sysname**|Nom de la publication.|  
|**object_name**|**sysname**|Nom de l'objet.|  
|**object_type**|**char(2)**|Le type d’objet :<br /><br /> **u** = table.<br /><br /> **t** = déclencheur.<br /><br /> **p** = procédure stockée.|  
|**article**|**sysname**|Nom de l'article auquel l'objet est associé|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
