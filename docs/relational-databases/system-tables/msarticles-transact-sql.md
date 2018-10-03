---
title: MSarticles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSarticles
- MSarticles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSarticles system table
ms.assetid: 1acd79a5-b3e2-4161-9592-7acc2a41ba38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: de2edcb376cbd58b4186fb7e2dd55c16953a48ad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47829617"
---
# <a name="msarticles-transact-sql"></a>MSarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSarticles** table contient une ligne pour chaque article répliqué par un éditeur. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|L’ID du serveur de publication.|  
|**publisher_db**|**sysname**|Nom de la base de données du serveur de publication.|  
|**publication_id**|**Int**|ID de la publication.|  
|**article**|**sysname**|Le nom de l’article.|  
|**article_id**|**Int**|L’ID de l’article.|  
|**destination_object**|**sysname**|Nom de la table créée sur l'Abonné.|  
|**source_owner**|**sysname**|Nom du schéma de la table source hébergée sur le serveur de publication.|  
|**source_object**|**sysname**|Nom de l'objet source à partir duquel ajouter l'article.|  
|**description**|**nvarchar(255)**|Description de l'article.|  
|**destination_owner**|**sysname**|Nom du schéma de la table créée sur l'Abonné.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
