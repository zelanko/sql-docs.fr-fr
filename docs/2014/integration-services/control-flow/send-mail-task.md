---
title: Envoyer un message, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.f1
helpviewer_keywords:
- mail [Integration Services]
- Send Mail task
- e-mail [Integration Services]
- messages [Integration Services]
- sending messages
ms.assetid: fe0b7cbc-fe8e-4fe2-95b4-2953efff5869
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 21db77ad7f226c78f31adaef80162b445129249e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257295"
---
# <a name="send-mail-task"></a>tache Envoyer un message
  La tâche Envoyer un message envoie un message électronique. La tâche Envoyer un message permet à un package d'envoyer des messages en cas de réussite ou d'échec des tâches du flux de travail du package, ou d'envoyer des messages en réponse à un événement déclenché par le package au moment de l'exécution. Par exemple, la tâche peut notifier à un administrateur de base de données la réussite ou l'échec de la tâche de sauvegarde de base de données.  
  
 Vous pouvez configurer la tâche Envoyer un message comme suit :  
  
-   Fournissez le texte du message électronique.  
  
-   Indiquez une ligne d'objet pour le message électronique.  
  
-   Définissez le niveau de priorité du message. La tâche prend en charge trois niveaux de priorité : normale, basse et haute.  
  
-   Indiquez les destinataires dans les lignes À, Cc et Cci. Si la tâche spécifie plusieurs destinataires, ceux-ci sont séparés par des points-virgules.  
  
    > [!NOTE]  
    >  Les lignes À, Cc et Cci sont limitées chacune à 256 caractères conformément aux normes Internet.  
  
-   Incluez les pièces jointes. Si la tâche spécifie plusieurs pièces jointes, celles-ci sont séparées par la barre verticale ( | ).  
  
    > [!NOTE]  
    >  Si un fichier de pièce jointe n'existe pas lors de l'exécution du package, une erreur se produit.  
  
-   Spécifiez le gestionnaire de connexions SMTP à utiliser.  
  
    > [!IMPORTANT]  
    >  Le gestionnaire de connexions SMTP prend en charge uniquement l'authentification anonyme et l'authentification Windows. Il ne prend pas en charge l'authentification de base.  
  
 Le texte du message peut être une chaîne indiquée par vos soins, ou bien une connexion à un fichier, ou le nom d'une variable qui contient le texte. La tâche utilise un gestionnaire de connexions de fichiers pour se connecter à un fichier. Pour plus d'informations, consultez [Flat File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 La tâche utilise un gestionnaire de connexions SMTP pour se connecter à un serveur de messagerie. Pour plus d’informations, consultez [Gestionnaire de connexions SMTP](../connection-manager/smtp-connection-manager.md).  
  
## <a name="custom-logging-messages-available-on-the-send-mail-task"></a>Messages de journalisation personnalisés disponibles dans la tâche Envoyer un message  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche Envoyer un message. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`SendMailTaskBegin`|Indique que la tâche a commencé l'envoi d'un message électronique.|  
|`SendMailTaskEnd`|Indique que la tâche a terminé l'envoi d'un message électronique.|  
|`SendMailTaskInfo`|Fournit des informations détaillées concernant la tâche.|  
  
## <a name="configuring-the-send-mail-task"></a>Configuration de la tâche Envoyer un message  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tache envoyer &#40;Page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur de tache envoyer &#40;Page de messagerie&#41;](../send-mail-task-editor-mail-page.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.SendMailTask.SendMailTask>  
  
## <a name="related-tasks"></a>Related Tasks  
 Pour obtenir des informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="related-content"></a>Contenu associé  
  
-   Article technique [Procédure d'envoi de courrier électronique avec notification de remise en C#](http://go.microsoft.com/fwlink/?LinkId=237625)(Procédure d’envoi d’e-mail avec notification de remise en C#) sur shareourideas.com  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](integration-services-tasks.md)   
 [Flux de contrôle](control-flow.md)  
  
  
