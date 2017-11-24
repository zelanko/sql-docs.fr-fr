---
title: Sys.identity_columns (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- identity_columns
- sys.identity_columns
- sys.identity_columns_TSQL
- identity_columns_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.identity_columns catalog view
ms.assetid: 97ee01e6-9c9e-4fd9-884b-68b4084669d5
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2669f1373bedec1256d3071b9fe1f85b7c8dab8f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysidentitycolumns-transact-sql"></a>sys.identity_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne par colonne d'identité.  
  
 Le **sys.identity_columns** vue hérite des lignes de la **sys.columns** vue. Le **sys.identity_columns** vue retourne les colonnes dans le **sys.columns** affichage, ainsi que les **seed_value**, **increment_value**, **last_value**, et **is_not_for_replication** colonnes. Pour plus d’informations, consultez [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md).  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**\<colonnes héritent de sys.columns >**||Le **sys.identity_columns** vue retourne toutes les colonnes de la **sys.columns** vue. Elle retourne également les colonnes supplémentaires décrites ci-après. Pour obtenir une description des colonnes qui le **sys.identity_columns** hérite **sys.columns**, consultez [sys.columns &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).|  
|**seed_value**|**sql_variant**|Valeur de départ de cette colonne d'identité. Le type de données de la valeur de départ est le même que celui de la colonne proprement dite.|  
|**increment_value**|**sql_variant**|Valeur d'incrément de cette colonne d'identité. Le type de données de la valeur de départ est le même que celui de la colonne proprement dite.|  
|**LAST_VALUE**|**sql_variant**|Dernière valeur générée pour cette colonne d'identité. Le type de données de la valeur de départ est le même que celui de la colonne proprement dite.|  
|**is_not_for_replication**|**bit**|La colonne d'identité est déclarée NOT FOR REPLICATION.|  
  
> [!NOTE]  
>  Pour créer un numéro à incrémentation automatique qui peut être utilisé dans plusieurs tables ou être appelé par des applications sans faire référence à une table, consultez [Numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
