---
title: sys. messages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6f54b68f7775910a7e25b858bd7579e751a75b98
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897130"
---
# <a name="messages-for-errors-catalog-views---sysmessages"></a>Affichages catalogue des messages (d’erreur) - sys.messages
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Contient une ligne pour chaque **message_id** ou **language_id** des messages d’erreur dans le système, à la fois pour les messages définis par le système et par l’utilisateur. Pour plus d’informations, consultez [sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md).  
   
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**message_id**|**int**|ID du message. Unique sur le serveur. Les ID de message inférieurs à 50 000 sont des messages système.|  
|**language_id**|**smallint**|ID de langue pour lequel le texte du **texte** est utilisé, tel que défini dans **syslanguages**. Il est unique pour un **message_id**spécifié.|  
|**severity**|**tinyint**|Niveau de gravité du message, entre 1 et 25. Cela est identique pour toutes les langues de message dans un **message_id**.|  
|**is_event_logged**|**bit**|1 = le message est consigné dans le journal des événements lorsqu'une erreur est déclenchée. Cela est identique pour toutes les langues de message dans un **message_id**.|  
|**text**|**nvarchar(2048)**|Texte du message utilisé lorsque la **language_id** correspondante est active.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** . Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)   
 [Affichages catalogue &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Messages &#40;pour les erreurs&#41; les affichages catalogue &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)   
 [Programmation de la boîte de message d’exception](https://msdn.microsoft.com/library/0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c)   
 [Messages d’erreur](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [Événements et erreurs de Moteur de base de données](../../relational-databases/errors-events/database-engine-events-and-errors.md)  
  
  
