---
title: dbo.sysalerts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysalerts
- sysalerts_TSQL
- dbo.sysalerts_TSQL
- sysalerts
dev_langs:
- TSQL
helpviewer_keywords:
- sysalerts system table
ms.assetid: a2c2f50d-61f3-4951-996a-add5ad092cc2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7bad6fbd9229547318a060f08eeb102b21cda9bb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470887"
---
# <a name="dbosysalerts-transact-sql"></a>dbo.sysalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque alerte. Une alerte est un message envoyé en réponse à un événement. Elle peut transmettre des messages au-delà de l'environnement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sous la forme d'un message électronique ou d'un radiomessage. Une alerte peut également générer une tâche.  Cette table est stockée dans le **msdb** base de données.
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|Identification de l'alerte|  
|**nom**|**sysname**|Nom de l’alerte.|  
|**event_source**|**nvarchar(100)**|Source de l'événement : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**event_category_id**|**Int**|Réservé pour un usage ultérieur.|  
|**event_id**|**Int**|Réservé pour un usage ultérieur.|  
|**message_id**|**Int**|Défini par l’utilisateur ID de message ou une référence à **sysmessages** message qui déclenche cette alerte.|  
|**severity**|**Int**|Gravité de l'erreur qui déclenche cette alerte.|  
|**enabled**|**tinyint**|État de l'alerte :<br /><br /> **0** = désactivé.<br /><br /> **1** = activé.|  
|**delay_between_responses**|**Int**|Délai d'attente, en secondes, entre les notifications de cette alerte.|  
|**last_occurrence_date**|**Int**|Dernière occurrence (date) de l'alerte.|  
|**last_occurrence_time**|**Int**|Dernière occurrence (heure) de l'alerte.|  
|**last_response_date**|**Int**|Dernière notification (date) de l'alerte.|  
|**last_response_time**|**Int**|Dernière notification (heure) de l'alerte.|  
|**notification_message**|**nvarchar(512)**|Informations complémentaires envoyées avec l'alerte.|  
|**include_event_description**|**tinyint**|Masque de bits indiquant si la description de l’événement est envoyée par courrier électronique, radiomessagerie ou Net send. Consultez le tableau ci-dessous pour les valeurs.|  
|**database_name**|**nvarchar(512)**|Base de données dans laquelle cette alerte doit se produire pour déclencher cette alerte.|  
|**event_description_keyword**|**nvarchar(100)**|Modèle auquel doit correspondre l'erreur pour déclencher l'alerte.|  
|**occurrence_count**|**Int**|Nombre d'occurrences de cette alerte.|  
|**count_reset_date**|**Int**|Nombre de jours (date) sera remis à **0**.|  
|**count_reset_time**|**Int**|Heure du nombre de jours sera remis à **0**.|  
|**job_id**|**uniqueidentifier**|Identificateur du travail exécuté lorsque l'alerte se produit.|  
|**has_notification**|**Int**|Nombre d'opérateurs avertis par courrier électronique lorsque l'alerte a lieu.|  
|**flags**|**Int**|Réservé.|  
|**performance_condition**|**nvarchar(512)**|Réservé.|  
|**category_id**|**Int**|Réservé.|  
  
 ## <a name="remarks"></a>Notes

Le tableau suivant montre les valeurs pour le masque de bits include_event_description. La valeur décimale est retournée par dbo.sysalerts. 

|Décimal | binary | Signification |
|------|------|------|
|0 |0000 |Aucun message |
|1 |0001 |Messagerie |
|2 |0010 |récepteur de radiomessagerie |
|3 |0011 |récepteur de radiomessagerie et messagerie |
|4 |0100 |Envoi réseau |
|5 |0101 |Courrier électronique et net send |
|6 |0110 |Récepteur de radiomessagerie et net send |
|7 |0111 |Courrier électronique, radiomessagerie et net send |
  
