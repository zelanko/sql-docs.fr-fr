---
title: "&#201;diteur de t&#226;che de transfert de messages d&#39;erreur (page Messages) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transfererrormessagestask.errormessages.F1"
helpviewer_keywords: 
  - "Éditeur de tâche de transfert de messages d'erreur"
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# &#201;diteur de t&#226;che de transfert de messages d&#39;erreur (page Messages)
  Utilisez la page **Messages** de la boîte de dialogue **Éditeur de tâche de transfert de messages d’erreur** pour spécifier les propriétés de copie d’un ou plusieurs messages d’erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]définis par l’utilisateur d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]à une autre. Pour plus d'informations sur cette tâche, consultez [Transfer Error Messages Task](../../integration-services/control-flow/transfer-error-messages-task.md).  
  
## Options  
 **SourceConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur source.  
  
 **DestinationConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur de destination.  
  
 **IfObjectExists**  
 Déterminez si la tâche doit remplacer les messages d'erreur définis par l'utilisateur existants, ignorer les messages existants ou échouer si des messages d'erreur du même nom existent déjà sur le serveur de destination.  
  
 **TransferAllErrorMessages**  
 Déterminez si la tâche doit copier du serveur source au serveur de destination tous les messages définis par l'utilisateur ou seulement ceux spécifiés.  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|Copie tous les messages définis par l'utilisateur.|  
|**False**|Copie uniquement les messages définis par l'utilisateur spécifiés.|  
  
 **ErrorMessagesList**  
 Cliquez sur le bouton Parcourir **(…)** pour sélectionner les messages d’erreur à copier.  
  
> [!NOTE]  
>  Vous devez spécifier **SourceConnection** avant de pouvoir sélectionner les messages d’erreur à copier.  
  
 **ErrorMessageLanguagesList**  
 Cliquez sur le bouton Parcourir **(…)** pour sélectionner les langues pour lesquelles copier les messages d’erreur définis par l’utilisateur sur le serveur de destination. Une version us_english (page de codes 1033) du message doit exister sur le serveur de destination avant de pouvoir transférer vers ce serveur d'autres versions de langue du message.  
  
> [!NOTE]  
>  Vous devez spécifier **SourceConnection** avant de pouvoir sélectionner les messages d’erreur à copier.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Éditeur de tâche de transfert de messages d’erreur &#40;page Général&#41;](../../integration-services/control-flow/transfer-error-messages-task-editor-general-page.md)   
 [Gestionnaire de connexions SMO](../../integration-services/connection-manager/smo-connection-manager.md)   
 [Éditeur de tâche de transfert de messages d’erreur &#40;page Général&#41;](../../integration-services/control-flow/transfer-error-messages-task-editor-general-page.md)   
 [Gestionnaire de connexions SMO](../../integration-services/connection-manager/smo-connection-manager.md)  
  
  