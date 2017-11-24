---
title: Sys.Periods (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 25e66ed3-2270-4c5c-9f5a-2c0f165a57ca
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 58e8428bc016975594105b842c75fca1304d0695
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysperiods-transact-sql"></a>Sys.Periods (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque table pour laquelle les périodes ont été définies.  
  
|En-tête de colonne|Type de données| Description|  
|-------------------|---------------|-----------------|  
|period_type|**sysname**|Nom de la période|  
|period_type_desc|**tinyint**|La valeur numérique qui représente le type de période :<br /><br /> 1 = période de temps système|  
|object_id|**nvarchar (60)**|La description textuelle du type de colonne :<br /><br /> SYSTEM_TIME_PERIOD|  
|object_id|**int**|L’id de la table contenant la colonne period_type|  
|start_column_id|**int**|L’id de la colonne qui définit la limite inférieure de période|  
|end_column_id|**int**|L’id de la colonne qui définit la limite supérieure de période|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues système &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Sys.all_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [Sys.system_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)   
 [Interrogation des catalogues système SQL Server FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Tables temporelles](../../relational-databases/tables/temporal-tables.md)  
  
  
