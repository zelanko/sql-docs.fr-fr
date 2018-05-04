---
title: IHpublishercolumnindexes (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- IHpublishercolumnindexes
- IHpublishercolumnindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumnindexes system table
ms.assetid: 95b95a1d-b502-4838-825f-82a456487e25
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2e2b004dc0d1ac792ae07ae450267f94f10ab74a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ihpublishercolumnindexes-transact-sql"></a>IHpublishercolumnindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **IHpublishercolumnindexes** (table système) mappe les colonnes d’une publication non SQL Server dans le [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) (table système) avec les index de la [IHpublisherindexes](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md) (table système). Cette table est stockée dans la base de données de distribution.  
  
## <a name="definition"></a>Définition  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Identifie la colonne de [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) avec un index associé.|  
|**publisherindex_id**|**int**|Identifie un index de la [IHpublisherindexes](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md) table associée à la colonne.|  
|**indid**|**int**|Indique la position de la colonne dans la table publiée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
