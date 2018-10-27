---
title: Broker, catégorie d’événement | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Broker event category
- Broker event category [SQL Server]
- event classes [SQL Server], Broker event category
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 602113da86b3d8ffdc79484b35dab59749844a01
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145644"
---
# <a name="broker-event-category"></a>Catégorie d'événement Broker
  La catégorie d’événement **Broker** contient des événements généraux de Service Broker.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Classe d'événement Broker:Activation](broker-activation-event-class.md)|Événement généré lorsqu'un moniteur de file d'attente démarre une procédure stockée d'activation.|  
|[Classe d'événement Broker:Connection](broker-connection-event-class.md)|Événement généré pour signaler l'état d'une connexion de transport gérée par Service Broker.|  
|[Classe d'événements Broker:Conversation](broker-conversation-event-class.md)|Événement généré pour rapporter les progrès d'une conversation.|  
|[Classe d'événement Broker:Conversation Group](broker-conversation-group-event-class.md)|Événement généré lorsque la base de données crée ou supprime un groupe de conversations.|  
|[Classe d'événements Broker:Corrupted Message](broker-corrupted-message-event-class.md)|Événement généré pour indiquer que la base de données a reçu un message endommagé.|  
|[Classe d'événements Broker:Forwarded Message Dropped](broker-forwarded-message-dropped-event-class.md)|Événement généré lorsque SQL Server supprime un message Service Broker qui aurait dû être transféré.|  
|[Broker:Forwarded Message Sent (classe d'événements)](broker-forwarded-message-sent-event-class.md)|Événement généré lorsque SQL Server transfère un message Service Broker.|  
|[Classe d'événements Broker:Message Classify](broker-message-classify-event-class.md)|Événement généré lorsque Service Broker détermine le routage d'un message.|  
|[Classe d'événements Broker:Message Drop](broker-message-drop-event-class.md)|Événement généré lorsque Service Broker ne peut pas conserver un message reçu qui aurait dû être remis à un service dans cette instance.|  
|[Classe d'événements Broker:Remote Message Ack](broker-remote-message-ack-event-class.md)|Événement généré lorsque Service Broker envoie ou reçoit un accusé de réception du message.|  
  
 Deux événements d'audit de sécurité sont également fournis pour Service Broker. Pour plus d’informations sur ces événements, consultez [Classe d’événements Audit Broker Login](audit-broker-login-event-class.md) et [Classe d’événement Audit Broker Conversation](audit-broker-conversation-event-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Catégorie d'événement Audit de sécurité](https://docs.microsoft.com/bi-reference/trace-events/security-audit-event-category)  
  
  
