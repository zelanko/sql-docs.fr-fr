---
title: Éditeur de tâche MSMQ (page général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.general.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2cdd3c2e8e903de90871b096d24cda17fe490d1d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057630"
---
# <a name="message-queue-task-editor-general-page"></a>Éditeur de tâche MSMQ (page Général)
  Utilisez la page **Général** de la boîte de dialogue **Éditeur de tâche MSMQ** pour nommer et décrire la tâche MSMQ, pour spécifier le format du message et indiquer si la tâche envoie ou reçoit des messages.  
  
 Pour en savoir plus sur cette tâche, consultez [Message Queue Task](control-flow/message-queue-task.md).  
  
## <a name="options"></a>Options  
 **Nom**  
 Attribuez un nom unique à la tâche MSMQ. Ce nom sert d'étiquette à l'icône de la tâche.  
  
> [!NOTE]  
>  Les noms de tâche doivent être uniques dans un package.  
  
 **Description**  
 Tapez la description de la tâche MSMQ.  
  
 **Use2000Format**  
 Indiquez si le format 2000 de Message Queuing (ou MSMQ) doit être utilisé. Par défaut, il s’agit de `False`.  
  
 **MSMQConnection**  
 Sélectionnez un gestionnaire de connexions MSMQ existant ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
 **Rubriques connexes**: [Gestionnaire de connexions MSMQ](connection-manager/msmq-connection-manager.md), [éditeur du gestionnaire de connexions MSMQ](../../2014/integration-services/msmq-connection-manager-editor.md)  
  
 **Message**  
 Spécifiez si la tâche MSMQ envoie ou reçoit des messages. Si vous sélectionnez l’option **Envoyer un message**, la page Envoyer est répertoriée dans le volet gauche de la boîte de dialogue ; si vous sélectionnez l’option **Recevoir un message**, la page Recevoir est répertoriée. Par défaut, cette valeur est définie sur **Envoyer un message**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche MSMQ &#40;page de réception&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md)   
 [Éditeur de tâche MSMQ &#40;page envoyer&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
