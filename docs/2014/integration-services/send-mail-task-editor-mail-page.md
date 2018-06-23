---
title: Éditeur de tache envoyer (Page courrier) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.sendmailtask.mail.f1
helpviewer_keywords:
- Send Mail Task Editor
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b65b2b385489073010d853ea01c3f6feb2a1924b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045181"
---
# <a name="send-mail-task-editor-mail-page"></a>Éditeur de tâche Envoyer un message (page Courrier)
  Utilisez la page **Courrier** de la boîte de dialogue **Éditeur de tâche Envoyer un message** pour indiquer les destinataires d'un message, son type et sa priorité. Vous pouvez également joindre des fichiers au message. Le texte de ce courrier peut se présenter sous la forme d'une chaîne que vous précisez, d'une connexion à un fichier comportant le texte voulu ou le nom d'une variable contenant le texte en question.  
  
 Pour en savoir plus sur cette tâche, consultez [Send Mail Task](control-flow/send-mail-task.md).  
  
## <a name="options"></a>Options  
 **SMTPConnection**  
 Sélectionnez un gestionnaire de connexions SMTP dans la liste ou cliquez sur **\<Nouvelle connexion...**> pour en créer un.  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions SMTP prend en charge uniquement l'authentification anonyme et l'authentification Windows. Il ne prend pas en charge l'authentification de base.  
  
 **Rubriques connexes :** [Gestionnaire de connexions SMTP](connection-manager/smtp-connection-manager.md)  
  
 **De**  
 Indique l'adresse électronique de l'expéditeur.  
  
 **Pour**  
 Fournit les adresses de messagerie des destinataires séparées par un point-virgule.  
  
 **Cc**  
 Fournit les adresses de messagerie des individus destinés à recevoir une copie du message, séparées par un point-virgule.  
  
 **Cci**  
 Fournit les adresses de messagerie des individus destinés à recevoir une copie carbone invisible (Cci) du message, séparées par un point-virgule.  
  
 **Subject**  
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
>  Les lignes À, Cc et Cci sont limitées à 256 caractères, conformément aux Internet standards.  
  
## <a name="messagesourcetype-dynamic-options"></a>Options dynamiques de MessageSourceType  
  
### <a name="messagesourcetype--direct-input"></a>MessageSourceType = Entrée directe  
 **MessageSource**  
 Permet d’entrer le texte du message ou de cliquer sur le bouton d’exploration représenté par les points de suspension (…), puis de taper le message dans la boîte de dialogue **Source du message** .  
  
### <a name="messagesourcetype--file-connection"></a>MessageSourceType = Connexion de fichiers  
 **MessageSource**  
 Sélectionnez un gestionnaire de connexions de fichiers dans la liste ou cliquez sur <\<**Nouvelle connexion...**> pour en créer un.  
  
 **Rubriques connexes :** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="messagesourcetype--variable"></a>MessageSourceType = Variable  
 **MessageSource**  
 Sélectionnez une variable dans la liste ou cliquez sur <\<**Nouvelle variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Ajouter une variable](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tache envoyer &#40;Page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  