---
title: "Utilisation de la messagerie de base de données | Documents Microsoft"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- e-mail [SMO]
- Database Mail [SMO]
- mail [SMO]
ms.assetid: 7605390f-b485-48cc-8d97-e364a066067b
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 28082a9c402700a17c7072ed6d7dcd3a87c92bd9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="using-database-mail"></a>Utilisation de la messagerie de base de données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Dans SMO, le sous-système de messagerie de base de données est représenté par le <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> objet qui est référencé par le <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> propriété. En utilisant l'objet SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>, vous pouvez configurer le sous-système de messagerie de base de données et gérer des profils et des comptes de messagerie. SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> objet appartient à la **Server** objet, ce qui signifie que l’étendue des comptes de messagerie est au niveau du serveur.  
  
## <a name="examples"></a>Exemples  
 Pour utiliser un exemple de code qui est fourni, vous devrez choisir l'environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un Visual C &#35; Projet SMO dans Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
 Pour les programmes qui utilisent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] messagerie de base de données, vous devez inclure le **importations** instruction pour qualifier l’espace de noms de messagerie. Insérez l'instruction après les autres instructions **Imports** , avant toute autre déclaration dans l'application, par exemple :  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Mail`  
  
## <a name="creating-a-database-mail-account-by-using-visual-basic"></a>Création d'un compte de messagerie de base de données à l'aide de Visual Basic  
 Cet exemple de code montre comment créer un compte de messagerie dans SMO. La messagerie de base de données est représentée par l'objet <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> et référencée par la propriété <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Server>. SMO peut être utilisé pour configurer la messagerie de base de données par programme, mais il ne permet pas l'envoi ou la réception de courrier électronique.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server()
'Define the Database Mail service with a SqlMail object variable and reference it using the Server Mail property.
Dim sm As SqlMail
sm = srv.Mail
'Define and create a mail account by supplying the Database Mail service, name, description, display name, and email address arguments in the constructor.
Dim a As MailAccount
a = New MailAccount(sm, "AdventureWorks Administrator", "AdventureWorks Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com")
a.Create()
```
  
## <a name="creating-a-database-mail-account-by-using-visual-c"></a>Création d'un compte de messagerie de base de données à l'aide de Visual C#  
 Cet exemple de code montre comment créer un compte de messagerie dans SMO. La messagerie de base de données est représentée par l'objet <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> et référencée par la propriété <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Server>. SMO peut être utilisé pour configurer la messagerie de base de données par programme, mais il ne permet pas l'envoi ou la réception de courrier électronique.  
  
```csharp  
{  
         //Connect to the local, default instance of SQL Server.  
         Server srv = default(Server);   
           srv = new Server();   
           //Define the Database Mail service with a SqlMail object variable   
           //and reference it using the Server Mail property.   
           SqlMail sm;   
           sm = srv.Mail;   
           //Define and create a mail account by supplying the Database Mail  
           //service, name, description, display name, and email address  
           //arguments in the constructor.   
           MailAccount a = default(MailAccount);   
           a = new MailAccount(sm, "AdventureWorks2012 Administrator", "AdventureWorks2012 Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com");   
           a.Create();    
}  
```  
  
## <a name="creating-a-database-mail-account-by-using-powershell"></a>Création d'un compte de messagerie de base de données à l'aide de PowerShell  
 Cet exemple de code montre comment créer un compte de messagerie dans SMO. La messagerie de base de données est représentée par l'objet <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> et référencée par la propriété <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Server>. SMO peut être utilisé pour configurer la messagerie de base de données par programme, mais il ne permet pas l'envoi ou la réception de courrier électronique.  
  
  
  
```powershell  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define the Database Mail; reference it using the Server Mail property.  
$sm = $srv.Mail  
  
#Define and create a mail account by supplying the Database Mail service,  
#name, description, display name, and email address arguments in the constructor.  
$a = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Mail.MailAccount -argumentlist $sm, `  
"Adventure Works Administrator", "Adventure Works Automated Mailer",`  
 "Mail account for administrative e-mail.", "dba@Adventure-Works.com"  
$a.Create()  
```  
  
  
