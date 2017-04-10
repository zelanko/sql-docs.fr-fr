---
title: "T&#226;che Envoyer un message | Microsoft Docs"
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
  - "sql13.dts.designer.sendmailtask.f1"
helpviewer_keywords: 
  - "messagerie [Integration Services]"
  - "tache Envoyer un message"
  - "courrier électronique [Integration Services]"
  - "messages [Integration Services]"
  - "sending messages"
ms.assetid: fe0b7cbc-fe8e-4fe2-95b4-2953efff5869
caps.latest.revision: 51
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 51
---
# T&#226;che Envoyer un message
  La tâche Envoyer un message envoie un message électronique. La tâche Envoyer un message permet à un package d'envoyer des messages en cas de réussite ou d'échec des tâches du flux de travail du package, ou d'envoyer des messages en réponse à un événement déclenché par le package au moment de l'exécution. Par exemple, la tâche peut notifier à un administrateur de base de données la réussite ou l'échec de la tâche de sauvegarde de base de données.  
  
 Vous pouvez configurer la tâche Envoyer un message comme suit :  
  
-   Fournissez le texte du message électronique.  
  
-   Indiquez une ligne d'objet pour le message électronique.  
  
-   Définissez le niveau de priorité du message. La tâche prend en charge trois niveaux de priorité : normale, basse et haute.  
  
-   Indiquez les destinataires dans les lignes À, Cc et Cci. Si la tâche spécifie plusieurs destinataires, ceux-ci sont séparés par des points-virgules.  
  
    > [!NOTE]  
    >  Les lignes À, Cc et Cci sont limitées chacune à 256 caractères conformément aux normes Internet.  
  
-   Incluez les pièces jointes. Si la tâche spécifie plusieurs pièces jointes, celles-ci sont séparées par la barre verticale ( | ).  
  
    > [!NOTE]  
    >  Si un fichier de pièce jointe n'existe pas lors de l'exécution du package, une erreur se produit.  
  
-   Spécifiez le gestionnaire de connexions SMTP à utiliser.  
  
    > [!IMPORTANT]  
    >  Le gestionnaire de connexions SMTP prend en charge uniquement l'authentification anonyme et l'authentification Windows. Il ne prend pas en charge l'authentification de base.  
  
 Le texte du message peut être une chaîne indiquée par vos soins, ou bien une connexion à un fichier, ou le nom d'une variable qui contient le texte. La tâche utilise un gestionnaire de connexions de fichiers pour se connecter à un fichier. Pour plus d'informations, consultez [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
 La tâche utilise un gestionnaire de connexions SMTP pour se connecter à un serveur de messagerie. Pour plus d’informations, consultez [Gestionnaire de connexions SMTP](../../integration-services/connection-manager/smtp-connection-manager.md).  
  
## Messages de journalisation personnalisés disponibles dans la tâche Envoyer un message  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche Envoyer un message. Pour plus d’informations, consultez [Journalisation Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../../integration-services/performance/custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|**SendMailTaskBegin**|Indique que la tâche a commencé l'envoi d'un message électronique.|  
|**SendMailTaskEnd**|Indique que la tâche a terminé l'envoi d'un message électronique.|  
|**SendMailTaskInfo**|Fournit des informations détaillées concernant la tâche.|  
  
## Configuration de la tâche Envoyer un message  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche Envoyer un message &#40;page Général&#41;](../../integration-services/control-flow/send-mail-task-editor-general-page.md)  
  
-   [Éditeur de tâche Envoyer un message &#40;page Courrier&#41;](../../integration-services/control-flow/send-mail-task-editor-mail-page.md)  
  
-   [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.SendMailTask.SendMailTask>  
  
## Tâches associées  
 Pour obtenir des informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], cliquez sur [Définir les propriétés d’une tâche ou d’un conteneur](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md).  
  
## Contenu connexe  
  
-   Article technique [How to send email with delivery notification in C#](http://go.microsoft.com/fwlink/?LinkId=237625) (Procédure d’envoi d’e-mail avec notification de remise en C#) sur shareourideas.com  
  
## Voir aussi  
 [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flux de contrôle](../../integration-services/control-flow/control-flow.md)  
  
  