---
title: Sys.identity_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- identity_columns
- sys.identity_columns
- sys.identity_columns_TSQL
- identity_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.identity_columns catalog view
ms.assetid: 97ee01e6-9c9e-4fd9-884b-68b4084669d5
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6d6c97b167cb69eec72ad771504a1070ed59e4f1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47709597"
---
# <a name="sysidentitycolumns-transact-sql"></a>sys.identity_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne par colonne d'identité.  
  
 Le **sys.identity_columns** vue hérite des lignes de la **sys.columns** vue. Le **sys.identity_columns** vue retourne les colonnes dans le **sys.columns** vue, ainsi que les **seed_value**, **increment_value**, **last_value**, et **is_not_for_replication** colonnes. Pour plus d’informations, consultez [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**\<colonnes héritent de sys.columns >**||Le **sys.identity_columns** vue retourne toutes les colonnes dans le **sys.columns** vue. Elle retourne également les colonnes supplémentaires décrites ci-après. Pour obtenir une description des colonnes qui les **sys.identity_columns** hérite **sys.columns**, consultez [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).|  
|**seed_value**|**sql_variant**|Valeur de départ de cette colonne d'identité. Le type de données de la valeur de départ est le même que celui de la colonne proprement dite.|  
|**increment_value**|**sql_variant**|Valeur d'incrément de cette colonne d'identité. Le type de données de la valeur de départ est le même que celui de la colonne proprement dite.|  
|**LAST_VALUE**|**sql_variant**|Dernière valeur générée pour cette colonne d'identité. Le type de données de la valeur de départ est le même que celui de la colonne proprement dite.|  
|**is_not_for_replication**|**bit**|La colonne d'identité est déclarée NOT FOR REPLICATION.|  
  
> [!NOTE]  
>  Pour créer un numéro à incrémentation automatique qui peut être utilisé dans plusieurs tables ou être appelé par des applications sans faire référence à une table, consultez [Numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
