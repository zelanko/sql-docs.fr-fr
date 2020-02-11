---
title: IHpublisherconstraints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublisherconstraints
- IHpublisherconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublisherconstraints system table
ms.assetid: 537b1e1a-7228-4680-aa27-5ad7072ea01e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 44987e1b610483e6ce3cbca26c1efb8a1ef4c241
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990254"
---
# <a name="ihpublisherconstraints-transact-sql"></a>IHpublisherconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table système **IHpublisherconstraints** contient une ligne pour chaque contrainte répliquée à partir d’éditeurs non-SQL Server à l’aide du serveur de distribution actuel. Cette table est stockée dans la base de données de distribution.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisherconstraint_id**|**int**|Identifie une contrainte publiée.|  
|**table_id**|**int**|Identifie la table de [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) à laquelle la contrainte appartient.|  
|**publisher_id**|**smallint**|Identifie le serveur de publication non SQL Server à partir duquel la colonne est publiée.|  
|**Nom**|**Sa**|Nom de la contrainte publiée.|  
|**Type**|**nvarchar(255)**|Type de contrainte pris en charge à partir de la table système [IHconstrainttypes](../../relational-databases/system-tables/ihconstrainttypes-transact-sql.md) .|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
