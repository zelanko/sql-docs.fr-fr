---
title: Utilisation des collections | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, collections
- SMO [SQL Server], collections
- collections [SMO]
ms.assetid: 209eb175-2514-4de1-bc32-b2e6a469d945
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3c3f4c31da84c2ca07b948faeba4aed7b93ad011
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70148692"
---
# <a name="using-collections"></a>Utilisation de collections
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Une collection est une liste d'objets construits à partir de la même classe d'objets et qui partagent le même objet parent. L'objet de collection contient toujours le nom du type d'objet avec le suffixe Collection. Par exemple, pour accéder aux colonnes dans une table spécifiée, utilisez le type d'objet <xref:Microsoft.SqlServer.Management.Smo.ColumnCollection>. Il contient tous les objets <xref:Microsoft.SqlServer.Management.Smo.Column> qui appartiennent au même objet <xref:Microsoft.SqlServer.Management.Smo.Table>.  
  
 L'instruction [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] **For...Each** ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] **foreach** peut être utilisée pour parcourir chaque membre de la collection.  
  
## <a name="examples"></a>Exemples  
Pour utiliser un exemple de code qui est fourni, vous devrez choisir l'environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un projet Visual C&#35; Smo dans Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-basic"></a>Référence d'un objet à l'aide d'une collection en Visual Basic  
 Cet exemple de code indique comment définir une propriété de colonne à l'aide des propriétés <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> et <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A>. Ces propriétés représentent des collections, qui peuvent être utilisées pour identifier un objet particulier lorsqu'elles sont utilisées avec un paramètre qui spécifie le nom de l'objet. Le nom et le schéma sont requis pour la propriété d'objet de collection <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Modify a property using the Databases, Tables, and Columns collections to reference a column.
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("ModifiedDate").Nullable = True
'Call the Alter method to make the change on the instance of SQL Server.
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("ModifiedDate").Alter()
```
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-c"></a>Référence d'un objet à l'aide d'une collection en Visual C#  
 Cet exemple de code indique comment définir une propriété de colonne à l'aide des propriétés <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> et <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A>. Ces propriétés représentent des collections, qui peuvent être utilisées pour identifier un objet particulier lorsqu'elles sont utilisées avec un paramètre qui spécifie le nom de l'objet. Le nom et le schéma sont requis pour la propriété d'objet de collection <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>.  
  
```csharp  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Modify a property using the Databases, Tables, and Columns collections to reference a column.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Nullable = true;   
//Call the Alter method to make the change on the instance of SQL Server.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Alter();   
}  
```  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-basic"></a>Parcours des membres d'une collection en Visual Basic  
 Cet exemple de code parcourt la propriété de collection <xref:Microsoft.AnalysisServices.Server.Databases%2A> et affiche toutes les connexions de base de données à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
Dim count As Integer
Dim total As Integer
'Iterate through the databases and call the GetActiveDBConnectionCount method.
Dim db As Database
For Each db In srv.Databases
    count = srv.GetActiveDBConnectionCount(db.Name)
    total = total + count
    'Display the number of connections for each database.
    Console.WriteLine(count & " connections on " & db.Name)
Next
'Display the total number of connections on the instance of SQL Server.
Console.WriteLine("Total connections =" & total)
```
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-c"></a>Parcours des membres d'une collection en Visual C#  
 Cet exemple de code parcourt la propriété de collection <xref:Microsoft.AnalysisServices.Server.Databases%2A> et affiche toutes les connexions de base de données à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```csharp  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
int count = 0;   
int total = 0;   
//Iterate through the databases and call the GetActiveDBConnectionCount method.   
Database db = default(Database);   
foreach ( db in srv.Databases) {   
  count = srv.GetActiveDBConnectionCount(db.Name);   
  total = total + count;   
  //Display the number of connections for each database.   
  Console.WriteLine(count + " connections on " + db.Name);   
}   
//Display the total number of connections on the instance of SQL Server.   
Console.WriteLine("Total connections =" + total);   
}   
```  
  
  
