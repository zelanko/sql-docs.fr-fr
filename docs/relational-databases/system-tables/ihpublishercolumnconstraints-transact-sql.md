---
title: IHpublishercolumnconstraints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumnconstraints
- IHpublishercolumnconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumnconstraints system table
ms.assetid: d7a41da6-e067-430a-8da2-3f6745b8a4f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 58ef9c5e68e7d209262ebf43891ba5c1bcc4174f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67990287"
---
# <a name="ihpublishercolumnconstraints-transact-sql"></a>IHpublishercolumnconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table système **IHpublishercolumnconstraints** mappe les colonnes d’une publication non SQL Server dans la table système [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) aux contraintes de la table système [IHpublisherconstraints](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) . Cette table est stockée dans la base de données de distribution.  
  
## <a name="definition"></a>Définition  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Identifie la colonne de [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) avec une contrainte associée.|  
|**publisherconstraint_id**|**int**|Identifie une contrainte de [IHpublisherconstraints](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) associée à la colonne.|  
|**indid**|**int**|Indique la position de la colonne dans la table publiée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de bases de données hétérogènes](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
