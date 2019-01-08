---
title: MSdatatype_mappings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdatatype_mappings
- MSdatatype_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdatatype_mappings view
ms.assetid: 13cdabb3-6e07-4e8d-ae80-4235022ccc7f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5af1233e81c996e98287a637e01ad1d249671303
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52785091"
---
# <a name="msdatatypemappings-transact-sql"></a>MSdatatype_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSdatatype_mappings** vue mappe les types de données SQL Server pour les types de données utilisés par les systèmes de gestion de base de données non SQL Server (SGBD). Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**dbms_name**|**nvarchar(128)**|Est le nom du SGBD. Voici les valeurs possibles et leurs descriptions.<br /><br /> **MSSQLSERVER**: La destination est une base de données SQL Server.<br />**ORACLE**: Base de données Oracle de destination.<br />**DB2**: Base de données IBM DB2 de destination.<br />**SYBASE**: Base de données Sybase de destination.|  
|**sql_type**|**nvarchar(128)**|Est le type de données SQL Server.|  
|**dest_type**|**nvarchar(128)**|Est le nom du type de données non SQL Server.|  
|**dest_prec**|**bigint**|Est la précision du type de données non SQL Server.|  
|**dest_create_params**|**Int**|À usage interne uniquement|  
|**dest_nullable**|**bit**|Est si le type de données non SQL Server prend en charge une valeur NULL.|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Spécifier des mappages de types de données pour un serveur de publication Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
