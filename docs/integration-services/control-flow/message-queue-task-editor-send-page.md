---
title: "Éditeur de tâche MSMQ (Page Envoyer) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.msgqueuetask.send.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 565aa079-ac44-4407-8efc-cddab839de30
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d0914b6ab2222fa91d7db229970b081d4a43314d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="message-queue-task-editor-send-page"></a>Éditeur de tâche MSMQ (page Envoyer)
  Utilisez la page **Envoyer** de la boîte de dialogue **Éditeur de tâche MSMQ** pour configurer une tâche MSMQ afin d'envoyer des messages depuis un package [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Pour en savoir plus sur cette tâche, consultez [Message Queue Task](../../integration-services/control-flow/message-queue-task.md).  
  
## <a name="options"></a>Options  
 **UseEncryption**  
 Indiquez si le message doit être chiffré. La valeur par défaut est **False**.  
  
 **EncryptionAlgorithm**  
 Si vous utilisez le chiffrement, définissez le nom de l'algorithme de chiffrement à utiliser. La tâche MSMQ peut utiliser les algorithmes RC2 et RC4. La valeur par défaut est **RC2**.  
  
> [!NOTE]  
>  L'algorithme RC4 est uniquement pris en charge pour des raisons de compatibilité descendante. Le nouveau matériel ne peut être chiffré à l'aide de RC4 ou de RC4_128 que lorsque la base de données se trouve dans le niveau de compatibilité 90 ou 100. (Non recommandé.) Utilisez à la place un algorithme plus récent, tel qu'un des algorithmes AES. Dans la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le matériel chiffré à l'aide de RC4 ou de RC4_128 peut être déchiffré dans n'importe quel niveau de compatibilité.  
  
> [!IMPORTANT]  
>  Il s'agit des algorithmes de chiffrement que la technologie Message Queuing (ou MSMQ) prend en charge. Ces deux algorithmes de chiffrement sont aujourd'hui considérés comme faibles du point de vue du chiffrement par rapport aux algorithmes plus récents, non encore pris en charge par la technologie Microsoft Message Queuing. Par conséquent, vous devez minutieusement évaluer vos besoins en matière de chiffrement si vous souhaitez envoyer des messages à l'aide de la tâche MSMQ.  
  
 **MessageType**  
 Sélectionnez le type de message : Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Message de fichiers de données**|Le message est stocké dans un fichier. La sélection de cette valeur affiche l'option dynamique **DataFileMessage**.|  
|**Message de type variable**|Le message est stocké dans une variable. Cette valeur affiche l'option dynamique **VariableMessage**.|  
|**Message de type chaîne**|Le message est stocké dans la tâche MSMQ. Cette valeur affiche l'option dynamique **StringMessage**.|  
  
## <a name="messagetype-dynamic-options"></a>Options dynamiques MessageType  
  
### <a name="messagetype--data-file-message"></a>MessageType = Message de fichiers de données  
 **DataFileMessage**  
 Tapez le chemin du fichier de données ou cliquez sur le bouton avec les points de suspension **(…)** et recherchez le fichier.  
  
### <a name="messagetype--variable-message"></a>MessageType = Message de type variable  
 **VariableMessage**  
 Tapez les noms de variables ou cliquez sur les points de suspension **(…)** et sélectionnez les variables. Les variables sont séparées par des virgules.  
  
 **Rubriques connexes :** Sélectionner des variables  
  
### <a name="messagetype--string-message"></a>MessageType = Message de type chaîne  
 **StringMessage**  
 Tapez le message de type chaîne ou cliquez sur les points de suspension **(…)** et entrez le message dans la boîte de dialogue **Entrer le message de type chaîne** .  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche MSMQ &#40; Page Général &#41;](../../integration-services/control-flow/message-queue-task-editor-general-page.md)   
 [Éditeur de tâche MSMQ &#40; Réception Page &#41;](../../integration-services/control-flow/message-queue-task-editor-receive-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
  
