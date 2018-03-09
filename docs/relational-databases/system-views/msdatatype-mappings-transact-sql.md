---
title: MSdatatype_mappings (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdatatype_mappings
- MSdatatype_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdatatype_mappings view
ms.assetid: 13cdabb3-6e07-4e8d-ae80-4235022ccc7f
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f0acbcbf2c70b08b44e0147989fb1f9dcd3e2301
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="msdatatypemappings-transact-sql"></a>MSdatatype_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSdatatype_mappings** vue mappe les types de données SQL Server en types de données utilisées par les systèmes de gestion de base de données non SQL Server (SGBD). Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**dbms_name**|**nvarchar(128)**|Est le nom du SGBD. Vous trouverez ci-dessous les valeurs possibles et leurs descriptions.<br /><br /> **MSSQLSERVER**: la destination est une base de données SQL Server.<br />**ORACLE**: la destination est une base de données Oracle.<br />**DB2**: la destination est une base de données IBM DB2.<br />**SYBASE**: la destination est une base de données Sybase.|  
|**sql_type**|**nvarchar(128)**|Est le type de données SQL Server.|  
|**dest_type**|**nvarchar(128)**|Est le nom du type de données non SQL Server.|  
|**dest_prec**|**bigint**|Est la précision du type de données non SQL Server.|  
|**dest_create_params**|**int**|À usage interne uniquement|  
|**dest_nullable**|**bit**|Est le type de données non SQL Server prend en charge une valeur NULL.|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Spécifier des mappages de Type de données pour un serveur de publication Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Tables de réplication &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
