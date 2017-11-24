---
title: Sys.event_notifications (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- event_notifications_TSQL
- event_notifications
- sys.event_notifications_TSQL
- sys.event_notifications
dev_langs: TSQL
helpviewer_keywords: sys.event_notifications catalog view
ms.assetid: 136a76ee-2b35-4418-ab46-fda2d51f7d99
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ef927e091f15027d8e2fd965cc50955adf7092d1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="syseventnotifications-transact-sql"></a>sys.event_notifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque objet qui est une notification d’événement avec **sys.objects.type** = fr.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom de la notification d'événement|  
|**object_id**|**int**|Numéro d'identification de l'objet. Unique dans une base de données.|  
|**parent_class**|**tinyint**|Classe du parent.<br /><br /> 0 = Base de données<br /><br /> 1 = objet ou colonne|  
|**parent_class_desc**|**nvarchar (60)**|DATABASE<br /><br /> OBJECT_OR_COLUMN|  
|**parent_id**|**int**|ID non NULL de l'objet parent<br /><br /> 0 = La classe parent est la base de données.|  
|**create_date**|**datetime**|Date de création.|  
|**modify_date**|**datetime**|Est toujours égal à **create_date**.|  
|**SERVICE_NAME**|**nvarchar (256)**|Nom du service cible auquel la notification est envoyée.|  
|**BROKER_INSTANCE**|**nvarchar (128)**|Instance du broker auquel la notification est envoyée.|  
|**principal_id**|**int**|ID du principal de base de données propriétaire de cette notification d'événement|  
|**creator_sid**|**varbinary(85)**|SID de la connexion qui a créé la notification d'événement.<br /><br /> A la valeur NULL si l'option FAN_IN n'est pas spécifiée.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’objets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
