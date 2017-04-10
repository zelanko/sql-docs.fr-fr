---
title: "Cat&#233;gorie d&#39;&#233;v&#233;nement Broker | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Classes d’événements SQL Server, catégorie d’événement Broker"
  - "Broker [SQL Server], catégorie d'événement"
  - "classes d’événements [SQL Server], catégorie d’événement Broker"
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
caps.latest.revision: 17
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 17
---
# Cat&#233;gorie d&#39;&#233;v&#233;nement Broker
  La catégorie d’événement **Broker** contient des événements généraux de Service Broker.  
  
## Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Classe d'événement Broker:Activation](../../relational-databases/event-classes/broker-activation-event-class.md)|Événement généré lorsqu'un moniteur de file d'attente démarre une procédure stockée d'activation.|  
|[Classe d'événement Broker:Connection](../../relational-databases/event-classes/broker-connection-event-class.md)|Événement généré pour signaler l'état d'une connexion de transport gérée par Service Broker.|  
|[Classe d'événements Broker:Conversation](../../relational-databases/event-classes/broker-conversation-event-class.md)|Événement généré pour rapporter les progrès d'une conversation.|  
|[Classe d'événement Broker:Conversation Group](../../relational-databases/event-classes/broker-conversation-group-event-class.md)|Événement généré lorsque la base de données crée ou supprime un groupe de conversations.|  
|[Classe d'événements Broker:Corrupted Message](../../relational-databases/event-classes/broker-corrupted-message-event-class.md)|Événement généré pour indiquer que la base de données a reçu un message endommagé.|  
|[Classe d'événements Broker:Forwarded Message Dropped](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md)|Événement généré lorsque SQL Server supprime un message Service Broker qui aurait dû être transféré.|  
|[Broker:Forwarded Message Sent (classe d'événements)](../../relational-databases/event-classes/broker-forwarded-message-sent-event-class.md)|Événement généré lorsque SQL Server transfère un message Service Broker.|  
|[Classe d'événements Broker:Message Classify](../../relational-databases/event-classes/broker-message-classify-event-class.md)|Événement généré lorsque Service Broker détermine le routage d'un message.|  
|[Classe d'événements Broker:Message Drop](../../relational-databases/event-classes/broker-message-drop-event-class.md)|Événement généré lorsque Service Broker ne peut pas conserver un message reçu qui aurait dû être remis à un service dans cette instance.|  
|[Classe d'événements Broker:Remote Message Ack](../../relational-databases/event-classes/broker-remote-message-ack-event-class.md)|Événement généré lorsque Service Broker envoie ou reçoit un accusé de réception du message.|  
  
 Deux événements d'audit de sécurité sont également fournis pour Service Broker. Pour plus d’informations sur ces événements, consultez [Classe d’événements Audit Broker Login](../../relational-databases/event-classes/audit-broker-login-event-class.md) et [Classe d’événement Audit Broker Conversation](../../relational-databases/event-classes/audit-broker-conversation-event-class.md).  
  
## Voir aussi  
 [Catégorie d'événement Audit de sécurité](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  