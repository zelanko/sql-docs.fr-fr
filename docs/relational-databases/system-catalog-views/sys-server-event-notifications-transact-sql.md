---
description: sys.server_event_notifications (Transact-SQL)
title: sys. server_event_notifications (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_event_notifications
- sys.server_event_notifications
- sys.server_event_notifications_TSQL
- server_event_notifications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_notifications catalog view
ms.assetid: 1a83a044-3130-4551-95ca-162525846ff5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c9d10906885eefeb6be66d8f353fd7a553c57288
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551418"
---
# <a name="sysserver_event_notifications-transact-sql"></a>sys.server_event_notifications (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Retourne une ligne pour chaque objet de notification d'événement au niveau du serveur.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom de la notification d'événement serveur. Unique pour toutes les notifications d'événements serveur.|  
|**object_id**|**int**|Numéro d'identification de l'objet. Est unique dans la base de données **Master** .|  
|**parent_class**|**tinyint**|Classe du parent. A toujours la valeur 100 = Serveur.|  
|**parent_class_desc**|**nvarchar(60)**|Description d'une classe de parent. A toujours la valeur SERVER.|  
|**parent_id**|**int**|A toujours la valeur 0.|  
|**create_date**|**datetime**|Date de création.|  
|**modify_date**|**datetime**|Date de la dernière modification de l'objet à l'aide d'une instruction ALTER.|  
|**service_name**|**nvarchar (256)**|Nom du service cible auquel la notification est envoyée.|  
|**broker_instance**|**nvarchar(128)**|Service Broker sur lequel le service cible nommé est défini.|  
|**creator_sid**|**varbinary(85)**|ID de sécurité de la connexion exécutant l'instruction qui crée la notification d'événement. La valeur est NULL si WITH FAN_IN n'est pas spécifié dans la définition de la notification d'événement.|  
|**principal_id**|**int**|ID du principal de serveur propriétaire.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de catalogue d’objets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
