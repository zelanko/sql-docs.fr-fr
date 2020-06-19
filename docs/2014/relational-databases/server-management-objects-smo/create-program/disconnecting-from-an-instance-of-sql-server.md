---
title: Déconnexion d’une instance de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3430048a52b3dce5e82d6b7af2d6a8162841d062
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063162"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Déconnexion d'une instance de SQL Server
  Il n'est pas nécessaire de fermer et de déconnecter manuellement des objets SMO ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects). Les connexions sont ouvertes et fermées en fonction des besoins.  
  
## <a name="connection-pooling"></a>Regroupement de connexions  
 Lorsque la méthode <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> est appelée, la connexion n'est pas automatiquement libérée. La méthode <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> doit être appelée explicitement pour libérer la connexion au pool de connexions. Vous pouvez également demander une connexion non regroupée. Pour ce faire, vous définissez la propriété <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> de la propriété <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> qui fait référence à l'objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Déconnexion d'une instance de SQL Server pour des objets RMO  
 La fermeture des connexions au serveur lorsque vous programmez avec des objets RMO est légèrement différente de la procédure utilisée avec des objets SMO.  
  
 Étant donné que la connexion au serveur pour un objet RMO est conservée par l' <xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet, cet objet est également utilisé lors de la déconnexion d’une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lorsque vous programmez à l’aide de RMO. Pour fermer une connexion à l'aide de l'objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection>, appelez la méthode <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> de l'objet RMO. Une fois la connexion fermée, les objets RMO ne peuvent pas être utilisés.  
  
## <a name="example"></a>Exemple  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Fermeture et déconnexion d'un objet SMO en Visual Basic  
 Cet exemple de code indique comment demander une connexion non regroupée en définissant la propriété <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> de la propriété de l'objet <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB4](SMO How to#SMO_VB4)]  -->  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Fermeture et déconnexion d'un objet SMO en Visual C#  
 Cet exemple de code indique comment demander une connexion non regroupée en définissant la propriété <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> de la propriété de l'objet <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>.  
  
```  
{   
Server srv;   
srv = new Server();   
//Disable automatic disconnection.   
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect;   
//Connect to the local, default instance of SQL Server.   
srv.ConnectionContext.Connect();   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
//Disconnect explicitly.   
srv.ConnectionContext.Disconnect();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
