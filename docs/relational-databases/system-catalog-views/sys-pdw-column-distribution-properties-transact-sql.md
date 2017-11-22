---
title: Sys.pdw_column_distribution_properties (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 46b74f99-2e22-4dbd-872a-533fce0e239c
caps.latest.revision: "5"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 046b54a2eaa2f75cbba06802cf49c10c5025945a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwcolumndistributionproperties-transact-sql"></a>Sys.pdw_column_distribution_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations de distribution pour les colonnes.  
  
|Nom de la colonne|Type de données| Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|ID de l’objet auquel appartient la colonne.||  
|**column_id**|**int**|ID de la colonne.||  
|**distribution_ordinal**|**tinyint**|Ordinal (base 1) au sein de l’ensemble de la distribution.|0 = n’est pas une colonne de distribution. 1 = [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] est à l’aide de cette colonne pour distribuer la table parente.|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrepôt de données SQL et les vues de catalogue de l’entrepôt de données en parallèle](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
