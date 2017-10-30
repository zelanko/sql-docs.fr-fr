---
title: "Envoi d’un Message électronique HTML avec la tâche de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Send Mail task [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], HTML mail message
ms.assetid: dd2b1eef-b04f-4946-87ab-7bc56bb525ce
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: b5f50a79ca83243ea130c77a0d95ab402ba2d31a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="sending-an-html-mail-message-with-the-script-task"></a>Envoi d'un message électronique HTML à l'aide de la tâche de script
  La tâche SendMail de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prend uniquement en charge les messages électroniques au format texte brut. Toutefois, vous pouver envoyer facilement des messages électroniques HTML en utilisant la tâche de script et les fonctionnalités de messagerie du .NET Framework.  
  
> [!NOTE]  
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a> Description  
 L’exemple suivant utilise le **System.Net.Mail** espace de noms pour configurer et envoyer un message électronique HTML. Le script obtient To, à partir d’un objet et le corps du message électronique à partir de variables de package, les utilise pour créer un nouveau **MailMessag**e et définit son **IsBodyHtml** propriété **True**. Ensuite, il obtient le nom du serveur SMTP à partir d’une autre variable de package, initialise une instance de **System.Net.Mail.SmtpClient**et appelle son **envoyer** méthode pour envoyer le message au format HTML. L'exemple encapsule la fonctionnalité d'envoi du message dans une sous-routine susceptible d'être réutilisée dans d'autres scripts.  
  
#### <a name="to-configure-this-script-task-example-without-an-smtp-connection-manager"></a>Pour configurer cet exemple de tâche de script sans gestionnaire de connexions SMTP  
  
1.  Créez des variables chaîne nommées `HtmlEmailTo`, `HtmlEmailFrom` et `HtmlEmailSubject`, puis attribuez-leur des valeurs appropriées à un message de test valide.  
  
2.  Créez une variable chaîne nommée `HtmlEmailBody` et attribuez-lui une chaîne de balise HTML. Exemple :  
  
    ```  
    <html><body><h1>Testing</h1><p>This is a <b>test</b> message.</p></body></html>  
    ```  
  
3.  Créez une variable chaîne nommée `HtmlEmailServer` et attribuez le nom d'un serveur SMTP disponible qui accepte des messages sortants anonymes.  
  
4.  Les cinq de ces variables pour affecter le **ReadOnlyVariables** propriété d’une nouvelle tâche de Script.  
  
5.  Importer le **System.Net** et **System.Net.Mail** espaces de noms dans votre code.  
  
 L'exemple de code de cette rubrique obtient le nom du serveur SMTP auprès d'une variable du package. Toutefois, vous pourriez également exploiter un gestionnaire de connexions SMTP pour encapsuler les informations de connexion, puis extraire le nom du serveur du gestionnaire de connexions dans votre code. La méthode <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> du gestionnaire de connexions SMTP renvoie une chaîne au format suivant :  
  
 `SmtpServer=smtphost;UseWindowsAuthentication=False;EnableSsl=False;`  
  
 Vous pouvez utiliser la **String.Split** méthode pour séparer cette liste d’arguments dans un tableau de chaînes individuelles à chaque point-virgule ( ;) ou égale à signe (=), puis extraire le deuxième argument (indice 1) à partir du tableau en tant que le nom du serveur.  
  
#### <a name="to-configure-this-script-task-example-with-an-smtp-connection-manager"></a>Pour configurer cet exemple de tâche de script avec un gestionnaire de connexions SMTP  
  
1.  Modifier la tâche de Script configurée précédemment en supprimant le `HtmlEmailServer` variable dans la liste des **ReadOnlyVariables**.  
  
2.  Remplacez la ligne de code qui obtient le nom du serveur :  
  
    ```  
    Dim smtpServer As String = _  
      Dts.Variables("HtmlEmailServer").Value.ToString  
    ```  
  
     par les lignes suivantes :  
  
    ```  
    Dim smtpConnectionString As String = _  
      DirectCast(Dts.Connections("SMTP Connection Manager").AcquireConnection(Dts.Transaction), String)  
    Dim smtpServer As String = _  
      smtpConnectionString.Split(New Char() {"="c, ";"c})(1)  
    ```  
  
## <a name="code"></a>Code  
  
```vb  
Public Sub Main()  
  
  Dim htmlMessageTo As String = _  
    Dts.Variables("HtmlEmailTo").Value.ToString  
  Dim htmlMessageFrom As String = _  
    Dts.Variables("HtmlEmailFrom").Value.ToString  
  Dim htmlMessageSubject As String = _  
    Dts.Variables("HtmlEmailSubject").Value.ToString  
  Dim htmlMessageBody As String = _  
    Dts.Variables("HtmlEmailBody").Value.ToString  
  Dim smtpServer As String = _  
    Dts.Variables("HtmlEmailServer").Value.ToString  
  
  SendMailMessage( _  
      htmlMessageTo, htmlMessageFrom, _  
      htmlMessageSubject, htmlMessageBody, _  
      True, smtpServer)  
  
  Dts.TaskResult = ScriptResults.Success  
  
End Sub  
  
Private Sub SendMailMessage( _  
    ByVal SendTo As String, ByVal From As String, _  
    ByVal Subject As String, ByVal Body As String, _  
    ByVal IsBodyHtml As Boolean, ByVal Server As String)  
  
  Dim htmlMessage As MailMessage  
  Dim mySmtpClient As SmtpClient  
  
  htmlMessage = New MailMessage( _  
    SendTo, From, Subject, Body)  
  htmlMessage.IsBodyHtml = IsBodyHtml  
  
  mySmtpClient = New SmtpClient(Server)  
  mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials  
  mySmtpClient.Send(htmlMessage)  
  
End Sub  
```  
  
```csharp  
public void Main()  
        {  
  
            string htmlMessageTo = Dts.Variables["HtmlEmailTo"].Value.ToString();  
            string htmlMessageFrom = Dts.Variables["HtmlEmailFrom"].Value.ToString();  
            string htmlMessageSubject = Dts.Variables["HtmlEmailSubject"].Value.ToString();  
            string htmlMessageBody = Dts.Variables["HtmlEmailBody"].Value.ToString();  
            string smtpServer = Dts.Variables["HtmlEmailServer"].Value.ToString();  
  
            SendMailMessage(htmlMessageTo, htmlMessageFrom, htmlMessageSubject, htmlMessageBody, true, smtpServer);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
        private void SendMailMessage(string SendTo, string From, string Subject, string Body, bool IsBodyHtml, string Server)  
        {  
  
            MailMessage htmlMessage;  
            SmtpClient mySmtpClient;  
  
            htmlMessage = new MailMessage(SendTo, From, Subject, Body);  
            htmlMessage.IsBodyHtml = IsBodyHtml;  
  
            mySmtpClient = new SmtpClient(Server);  
            mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials;  
            mySmtpClient.Send(htmlMessage);  
  
        }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche Envoyer un message](../../integration-services/control-flow/send-mail-task.md)  
  
  

