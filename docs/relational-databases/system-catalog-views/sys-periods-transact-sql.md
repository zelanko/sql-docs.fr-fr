---
description: sys. periods (Transact-SQL)
title: sys. periods (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 25e66ed3-2270-4c5c-9f5a-2c0f165a57ca
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c091649234826080054de942ed96272055a1b595
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810316"
---
# <a name="sysperiods-transact-sql"></a>sys. periods (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Retourne une ligne pour chaque table pour laquelle des périodes ont été définies.  
  
|En-tête de colonne|Type de données|Description|  
|-------------------|---------------|-----------------|  
|name|**sysname**|Nom de la période|  
|period_type|**tinyint**|Valeur numérique représentant le type de période :<br /><br /> 1 = période système|  
|period_type_desc|**nvarchar(60)**|Description textuelle du type de colonne :<br /><br /> SYSTEM_TIME_PERIOD|  
|object_id|**int**|ID de la table contenant la colonne period_type|  
|start_column_id|**int**|ID de la colonne qui définit la limite inférieure de la période|  
|end_column_id|**int**|ID de la colonne qui définit la limite supérieure de la période|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues système &#40;&#41;Transact-SQL ](../../t-sql/language-reference.md)   
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)   
 [Interrogation du SQL Server FAQ du catalogue système](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Tables temporelles](../../relational-databases/tables/temporal-tables.md)  
  
