---
title: "&#201;diteur de t&#226;che Envoyer un message (page Courrier) | Microsoft Docs"
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
  - "sql13.dts.designer.sendmailtask.mail.f1"
helpviewer_keywords: 
  - "Éditeur de tache Envoyer un message"
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# &#201;diteur de t&#226;che Envoyer un message (page Courrier)
  Utilisez la page **Courrier** de la boîte de dialogue **Éditeur de tâche Envoyer un message** pour indiquer les destinataires d'un message, son type et sa priorité. Vous pouvez également joindre des fichiers au message. Le texte de ce courrier peut se présenter sous la forme d'une chaîne que vous précisez, d'une connexion à un fichier comportant le texte voulu ou le nom d'une variable contenant le texte en question.  
  
 Pour en savoir plus sur cette tâche, consultez [Send Mail Task](../../integration-services/control-flow/send-mail-task.md).  
  
## Options  
 **SMTPConnection**  
 Sélectionnez un gestionnaire de connexions SMTP dans la liste ou cliquez sur **\<Nouvelle connexion...>** pour créer un gestionnaire de connexions.  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions SMTP prend en charge uniquement l'authentification anonyme et l'authentification Windows. Il ne prend pas en charge l'authentification de base.  
  
 **Rubriques connexes :** [Gestionnaire de connexions SMTP](../../integration-services/connection-manager/smtp-connection-manager.md)  
  
 **De**  
 Indique l'adresse électronique de l'expéditeur.  
  
 **Pour**  
 Fournit les adresses de messagerie des destinataires séparées par un point-virgule.  
  
 **Cc**  
 Fournit les adresses de messagerie des individus destinés à recevoir une copie du message, séparées par un point-virgule.  
  
 **Cci**  
 Fournit les adresses de messagerie des individus destinés à recevoir une copie carbone invisible (Cci) du message, séparées par un point-virgule.  
  
 **Objet**  
 Permet de spécifier l'objet du message électronique.  
  
 **MessageSourceType**  
 Permet de sélectionner le type de source du message. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée directe**|Permet de définir la source du texte du message. Si cette valeur est sélectionnée, les options dynamiques incluses dans **MessageSource**s'affichent alors.|  
|**Connexion de fichiers**|Permet de définir la source du fichier contenant le texte du message. Si cette valeur est sélectionnée, les options dynamiques incluses dans **MessageSource**s'affichent alors.|  
|**Variable**|Permet d'attribuer à la source une variable contenant le texte du message. Si cette valeur est sélectionnée, les options dynamiques incluses dans **MessageSource**s'affichent alors.|  
  
 **Priorité**  
 Permet d'indiquer la priorité à appliquer au message.  
  
 **Pièces jointes**  
 Indique le nom des fichiers joints au message électronique, séparés par le caractère Barre verticale (|).  
  
> [!NOTE]  
>  Les lignes À, Cc et Cci sont limitées à 256 caractères, conformément aux Internet standards.  
  
## Options dynamiques de MessageSourceType  
  
### MessageSourceType = Entrée directe  
 **MessageSource**  
 Permet d’entrer le texte du message ou de cliquer sur le bouton d’exploration représenté par les points de suspension (…), puis de taper le message dans la boîte de dialogue **Source du message**.  
  
### MessageSourceType = Connexion de fichiers  
 **MessageSource**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### MessageSourceType = Variable  
 **MessageSource**  
 Sélectionnez une variable dans la liste ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md), [Ajouter une variable](../Topic/Add%20Variable.md)  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche Envoyer un message &#40;page Général&#41;](../../integration-services/control-flow/send-mail-task-editor-general-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
  