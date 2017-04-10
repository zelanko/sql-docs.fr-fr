---
title: "&#201;diteur de t&#226;che MSMQ (page G&#233;n&#233;ral) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.msgqueuetask.general.f1"
helpviewer_keywords: 
  - "Éditeur de tâche MSMQ"
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# &#201;diteur de t&#226;che MSMQ (page G&#233;n&#233;ral)
  Utilisez la page **Général** de la boîte de dialogue **Éditeur de tâche MSMQ** pour nommer et décrire la tâche MSMQ, pour spécifier le format du message et indiquer si la tâche envoie ou reçoit des messages.  
  
 Pour en savoir plus sur cette tâche, consultez [Message Queue Task](../../integration-services/control-flow/message-queue-task.md).  
  
## Options  
 **Nom**  
 Attribuez un nom unique à la tâche MSMQ. Ce nom sert d'étiquette à l'icône de la tâche.  
  
> [!NOTE]  
>  Les noms de tâche doivent être uniques dans un package.  
  
 **Description**  
 Tapez la description de la tâche MSMQ.  
  
 **Use2000Format**  
 Indiquez si le format 2000 de Message Queuing (ou MSMQ) doit être utilisé. La valeur par défaut est **False**.  
  
 **MSMQConnection**  
 Sélectionnez un gestionnaire de connexions MSMQ existant ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
 **Rubriques connexes** : [Gestionnaire de connexions MSMQ](../../integration-services/connection-manager/msmq-connection-manager.md), [Éditeur du gestionnaire de connexions MSMQ](../../integration-services/connection-manager/msmq-connection-manager-editor.md)  
  
 **Message**  
 Spécifiez si la tâche MSMQ envoie ou reçoit des messages. Si vous sélectionnez l’option **Envoyer un message**, la page Envoyer est répertoriée dans le volet gauche de la boîte de dialogue ; si vous sélectionnez l’option **Recevoir un message**, la page Recevoir est répertoriée. Par défaut, cette valeur est définie sur **Envoyer un message**.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche MSMQ &#40;page Recevoir&#41;](../../integration-services/control-flow/message-queue-task-editor-receive-page.md)   
 [Éditeur de tâche MSMQ &#40;page Envoyer&#41;](../../integration-services/control-flow/message-queue-task-editor-send-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
  