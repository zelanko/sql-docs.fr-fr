---
title: "&#201;diteur de t&#226;che MSMQ (page Recevoir) | Microsoft Docs"
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
  - "sql13.dts.designer.msgqueuetask.receive.f1"
helpviewer_keywords: 
  - "Éditeur de tâche MSMQ"
ms.assetid: 7028756d-1dcc-480c-bbcd-e9654f0772a0
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# &#201;diteur de t&#226;che MSMQ (page Recevoir)
  La page **Recevoir** de la boîte de dialogue **Éditeur de tâche MSMQ** permet de configurer une tâche MSMQ pour recevoir des messages MSMQ (Message Queuing) [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
 Pour en savoir plus sur cette tâche, consultez [Message Queue Task](../../integration-services/control-flow/message-queue-task.md).  
  
## Options  
 **RemoveFromMessageQueue**  
 Indiquez si vous voulez supprimer le message de la file d'attente après sa réception. La valeur par défaut est **False**.  
  
 **ErrorIfMessageTimeOut**  
 Indiquez si la tâche échoue lorsque le message expire, en affichant un message d'erreur. La valeur par défaut est **False**.  
  
 **TimeoutAfter**  
 Si vous choisissez d'afficher un message d'erreur sur l'échec de la tâche, définissez le nombre de secondes qui précèdent le message d'expiration.  
  
 **MessageType**  
 Sélectionnez le type de message : Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Message de fichiers de données**|Le message est stocké dans un fichier. La sélection de cette valeur affiche l'option dynamique **DataFileMessage**.|  
|**Message de type variable**|Le message est stocké dans une variable. Cette valeur affiche l'option dynamique **VariableMessage**.|  
|**Message de type chaîne**|Le message est stocké dans la tâche MSMQ. Cette valeur affiche l'option dynamique **StringMessage**.|  
|**Message de type chaîne pour la variable**|Le message<br /><br /> Cette valeur affiche l'option dynamique **StringMessage**.|  
  
## Options dynamiques MessageType  
  
### MessageType = Message de fichiers de données  
 **SaveFileAs**  
 Tapez le chemin du fichier à utiliser ou cliquez sur le bouton avec des points de suspension **(…)** et recherchez le fichier.  
  
 **Remplacer**  
 Indiquez si vous voulez remplacer les données dans un fichier existant lors de l'enregistrement du contenu d'un message de fichiers de données. La valeur par défaut est **False**.  
  
 **Filtre**  
 Indiquez si vous voulez appliquer un filtre au message. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Aucun filtre**|La tâche ne filtre pas les messages. Cette valeur affiche l’option dynamique **IdentifierReadOnly**.|  
|**À partir du package**|Le message reçoit uniquement les messages du package spécifié. Cette valeur affiche l’option dynamique **Identifier**.|  
  
### Options dynamiques de filtrage  
  
#### Filtrer = Aucun filtre  
 **IdentifierReadOnly**  
 Cette option est en lecture seule. Elle peut être vide ou contenir le GUID d'un package lorsque la propriété Filtrer a été définie.  
  
#### Filtrer = À partir du package  
 **Identificateur**  
 Si vous choisissez d’appliquer un filtre, tapez l’identificateur unique du package à partir duquel les messages peuvent être reçus, ou cliquez sur le bouton de sélection **(…)** et spécifiez le package.  
  
 **Rubriques connexes :** [Sélectionner un package](../../integration-services/control-flow/select-a-package.md)  
  
### MessageType = Message de type variable  
 **Filtre**  
 Indiquez si vous voulez appliquer un filtre aux messages. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Aucun filtre**|La tâche ne filtre pas les messages. Cette valeur affiche l’option dynamique **IdentifierReadOnly**.|  
|**À partir du package**|Le message reçoit uniquement les messages du package spécifié. Cette valeur affiche l’option dynamique **Identifier**.|  
  
 **Variable**  
 Tapez le nom de la variable ou cliquez sur \<**Nouvelle variable…**>, puis configurez une nouvelle variable.  
  
 **Rubriques connexes :** [Ajouter une variable](../Topic/Add%20Variable.md)  
  
### Options dynamiques de filtrage  
  
#### Filtrer = Aucun filtre  
 **IdentifierReadOnly**  
 Cette option est vide.  
  
#### Filtrer = À partir du package  
 **Identificateur**  
 Si vous choisissez d’appliquer un filtre, tapez l’identificateur unique du package à partir duquel les messages peuvent être reçus, ou cliquez sur le bouton de sélection **(…)** et spécifiez le package.  
  
 **Rubriques connexes :** [Sélectionner un package](../../integration-services/control-flow/select-a-package.md)  
  
### MessageType = Message de type chaîne  
 **Comparer**  
 Indiquez si vous voulez appliquer un filtre aux messages. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Aucun**|Les messages ne sont pas comparés.|  
|**Concordance exacte**|Les messages doivent correspondre exactement à la chaîne figurant dans l’option **CompareString**.|  
|**Ignorer la casse**|Le message doit correspondre à la chaîne figurant dans l’option **CompareString**, mais la comparaison ne tient pas compte de la casse.|  
|**Contenant**|Le message doit contenir la chaîne figurant dans l’option **CompareString**.|  
  
 **CompareString**  
 Si l’option **Comparer** n’est pas définie sur **Aucun**, indiquez la chaîne à laquelle le message doit être comparé.  
  
### MessageType = Message de type chaîne pour la variable  
 **Comparer**  
 Indiquez si vous voulez appliquer un filtre aux messages. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Aucun**|Les messages ne sont pas comparés.|  
|**Concordance exacte**|Le message doit correspondre exactement à la chaîne figurant dans l’option **CompareString**.|  
|**Ignorer la casse**|Le message doit correspondre à la chaîne figurant dans l’option **CompareString**, mais la comparaison ne tient pas compte de la casse.|  
|**Contenant**|Le message doit contenir la chaîne figurant dans l’option **CompareString**.|  
  
 **CompareString**  
 Si l’option **Comparer** n’est pas définie sur **Aucun**, indiquez la chaîne à laquelle le message doit être comparé.  
  
 **Variable**  
 Tapez le nom de la variable qui doit contenir le message reçu ou cliquez sur \<**Nouvelle variable…**>, puis configurez une nouvelle variable.  
  
 **Rubriques connexes :** [Ajouter une variable](../Topic/Add%20Variable.md)  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche MSMQ &#40;page Général&#41;](../../integration-services/control-flow/message-queue-task-editor-general-page.md)   
 [Éditeur de tâche MSMQ &#40;page Envoyer&#41;](../../integration-services/control-flow/message-queue-task-editor-send-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)   
 [Tâche MSMQ](../../integration-services/control-flow/message-queue-task.md)  
  
  