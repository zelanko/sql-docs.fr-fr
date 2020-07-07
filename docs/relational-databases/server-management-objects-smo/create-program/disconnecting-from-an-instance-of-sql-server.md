---
title: Déconnexion d’une instance de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1b7d361ab7648c4cc196aaf9ee2d7be88d980e4d
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006373"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Déconnexion d'une instance de SQL Server
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Il n'est pas nécessaire de fermer et de déconnecter manuellement des objets SMO ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects). Les connexions sont ouvertes et fermées en fonction des besoins.  
  
## <a name="connection-pooling"></a>Regroupement de connexions  
 Lorsque la méthode [Connect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.connect) est appelée, la connexion n’est pas automatiquement libérée. La méthode [Disconnect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) doit être appelée explicitement pour libérer la connexion au pool de connexions. Vous pouvez également demander une connexion non regroupée. Pour ce faire, définissez la propriété [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) de la <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> propriété qui fait référence à l’objet [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) .  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Déconnexion d'une instance de SQL Server pour des objets RMO  
 La fermeture des connexions au serveur lorsque vous programmez avec des objets RMO est légèrement différente de la procédure utilisée avec des objets SMO.  
  
 Étant donné que la connexion au serveur pour un objet RMO est conservée par l’objet [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) , cet objet est également utilisé lors de la déconnexion d’une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lorsque vous programmez à l’aide de RMO. Pour fermer une connexion à l’aide de l’objet [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) , appelez la méthode [Disconnect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) de l’objet RMO. Une fois la connexion fermée, les objets RMO ne peuvent pas être utilisés.  
  
## <a name="example"></a>Exemple  
Pour utiliser un exemple de code qui est fourni, vous devrez choisir l'environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un projet Visual C&#35; Smo dans Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
 
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Fermeture et déconnexion d'un objet SMO en Visual Basic  
 Cet exemple de code montre comment demander une connexion non regroupée en définissant la propriété [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) de la propriété de l' <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> objet.  
  
```VBNET
Dim srv As Server
srv = New Server
'Disable automatic disconnection.
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect
'Connect to the local, default instance of SQL Server.
srv.ConnectionContext.Connect()
'The actual connection is made when a property is retrieved.
Console.WriteLine(srv.Information.Version)
'Disconnect explicitly.
srv.ConnectionContext.Disconnect()
```
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Fermeture et déconnexion d'un objet SMO en Visual C#  
 Cet exemple de code montre comment demander une connexion non regroupée en définissant la propriété [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) de la propriété de l' <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> objet.  
  
```csharp  
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
 [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)  
  
  
