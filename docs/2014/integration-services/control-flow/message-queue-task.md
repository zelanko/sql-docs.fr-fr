---
title: Tâches MSMQ | Microsoft Docs
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
- sql12.dts.designer.messagequeuetask.f1
helpviewer_keywords:
- Message Queue task [Integration Services]
- receiving messages
- messages [Integration Services]
- sending messages
ms.assetid: ae1d8fad-6649-4e93-b589-14a32d07da33
caps.latest.revision: 68
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3be2c48f2a3b2dc552d3f9c89bf2caf57b0e0bf4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042957"
---
# <a name="message-queue-task"></a>Message Queue Task
  La tâche MSMQ vous permet d’utiliser Message Queuing (MSMQ) pour envoyer et recevoir des messages entre des packages [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ou pour envoyer des messages à une file d’attente d’application traitée par une application personnalisée. Ces messages peuvent être composés de texte brut, de fichiers ou de variables et leurs valeurs.  
  
 L'utilisation de la tâche MSMQ vous permet de coordonner des opérations à l'échelle de votre entreprise. Les messages peuvent être placés dans la file d'attente et remis ultérieurement si la destination est indisponible ou occupée ; par exemple, la tâche peut mettre en file d'attente les messages destinés à l'ordinateur portable hors connexion des représentants commerciaux, qui reçoivent leurs messages lorsqu'ils se connectent au réseau. Vous pouvez utiliser la tâche MSMQ pour effectuer les opérations suivantes :  
  
-   Retarder l'exécution d'une tâche jusqu'à la validation d'autres packages. Par exemple, sur chacun de vos sites de vente au détail, après une maintenance nocturne, une tâche MSMQ envoie un message à l'ordinateur de l'entreprise. Un package s'exécutant sur cet ordinateur contient des tâches MSMQ, chacune attendant le message d'un site de vente au détail spécifique. Lorsqu'un message d'un site arrive, une tâche télécharge des données à partir de ce site. Une fois tous les sites validés, le package calcule les totaux récapitulatifs.  
  
-   Envoyer des fichiers de données à l'ordinateur qui les traite. Par exemple, le résultat de la caisse enregistreuse d'un restaurant peut être envoyé dans un message de fichier de données au système du paiement des salaires de l'entreprise, où sont extraites les données liées aux pourboires des serveurs.  
  
-   Distribuer des fichiers à l'intérieur de votre entreprise. Par exemple, un package peut utiliser une tâche MSMQ pour envoyer un fichier de package à un autre ordinateur. Un package s'exécutant sur l'ordinateur de destination utilise alors une tâche MSMQ pour récupérer et enregistrer le package localement.  
  
 Lors de l'envoi ou de la réception de messages, la tâche MSMQ utilise l'un des quatre types de messages suivants : fichier de données, chaîne, message de type chaîne pour la variable ou variable. Le type de message « message de type chaîne pour la variable » peut être utilisé uniquement lors de la réception de messages.  
  
 La tâche utilise un gestionnaire de connexions MSMQ pour se connecter à une file d'attente de messages. Pour plus d’informations, consultez [Gestionnaire de connexions MSMQ](../connection-manager/msmq-connection-manager.md). Pour plus d’informations sur Message Queuing (MSMQ), consultez [MSDN Library](http://go.microsoft.com/fwlink/?LinkId=7022).  
  
 La tâche MSMQ exige que le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] soit installé. Parmi les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous pouvez sélectionner dans la page **Composants à installer** ou **Sélection de fonctionnalités** de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , certains n’installent qu’un sous-ensemble partiel des composants [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Ces composants sont utiles pour des tâches spécifiques, mais les fonctionnalités de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] s'en trouvent limitées. Par exemple, l'option [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] installe les composants [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nécessaires pour concevoir un package mais le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n'est pas installé, par conséquent la tâche MSMQ ne fonctionne pas. Pour garantir une installation complète de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous devez sélectionner [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans la page **Composants à installer** . Pour plus d’informations sur l’installation et l’exécution de la tâche MSMQ, consultez [Installer Integration Services](../install-windows/install-integration-services.md).  
  
> [!NOTE]  
>  La tâche MSMQ ne parvient pas à assurer la conformité avec le standard FIPS (Federal Information Processing Standard) 140-2 lorsque le système d'exploitation de l'ordinateur est configuré en mode FIPS et que la tâche utilise le chiffrement. Si la tâche MSMQ n'utilise pas le chiffrement, elle peut s'exécuter correctement.  
  
## <a name="message-types"></a>Types de messages  
 Vous pouvez configurer les types de messages fournis par la tâche MSMQ des manières suivantes :  
  
-   `Data file` message indique qu’un fichier contient le message. Lors de la réception de messages, vous pouvez configurer la tâche de façon à enregistrer le fichier, remplacer un fichier existant et spécifier le package à partir duquel la tâche peut recevoir des messages.  
  
-   `String` message Spécifie le message sous forme de chaîne. Lors de la réception de messages, vous pouvez configurer la tâche de façon à comparer la chaîne reçue avec une chaîne définie par l'utilisateur et exécuter une action en fonction du résultat de la comparaison. La comparaison de chaînes peut être exacte, sensible ou non à la casse, ou utiliser une sous-chaîne.  
  
-   `String message to variable` Spécifie le message source sous forme de chaîne qui est envoyé à une variable de destination. Vous pouvez configurer la tâche de façon à comparer la chaîne reçue avec une chaîne définie par l'utilisateur à l'aide d'une comparaison exacte, non sensible à la casse ou de sous-chaîne. Ce type de message est disponible uniquement lorsque la tâche reçoit des messages.  
  
-   `Variable` Spécifie que le message contienne une ou plusieurs variables. Vous pouvez configurer la tâche de façon à spécifier les noms des variables contenues dans le message. Lors de la réception de messages, vous pouvez configurer la tâche de façon à spécifier à la fois le package à partir duquel elle peut recevoir des messages et la variable qui est la destination du message.  
  
## <a name="sending-messages"></a>sending messages  
 Lorsque vous configurez la tâche MSMQ pour envoyer des messages, vous pouvez utiliser l'un des algorithmes de chiffrement actuellement pris en charge par la technologie Message Queuing, RC2 et RC4, pour chiffrer le message. Ces deux algorithmes de chiffrement sont aujourd'hui considérés comme faibles d'un point de vue du chiffrement par rapport aux algorithmes plus récents, non encore pris en charge par la technologie Microsoft Message Queuing. Par conséquent, vous devez minutieusement évaluer vos besoins en matière de chiffrement si vous souhaitez envoyer des messages à l'aide de la tâche MSMQ.  
  
## <a name="receiving-messages"></a>réception de messages  
 Lors de la réception de messages, la tâche MSMQ peut être configurée des manières suivantes :  
  
-   Contournement du message ou suppression du message de la file d'attente.  
  
-   Spécification d'un délai d'attente.  
  
-   Échec en cas d'expiration du délai d'attente.  
  
-   Remplacement d'un fichier existant si le message est stocké dans un `Data file`.  
  
-   Enregistrer le fichier de message à un autre nom de fichier, si le message utilise le `Data file message` type.  
  
## <a name="custom-logging-messages-available-on-the-message-queue-task"></a>Messages de journalisation personnalisés disponibles dans la tâche MSMQ  
 Le tableau suivant répertorie les entrées de journal personnalisées de la tâche MSMQ. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`MSMQAfterOpen`|Indique que la tâche a fini d'ouvrir la file d'attente des messages.|  
|`MSMQBeforeOpen`|Indique que la tâche a commencé l'ouverture de la file d'attente des messages.|  
|`MSMQBeginReceive`|Indique que la tâche a commencé la réception d'un message.|  
|`MSMQBeginSend`|Indique que la tâche a commencé l'envoi d'un message.|  
|`MSMQEndReceive`|Indique que la tâche a terminé la réception d'un message.|  
|`MSMQEndSend`|Indique que la tâche a terminé l'envoi d'un message.|  
|`MSMQTaskInfo`|Fournit des informations détaillées concernant la tâche.|  
|`MSMQTaskTimeOut`|Indique que le délai de la tâche a expiré.|  
  
## <a name="configuration-of-the-message-queue-task"></a>Configuration de la tâche MSMQ  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation. Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche MSMQ &#40;Page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur de tâche MSMQ &#40;Page de réception&#41;](../message-queue-task-editor-receive-page.md)  
  
-   [Éditeur de tâche MSMQ &#40;envoyer la Page&#41;](../message-queue-task-editor-send-page.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d’informations sur la définition par programmation de ces propriétés, consultez la documentation relative à la classe **Microsoft.SqlServer.Dts.Tasks.MessageQueueTask.MessageQueueTask** dans le Guide du développeur.  
  
## <a name="related-tasks"></a>Related Tasks  
 Pour plus d’informations sur la façon de définir ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](integration-services-tasks.md)   
 [Flux de contrôle](control-flow.md)  
  
  