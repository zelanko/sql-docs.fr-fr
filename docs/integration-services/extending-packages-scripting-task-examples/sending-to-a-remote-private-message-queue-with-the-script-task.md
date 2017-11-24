---
title: "Envoi à une file d’attente de messages privée distante à avec la tâche de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting-task-examples
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], remote private message queues
- Message Queue task [Integration Services]
- Script task [Integration Services], examples
ms.assetid: 636314fd-d099-45cd-8bb4-f730d0a06739
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5ab9314ef0825486914d1801bfa2b9613883b43e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="sending-to-a-remote-private-message-queue-with-the-script-task"></a>Envoi vers une file d'attente de messages privée distante à l'aide de la tâche de script
  Message Queuing (également appelé MSMQ) permet aux développeurs de communiquer de façon simple, rapide et fiable avec des programmes d'application par l'envoi et la réception de messages. Une file d'attente de messages peut se trouver sur l'ordinateur local ou un ordinateur distant et être publique ou privée. Dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], le gestionnaire de connexions MSMQ et la tâche MSMQ ne prennent pas en charge l'envoi vers une file d'attente privée située sur un ordinateur distant. Toutefois, la tâche de script permet d'envoyer facilement un message à une file d'attente privée distante.  
  
> [!NOTE]  
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a> Description  
 L’exemple suivant utilise un gestionnaire de connexions MSMQ existant, ainsi que des objets et des méthodes à partir de l’espace de noms System.Messaging pour envoyer le texte contenu dans une variable de package pour une file d’attente de messages privée distante. L’appel à la méthode M:Microsoft.SqlServer.Dts.ManagedConnections.MSMQConn.AcquireConnection(System.Object) du Gestionnaire de connexions MSMQ retourne un **MessageQueue** dont l’objet **envoyer** méthode effectue cette tâche.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Créez un gestionnaire de connexions MSMQ avec le nom par défaut. Définissez le chemin d'accès d'une file d'attente privée distante valide, dans le format suivant :  
  
    ```  
    FORMATNAME:DIRECT=OS:<computername>\private$\<queuename>  
    ```  
  
2.  Créer un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable nommée **MessageText** de type **chaîne** pour transférer le texte du message dans le script. Entrez un message par défaut en tant que valeur de la variable.  
  
3.  Ajoutez une tâche de script à l'aire de conception et modifiez-la. Sur le **Script** onglet de la **éditeur de tâche de Script**, ajouter le `MessageText` variable à la **ReadOnlyVariables** propriété afin de libérer de la variable dans le script.  
  
4.  Cliquez sur **modifier le Script** pour ouvrir le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] outils de l’éditeur de script d’Applications (VSTA).  
  
5.  Ajoutez une référence dans le projet de script pour le **System.Messaging** espace de noms.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Tâche MSMQ](../../integration-services/control-flow/message-queue-task.md)  
  
  

