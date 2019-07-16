---
title: MSdbms_datatype_mapping (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdbms_datatype_mapping_TSQL
- MSdbms_datatype_mapping
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype_mapping system table
ms.assetid: 13289a0b-dfb0-4771-ad80-4c5f83cded99
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9a1042bb3aa7b6113121693cc66440ebbf81ce1b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67907543"
---
# <a name="msdbmsdatatypemapping-transact-sql"></a>MSdbms_datatype_mapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSdbms_datatype_mapping** table contient les mappages de types de données autorisée à partir du type de données dans le système de gestion de base de données (SGBD) source à un ou plusieurs types de données spécifiques dans le SGBD de destination. Cette table est stockée dans le **msdb** de base de données et est utilisé pour la réplication de bases de données hétérogènes.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**datatype_mapping_id**|**int**|Identifie chaque mappage de type de données unique.|  
|**map_id**|**Int**|Identifie le type de données source.|  
|**dest_datatype_id**|**Int**|Identifie le type de données de destination.|  
|**dest_precision**|**bigint**|Définit la précision du type de données de destination, où une valeur NULL signifie que la précision n’est pas utilisée, et la valeur de **-1** signifie que la précision du type de données source est utilisée.|  
|**dest_scale**|**int**|Définit l’échelle du type de données de destination, où une valeur NULL signifie que la mise à l’échelle n’est pas utilisé, et la valeur de **-1** signifie que la mise à l’échelle du type de données source est utilisé.|  
|**dest_length**|**bigint**|Définit la longueur du type de données de destination, où une valeur NULL signifie que la longueur n’est pas utilisée, et la valeur de **-1** signifie que la longueur du type de données source est utilisée.|  
|**dest_nullable**|**bit**|Indique si la colonne de destination dans le mappage autorise les valeurs NULL, où une valeur NULL signifie que cette définition n'est pas requise.|  
|**dest_createparams**|**int**|Bitmap décrivant la combinaison de longueur, précision et échelle applicable à chaque type de données, qui inclut :<br /><br /> **0 x 1** = précision.<br /><br /> **0 x 2** = mise à l’échelle.<br /><br /> **0 x 4** = longueur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Spécifier des mappages de types de données pour un serveur de publication Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
