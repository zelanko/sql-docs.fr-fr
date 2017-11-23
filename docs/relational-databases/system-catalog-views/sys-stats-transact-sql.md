---
title: Sys.stats (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- sys.stats
- stats_TSQL
- sys.stats_TSQL
- stats
dev_langs: TSQL
helpviewer_keywords: sys.stats catalog view
ms.assetid: 42605c80-126f-460a-befb-a0b7482fae6a
caps.latest.revision: "41"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ba477c2bc30fdeccee1af448e953043f3c5d9d92
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sysstats-transact-sql"></a>sys.stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contient une ligne pour chaque objet de statistiques qui existe pour les tables, index et vues indexées de la base de données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Chaque index aura une ligne de statistiques correspondante avec le même nom et le même ID (**index_id** = **stats_id**), mais pas chaque ligne de statistiques a un index correspondant.  
  
 La vue de catalogue [sys.stats_columns](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md) fournit des informations statistiques pour chaque colonne dans la base de données. Pour plus d’informations sur les statistiques, consultez [statistiques](../../relational-databases/statistics/statistics.md).  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID de l'objet auquel ces statistiques appartiennent.|  
|**nom**|**sysname**|Nom des statistiques. Unique dans l'objet.|  
|**stats_id**|**int**|ID des statistiques. Unique dans l'objet.|  
|**auto_created**|**bit**|Indique si les statistiques ont été créées automatiquement par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 0 = Les statistiques n'ont pas été créées automatiquement par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 = Les statistiques ont été créées automatiquement par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**user_created**|**bit**|Indique si les statistiques ont été créées par un utilisateur.<br /><br /> 0 = Les statistiques n'ont pas été créées par un utilisateur.<br /><br /> 1 = Les statistiques ont été créées par un utilisateur.|  
|**no_recompute**|**bit**|Indique si les statistiques ont été créées avec la **NORECOMPUTE** option.<br /><br /> 0 = les statistiques n’ont pas été créés avec le **NORECOMPUTE** option.<br /><br /> 1 = les statistiques ont été créées avec la **NORECOMPUTE** option.|  
|**has_filter**|**bit**|0 = Les statistiques n'ont pas de filtre et sont calculées sur toutes les lignes.<br /><br /> 1 = Les statistiques ont un filtre et sont calculées uniquement sur les lignes qui satisfont la définition de filtre.|  
|**filter_definition**|**nvarchar(max)**|Expression pour le sous-ensemble de lignes inclus dans les statistiques filtrées.<br /><br /> NULL = Statistiques non filtrées.|  
|**is_temporary**|**bit**|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Indiquez si les statistiques sont temporaires. Les statistiques temporaires prennent en charge les bases de données secondaires [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] qui sont activés pour un accès en lecture seule.<br /><br /> 0 = Les statistiques ne sont pas temporaires.<br /><br /> 1 = Les statistiques sont temporaires.|  
|**is_incremental**|**bit**|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Indiquez si les statistiques sont créées comme statistiques incrémentielles.<br /><br /> 0 = Les statistiques ne sont pas incrémentielles.<br /><br /> 1 = Les statistiques sont incrémentielles.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants retournent toutes les statistiques et les colonnes de statistiques de la table `HumanResources.Employee`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT s.name AS statistics_name  
      ,c.name AS column_name  
      ,sc.stats_column_id  
FROM sys.stats AS s  
INNER JOIN sys.stats_columns AS sc   
    ON s.object_id = sc.object_id AND s.stats_id = sc.stats_id  
INNER JOIN sys.columns AS c   
    ON sc.object_id = c.object_id AND c.column_id = sc.column_id  
WHERE s.object_id = OBJECT_ID('HumanResources.Employee');  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
