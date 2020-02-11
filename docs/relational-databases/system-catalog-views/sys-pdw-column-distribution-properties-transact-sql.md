---
title: sys. pdw_column_distribution_properties (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 46b74f99-2e22-4dbd-872a-533fce0e239c
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 5b71df1a25a9cd8480f23dc104792ad8f3e70f35
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401695"
---
# <a name="syspdw_column_distribution_properties-transact-sql"></a>sys. pdw_column_distribution_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient les informations de distribution pour les colonnes.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|ID de l’objet auquel la colonne appartient.||  
|**column_id**|**int**|Identificateur de la colonne.||  
|**distribution_ordinal**|**tinyint**|Ordinal (de base 1) au sein d’un ensemble de distribution.|0 = n’est pas une colonne de distribution. 1 = [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] utilise cette colonne pour distribuer la table parente.|  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue de la SQL Data Warehouse et des Data Warehouse parallèles](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
