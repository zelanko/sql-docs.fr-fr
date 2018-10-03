---
title: Envoi vers une file d’attente de messages privée distante à l’aide de la tâche de script | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], remote private message queues
- Message Queue task [Integration Services]
- Script task [Integration Services], examples
ms.assetid: 636314fd-d099-45cd-8bb4-f730d0a06739
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8e595c437df054bfff996c864fe687818ea9d467
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48156809"
---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a>Envoi vers une file d'attente de messages privée distante à l'aide de la tâche de script
  Message Queuing (également appelé MSMQ) permet aux développeurs de communiquer de façon simple, rapide et fiable avec des programmes d'application par l'envoi et la réception de messages. Une file d'attente de messages peut se trouver sur l'ordinateur local ou un ordinateur distant et être publique ou privée. Dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], le gestionnaire de connexions MSMQ et la tâche MSMQ ne prennent pas en charge l'envoi vers une file d'attente privée située sur un ordinateur distant. Toutefois, la tâche de script permet d'envoyer facilement un message à une file d'attente privée distante.  
  
> [!NOTE]  
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 L’exemple suivant utilise un gestionnaire de connexions MSMQ existant, avec des objets et des méthodes de l’espace de noms System.Messaging, pour envoyer le texte contenu dans une variable de package à une file d’attente de messages privée distante. L’appel à la méthode M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection(System.Object) du Gestionnaire de connexions MSMQ retourne un **MessageQueue** de l’objet dont la propriété `Send` pour cela, méthode tâche.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Créez un gestionnaire de connexions MSMQ avec le nom par défaut. Définissez le chemin d'accès d'une file d'attente privée distante valide, dans le format suivant :  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  Créer un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable nommée **MessageText** de type `String` pour transmettre le texte du message dans le script. Entrez un message par défaut en tant que valeur de la variable.  
  
3.  Ajoutez une tâche de script à l'aire de conception et modifiez-la. Sous l’onglet **Script** de l’**Éditeur de tâche de script**, ajoutez la variable `MessageText` à la propriété **ReadOnlyVariables** pour rendre la variable disponible dans le script.  
  
4.  Cliquez sur **Modifier le script** pour ouvrir l’éditeur de script [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).  
  
5.  Dans le projet de script, ajoutez une référence à l'espace de noms `System.Messaging`.  
  
6.  Remplacez le contenu de la fenêtre de script par le code dans la section suivante.  
  
## <a name="code"></a>Code  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Messaging  
  
Public Class ScriptMain  
  
    Public Sub Main()  
  
        Dim remotePrivateQueue As MessageQueue  
        Dim messageText As String  
  
        remotePrivateQueue = _  
            DirectCast(Dts.Connections("Message Queue Connection Manager").AcquireConnection(Dts.Transaction), _  
            MessageQueue)  
        messageText = DirectCast(Dts.Variables("MessageText").Value, String)  
        remotePrivateQueue.Send(messageText)  
  
        Dts.TaskResult = ScriptResults.Success  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Messaging;  
  
public class ScriptMain  
{  
  
    public void Main()  
        {  
  
            MessageQueue remotePrivateQueue = new MessageQueue();  
            string messageText;  
  
            remotePrivateQueue = (MessageQueue)(Dts.Connections["Message Queue Connection Manager"].AcquireConnection(Dts.Transaction) as MessageQueue);  
            messageText = (string)(Dts.Variables["MessageText"].Value);  
            remotePrivateQueue.Send(messageText);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
```  
  
![Icône Integration Services (petite)](../media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services** <br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche MSMQ](../control-flow/message-queue-task.md)  
  
  
