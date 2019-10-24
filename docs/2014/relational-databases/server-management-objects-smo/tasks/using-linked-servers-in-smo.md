---
title: Utilisation de serveurs liés dans SMO | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0f62efaa1550ea0b9e68ce4914e4852612d53f48
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72781995"
---
# <a name="using-linked-servers-in-smo"></a>Utilisation de serveurs liés dans SMO
  Un serveur lié représente une source de données OLE DB sur un serveur distant. Les sources de données OLE DB distantes sont liées à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de l'objet <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>.  
  
 Les serveurs de bases de données distants peuvent être liés à l'instance actuelle de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide d'un fournisseur OLE DB. Dans SMO, les serveurs liés sont représentés par l'objet <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. La propriété <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> référence une collection d'objets <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin>. Ces derniers stockent les informations d'identification requises pour établir une connexion avec le serveur lié.  
  
## <a name="ole-db-providers"></a>Fournisseurs OLE DB  
 Dans SMO, les fournisseurs OLE DB installés sont représentés par une collection d'objets <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple de code suivant, vous devez sélectionner l'environnement, le modèle et le langage de programmation à utiliser pour créer votre application. Pour plus d’informations, consultez [créer un projet Visual Basic Smo dans Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) et [créer un projet&#35; Smo Visual C dans Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-basic"></a>Création d'un lien vers un serveur de fournisseur OLE DB en Visual Basic  
 L'exemple de code suivant montre comment créer un lien vers une source de données hétérogènes OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de l'objet <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. En spécifiant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] comme nom de produit, l'accès aux données sur le serveur lié s'effectue en utilisant le fournisseur OLE DB [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client, qui est le fournisseur OLE DB officiel pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLinkedServers1](SMO How to#SMO_VBLinkedServers1)]  -->  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Création d'un lien vers un serveur de fournisseur OLE DB en Visual C#  
 L'exemple de code suivant montre comment créer un lien vers une source de données hétérogènes OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de l'objet <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. En spécifiant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] comme nom de produit, l'accès aux données sur le serveur lié s'effectue en utilisant le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client, qui est le fournisseur OLE DB officiel pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```csharp
//Connect to the local, default instance of SQL Server.   
{   
   Server srv = new Server();   
   //Create a linked server.   
   LinkedServer lsrv = default(LinkedServer);   
   lsrv = new LinkedServer(srv, "OLEDBSRV");   
   //When the product name is SQL Server the remaining properties are   
   //not required to be set.   
   lsrv.ProductName = "SQL Server";   
   lsrv.Create();   
}   
```  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-powershell"></a>Création d'un lien vers un serveur de fournisseur OLE DB dans PowerShell  
 L'exemple de code suivant montre comment créer un lien vers une source de données hétérogènes OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de l'objet <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. En spécifiant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] comme nom de produit, l'accès aux données sur le serveur lié s'effectue en utilisant le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client, qui est le fournisseur OLE DB officiel pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```powershell
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -ArgumentList $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.
$lsvr.ProductName = "SQL Server"
  
#Create the Database Object  
$lsvr.Create()
```  
