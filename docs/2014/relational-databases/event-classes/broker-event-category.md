---
title: Broker, catégorie d’événement | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
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
ms.openlocfilehash: 9918aca57caaef0dc460e810f5ed5ca2d1106ac3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62663808"
---
# <a name="broker-event-category"></a>Catégorie d'événement Broker
  La catégorie d’événement **Broker** contient des événements généraux de Service Broker.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Broker:Activation, classe d’événements](broker-activation-event-class.md)|Événement généré lorsqu'un moniteur de file d'attente démarre une procédure stockée d'activation.|  
|[Broker:Connection, classe d’événements](broker-connection-event-class.md)|Événement généré pour signaler l'état d'une connexion de transport gérée par Service Broker.|  
|[Broker:Conversation, classe d’événements](broker-conversation-event-class.md)|Événement généré pour rapporter les progrès d'une conversation.|  
|[Broker:Conversation Group, classe d’événements](broker-conversation-group-event-class.md)|Événement généré lorsque la base de données crée ou supprime un groupe de conversations.|  
|[Broker:Corrupted Message, classe d’événements](broker-corrupted-message-event-class.md)|Événement généré pour indiquer que la base de données a reçu un message endommagé.|  
|[Broker:Forwarded Message Dropped, classe d’événements](broker-forwarded-message-dropped-event-class.md)|Événement généré lorsque SQL Server supprime un message Service Broker qui aurait dû être transféré.|  
|[Broker:Forwarded Message Sent, classe d’événements](broker-forwarded-message-sent-event-class.md)|Événement généré lorsque SQL Server transfère un message Service Broker.|  
|[Classe d'événements Broker:Message Classify](broker-message-classify-event-class.md)|Événement généré lorsque Service Broker détermine le routage d'un message.|  
|[Classe d'événements Broker:Message Drop](broker-message-drop-event-class.md)|Événement généré lorsque Service Broker ne peut pas conserver un message reçu qui aurait dû être remis à un service dans cette instance.|  
|[Classe d'événements Broker:Remote Message Ack](broker-remote-message-ack-event-class.md)|Événement généré lorsque Service Broker envoie ou reçoit un accusé de réception du message.|  
  
 Deux événements d'audit de sécurité sont également fournis pour Service Broker. Pour plus d’informations sur ces événements, consultez [Classe d’événements Audit Broker Login](audit-broker-login-event-class.md) et [Classe d’événement Audit Broker Conversation](audit-broker-conversation-event-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Catégorie d'événement Audit de sécurité](https://docs.microsoft.com/bi-reference/trace-events/security-audit-event-category)  
  
  
