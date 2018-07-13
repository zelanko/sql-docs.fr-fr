---
title: Utilisation de la messagerie de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- e-mail [SMO]
- Database Mail [SMO]
- mail [SMO]
ms.assetid: 7605390f-b485-48cc-8d97-e364a066067b
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: df48338975af6de44979a9169ecad35321dd1fa1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278719"
---
# <a name="using-database-mail"></a>Utilisation de la messagerie de base de données
  Dans SMO, le sous-système de la messagerie de base de données est représentée par l'objet <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> qui est référencé par la propriété <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A>. En utilisant l'objet SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>, vous pouvez configurer le sous-système de messagerie de base de données et gérer des profils et des comptes de messagerie. SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> objet appartient à la `Server` objet, ce qui signifie que l’étendue des comptes de messagerie est au niveau du serveur.  
  
## <a name="examples"></a>Exemples  
 Pour utiliser un exemple de code qui est fourni, vous devrez choisir l'environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un projet SMO Visual Basic dans Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) ou [créer un Visual C&#35; projet SMO dans Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
 Pour les programmes qui utilisent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] messagerie de base de données, vous devez inclure la `Imports` instruction pour qualifier l’espace de noms de messagerie. Insérez l'instruction après les autres instructions `Imports`, avant toute autre déclaration dans l'application, par exemple :  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Mail`  
  
## <a name="creating-a-database-mail-account-by-using-visual-basic"></a>Création d'un compte de messagerie de base de données à l'aide de Visual Basic  
 Cet exemple de code montre comment créer un compte de messagerie dans SMO. La messagerie de base de données est représentée par l'objet <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> et référencée par la propriété <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Server>. SMO peut être utilisé pour configurer la messagerie de base de données par programme, mais il ne permet pas l'envoi ou la réception de courrier électronique.  
  
 VB.NET  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMail1](SMO How to#SMO_VBMail1)]  -->  
  
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
  
 PowerShell  
  
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
  
  
