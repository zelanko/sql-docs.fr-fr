---
title: Sys.messages (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- messages_TSQL
- sys.messages_TSQL
- sys.messages
- messages
dev_langs:
- TSQL
helpviewer_keywords:
- error messages [SQL Server]
- sys.messages catalog view
- error numbers [SQL Server]
ms.assetid: 8c16ecdf-68f4-4a2a-b594-086e3344e58a
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: aa37a19743801bea70b1c78d8c9606be74dfe2f8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="messages-for-errors-catalog-views---sysmessages"></a>Affichages catalogue de messages (erreurs) - sys.messages
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque **message_id** ou **ID_langue** des messages d’erreur dans le système, pour les messages à la fois défini par le système et définies par l’utilisateur. Pour plus d’informations, consultez [sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md).  
   
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**message_id**|**int**|ID du message. Unique sur le serveur. Les ID de message inférieurs à 50 000 sont des messages système.|  
|**ID_langue**|**smallint**|ID de langue pour laquelle le texte de **texte** est utilisé, comme défini dans **syslanguages**. Il est unique pour un **message_id**.|  
|**severity**|**tinyint**|Niveau de gravité du message, entre 1 et 25. Cela est identique pour toutes les langues de message dans un **message_id**.|  
|**is_event_logged**|**bit**|1 = le message est consigné dans le journal des événements lorsqu'une erreur est déclenchée. Cela est identique pour toutes les langues de message dans un **message_id**.|  
|**texte**|**nvarchar(2048)**|Texte du message utilisé lorsque le correspondant **ID_langue** est actif.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Messages &#40;pour les erreurs&#41; affichages catalogue &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)   
 [Message d’exception zone programmation](http://msdn.microsoft.com/library/0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c)   
 [Messages d’erreur](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [Erreurs et événements du moteur de base de données](../../relational-databases/errors-events/database-engine-events-and-errors.md)  
  
  
