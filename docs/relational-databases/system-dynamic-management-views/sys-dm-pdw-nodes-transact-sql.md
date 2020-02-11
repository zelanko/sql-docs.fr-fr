---
title: sys. dm_pdw_nodes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 93966909-d758-4d50-950b-f5066d104fa6
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 61593522e09ed86ec10f08a6ad8ff7a941a2e10e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899344"
---
# <a name="sysdm_pdw_nodes-transact-sql"></a>sys. dm_pdw_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contient des informations sur tous les nœuds [!INCLUDE[ssAPS](../../includes/ssaps-md.md)]dans. Elle répertorie une ligne par nœud dans l’appliance.  
  
|Nom de la colonne|Type de données|Description|Plage|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|ID numérique unique associé au nœud.<br /><br /> Clé pour cette vue.|Unique sur l’ensemble de l’appliance, quel que soit le type.|  
|type|**nvarchar (32)**|Type du nœud.|« COMPUTE », « CONTROL », « MANAGEMENT »|  
|name|**nvarchar (32)**|Nom logique du nœud.|Toute chaîne de longueur appropriée.|  
|address|**nvarchar (32)**|Adresse IP de ce nœud.|Au format [0-255]. [0-255]. [0-255]. [0-255].|  
|is_passive|**int**|Indique si l’ordinateur virtuel qui exécute le nœud est en cours d’exécution sur le serveur affecté ou s’il a basculé sur le serveur de réserve.|0-le nœud de la machine virtuelle est en cours d’exécution sur le serveur d’origine.<br /><br /> 1-le nœud de la machine virtuelle est en cours d’exécution sur le serveur de réserve.|  
|region|**nvarchar (32)**|Région dans laquelle le nœud est en cours d’exécution.|« PDW », « HDINSIGHT »|  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Data Warehouse et les vues de gestion dynamique Data Warehouse parallèles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
