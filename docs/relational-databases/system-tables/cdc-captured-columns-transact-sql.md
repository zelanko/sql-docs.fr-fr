---
title: CDC.captured_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.captured_columns
- cdc.captured_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.captured_columns
ms.assetid: 7bb4d408-d764-4ef6-802c-f271c8d39c2a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fb9bc8d8fe92a53eace426080221c224e229a80b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620037"
---
# <a name="cdccapturedcolumns-transact-sql"></a>cdc.captured_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque colonne suivie dans une instance de capture. Par défaut, toutes les colonnes de la table source sont capturées. Toutefois, les colonnes peuvent être incluses ou exclues lorsque la table source est activée pour la capture des données modifiées en spécifiant une liste de colonnes. Pour plus d’informations, consultez [sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
 Il est recommandé que vous **pas directement interroger les tables système**. À la place, exécutez le [sys.sp_cdc_get_source_columns](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md) procédure stockée.  
   
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**Int**|Identificateur de la table source à laquelle appartient la colonne capturée.|  
|**column_name**|**sysname**|Nom de la colonne capturée.|  
|**column_id**|**Int**|ID de la colonne capturée dans la table source.|  
|**COLUMN_TYPE**|**sysname**|Type de la colonne capturée.|  
|**column_ordinal**|**Int**|Ordinal de colonne (de base 1) dans la table de modifications. Les colonnes de métadonnées dans la table de modifications sont exclues. L'ordinal 1 est assigné à la première colonne capturée.|  
|**is_computed**|**bit**|Indique que la colonne capturée est une colonne calculée dans la table source.|  
  
## <a name="see-also"></a>Voir aussi  
 [CDC.change_tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
  
  
