---
title: IHpublisherindexes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublisherindexes
- IHpublisherindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublisherindexes system table
ms.assetid: 6008ef89-eeb9-46dc-93a2-f7623298cf0f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a24126ef3226878b4d07a056573f3b60e94495c3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802511"
---
# <a name="ihpublisherindexes-transact-sql"></a>IHpublisherindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **IHpublisherindexes** (table système) contient une ligne pour chaque index répliqué à partir de non - éditeurs SQL Server à l’aide du serveur de distribution en cours. Cette table est stockée dans la base de données de distribution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisherindex_id**|**Int**|Identifie un index publié.|  
|**table_id**|**Int**|Identifie la table de [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) auquel appartient l’index.|  
|**publisher_id**|**smallint**|Identifie le serveur de publication non-SQL à partir de laquelle l’index est publié.|  
|**nom**|**sysname**|Nom de l'index publié.|  
|**type**|**nvarchar(255)**|Un type d’index pris en charge à partir de la [IHindextypes](../../relational-databases/system-tables/ihindextypes-transact-sql.md) (table système).|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
