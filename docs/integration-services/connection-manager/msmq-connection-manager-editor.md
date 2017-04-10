---
title: "&#201;diteur du gestionnaire de connexions MSMQ | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.msmqconnectionmanager.f1"
helpviewer_keywords: 
  - "Éditeur du gestionnaire de connexions MSMQ"
ms.assetid: ef842cb4-82da-4550-85fe-9bedbc1e77c7
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# &#201;diteur du gestionnaire de connexions MSMQ
  La boîte de dialogue **Gestionnaire de connexions MSMQ** permet de spécifier le chemin d’une file d’attente de messages MSMQ (Message Queuing).  
  
 Pour en savoir plus sur le gestionnaire de connexions MSMQ, consultez [MSMQ Connection Manager](../../integration-services/connection-manager/msmq-connection-manager.md).  
  
> [!NOTE]  
>  Le gestionnaire de connexions MSMQ prend en charge les files d'attente privées et publiques locales et les files d'attente publiques distantes. Il ne prend pas en charge les files d'attente privées distantes. Pour une solution de contournement qui utilise la tâche de script, consultez [Sending to a Remote Private Message Queue with the Script Task](../../integration-services/extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md).  
  
## Options  
 **Nom**  
 Fournissez un nom unique pour le gestionnaire de connexions MSMQ dans le flux de travail. Le nom fourni sera affiché dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 **Description**  
 Décrivez le gestionnaire de connexions. Il est recommandé d'indiquer ici l'usage auquel le gestionnaire de connexions est destiné, de sorte que les packages soient correctement documentés et plus faciles à gérer.  
  
 **Chemin d'accès**  
 Tapez le chemin d'accès complet de la file d'attente de messages. Le format du chemin d'accès dépend du type de file d'attente.  
  
|Type de file d'attente|Exemple de chemin d'accès|  
|----------------|-----------------|  
|Public|\<nom de l’ordinateur>\\<nom de la file d’attente\>|  
|Privé|\<nom de l’ordinateur>\Private$\\<nom de la file d’attente\>|  
  
 Vous pouvez utiliser "." pour représenter l'ordinateur local.  
  
 **Test**  
 Après avoir configuré le gestionnaire de connexions MSMQ, vérifiez si la connexion est opérationnelle en cliquant sur **Tester**.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)  
  
  