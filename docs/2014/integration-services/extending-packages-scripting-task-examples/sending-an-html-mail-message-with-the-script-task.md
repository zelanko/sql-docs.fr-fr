---
title: Envoi d’un message électronique HTML à l’aide de la tâche de script | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Send Mail task [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], HTML mail message
ms.assetid: dd2b1eef-b04f-4946-87ab-7bc56bb525ce
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 254f1fcb701fd11b22e35def915b09b537c4b33a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62894988"
---
# <a name="sending-an-html-mail-message-with-the-script-task"></a>Envoi d'un message électronique HTML à l'aide de la tâche de script
  La tâche SendMail de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prend uniquement en charge les messages électroniques au format texte brut. Toutefois, vous pouver envoyer facilement des messages électroniques HTML en utilisant la tâche de script et les fonctionnalités de messagerie du .NET Framework.  
  
> [!NOTE]  
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 L'exemple suivant utilise l'espace de noms `System.Net.Mail` pour configurer et envoyer un message électronique HTML. Le script obtient le destinataire, l'expéditeur, l'objet et le corps du message électronique à partir de variables du package, les utilise pour créer un nouveau `MailMessag`e et définit sa propriété `IsBodyHtml` sur `True`. Ensuite, il obtient le nom du serveur SMTP auprès d'une autre variable du package, initialise une instance de `System.Net.Mail.SmtpClient` et appelle sa méthode `Send` pour envoyer le message HTML. L'exemple encapsule la fonctionnalité d'envoi du message dans une sous-routine susceptible d'être réutilisée dans d'autres scripts.  
  
#### <a name="to-configure-this-script-task-example-without-an-smtp-connection-manager"></a>Pour configurer cet exemple de tâche de script sans gestionnaire de connexions SMTP  
  
1.  Créez des variables chaîne nommées `HtmlEmailTo`, `HtmlEmailFrom` et `HtmlEmailSubject`, puis attribuez-leur des valeurs appropriées à un message de test valide.  
  
2.  Créez une variable chaîne nommée `HtmlEmailBody` et attribuez-lui une chaîne de balise HTML. Par exemple :  
  
    ```  
    <html><body><h1>Testing</h1><p>This is a <b>test</b> message.</p></body></html>  
    ```  
  
3.  Créez une variable chaîne nommée `HtmlEmailServer` et attribuez le nom d'un serveur SMTP disponible qui accepte des messages sortants anonymes.  
  
4.  Attribuez ces cinq variables à la propriété **ReadOnlyVariables** d’une nouvelle tâche de script.  
  
5.  Importez les espaces de noms `System.Net` et `System.Net.Mail` dans votre code.  
  
 L'exemple de code de cette rubrique obtient le nom du serveur SMTP auprès d'une variable du package. Toutefois, vous pourriez également exploiter un gestionnaire de connexions SMTP pour encapsuler les informations de connexion, puis extraire le nom du serveur du gestionnaire de connexions dans votre code. La méthode <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> du gestionnaire de connexions SMTP renvoie une chaîne au format suivant :  
  
 `SmtpServer=smtphost;UseWindowsAuthentication=False;EnableSsl=False;`  
  
 Vous pouvez utiliser la méthode `String.Split` pour séparer cette liste d'arguments en un tableau de chaînes individuelles à chaque point-virgule (;) ou signe égal (=), puis extraire le deuxième argument (indice 1) du tableau en tant que nom du serveur.  
  
#### <a name="to-configure-this-script-task-example-with-an-smtp-connection-manager"></a>Pour configurer cet exemple de tâche de script avec un gestionnaire de connexions SMTP  
  
1.  Modifiez la tâche de script configurée précédemment en supprimant la variable `HtmlEmailServer` de la liste de la propriété **ReadOnlyVariables**.  
  
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
  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Tache Envoyer un message](../control-flow/send-mail-task.md)  
  
  
