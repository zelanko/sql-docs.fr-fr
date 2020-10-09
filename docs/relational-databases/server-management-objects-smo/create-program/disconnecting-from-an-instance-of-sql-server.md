---
description: Déconnexion d'une instance de SQL Server
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
ms.openlocfilehash: 2e98180b877fb81c5d32f908a2f8e9cdc131a45a
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91868617"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Déconnexion d'une instance de SQL Server
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Il n'est pas nécessaire de fermer et de déconnecter manuellement des objets SMO ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects). Les connexions sont ouvertes et fermées en fonction des besoins.  
  
## <a name="connection-pooling"></a>Regroupement de connexions  
 Lorsque la méthode [Connect](/previous-versions/sql/sql-server-2014/ms199449(v=sql.120)) est appelée, la connexion n’est pas automatiquement libérée. La méthode [Disconnect](/previous-versions/sql/sql-server-2014/ms199428(v=sql.120)) doit être appelée explicitement pour libérer la connexion au pool de connexions. Vous pouvez également demander une connexion non regroupée. Pour ce faire, définissez la propriété [NonPooledConnection](/previous-versions/sql/sql-server-2014/ms214357(v=sql.120)) de la <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> propriété qui fait référence à l’objet [ServerConnection](/previous-versions/sql/sql-server-2014/ms218641(v=sql.120)) .  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Déconnexion d'une instance de SQL Server pour des objets RMO  
 La fermeture des connexions au serveur lorsque vous programmez avec des objets RMO est légèrement différente de la procédure utilisée avec des objets SMO.  
  
 Étant donné que la connexion au serveur pour un objet RMO est conservée par l’objet [ServerConnection](/previous-versions/sql/sql-server-2014/ms218641(v=sql.120)) , cet objet est également utilisé lors de la déconnexion d’une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lorsque vous programmez à l’aide de RMO. Pour fermer une connexion à l’aide de l’objet [ServerConnection](/previous-versions/sql/sql-server-2014/ms218641(v=sql.120)) , appelez la méthode [Disconnect](/previous-versions/sql/sql-server-2014/ms199428(v=sql.120)) de l’objet RMO. Une fois la connexion fermée, les objets RMO ne peuvent pas être utilisés.  
  
## <a name="example"></a>Exemple  
Pour utiliser un exemple de code qui est fourni, vous devrez choisir l'environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un projet Visual C&#35; Smo dans Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
 
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Fermeture et déconnexion d'un objet SMO en Visual Basic  
 Cet exemple de code montre comment demander une connexion non regroupée en définissant la propriété [NonPooledConnection](/previous-versions/sql/sql-server-2014/ms214357(v=sql.120)) de la propriété de l' <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> objet.  
  
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
 Cet exemple de code montre comment demander une connexion non regroupée en définissant la propriété [NonPooledConnection](/previous-versions/sql/sql-server-2014/ms214357(v=sql.120)) de la propriété de l' <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> objet.  
  
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
 [ServerConnection](/previous-versions/sql/sql-server-2014/ms218641(v=sql.120))  
  
