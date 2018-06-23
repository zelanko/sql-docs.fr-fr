---
title: Utilisation de serveurs liés dans SMO | Documents Microsoft
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
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7ae91209d5786ed976e1c29ed9b51d7d52e0070a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044485"
---
# <a name="using-linked-servers-in-smo"></a>Utilisation de serveurs liés dans SMO
  Un serveur lié représente une source de données OLE DB sur un serveur distant. Les sources de données OLE DB distantes sont liées à l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide de la <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> objet.  
  
 Les serveurs de base de données distante peuvent être liés à l’instance actuelle de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide d’un fournisseur OLE DB. Dans SMO, les serveurs liés sont représentés par le <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> objet. Le <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> propriété fait référence à une collection de <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> objets. Ces derniers stockent les informations d'identification requises pour établir une connexion avec le serveur lié.  
  
## <a name="ole-db-providers"></a>Fournisseurs OLE DB  
 Dans SMO, les fournisseurs OLE DB installés sont représentés par une collection d'objets <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple de code suivant, vous devez sélectionner l'environnement, le modèle et le langage de programmation à utiliser pour créer votre application. Pour plus d’informations, consultez [créer un projet SMO Visual Basic dans Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) et [créer un Visual C&#35; projet SMO dans Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-basic"></a>Création d'un lien vers un serveur de fournisseur OLE DB en Visual Basic  
 L’exemple de code montre comment créer un lien vers une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, source de données hétérogènes à l’aide de la <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> objet. En spécifiant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] comme nom de produit, les données sont accessible sur le serveur lié en utilisant le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client fournisseur OLE DB, qui est le fournisseur OLE DB officiel pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLinkedServers1](SMO How to#SMO_VBLinkedServers1)]  -->  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Création d'un lien vers un serveur de fournisseur OLE DB en Visual C#  
 L’exemple de code montre comment créer un lien vers une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, source de données hétérogènes à l’aide de la <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> objet. En spécifiant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] comme nom de produit, les données sont accessible sur le serveur lié en utilisant le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client fournisseur OLE DB, qui est le fournisseur OLE DB officiel pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
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
 L’exemple de code montre comment créer un lien vers une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB, source de données hétérogènes à l’aide de la <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> objet. En spécifiant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] comme nom de produit, les données sont accessible sur le serveur lié en utilisant le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client fournisseur OLE DB, qui est le fournisseur OLE DB officiel pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -argumentlist $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.   
$lsvr.ProductName = "SQL Server"  
  
#Create the Database Object  
$lsvr.Create()   
```  
  
  