---
title: Gestion des utilisateurs, rôles et connexions | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- logins [SMO]
- roles [SMO]
- users [SMO]
ms.assetid: 74e411fa-74ed-49ec-ab58-68c250f2280e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9bac188dcc6eb26c1bca77ec292a096f4eac2f35
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63226179"
---
# <a name="managing-users-roles-and-logins"></a>Gestion des utilisateurs, rôles et connexions
  Dans SMO, les connexions sont représentées par l'objet <xref:Microsoft.SqlServer.Management.Smo.Login>. Lorsque la connexion existe dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], elle peut être ajoutée à un rôle serveur. Le rôle de serveur est représenté par l'objet <xref:Microsoft.SqlServer.Management.Smo.ServerRole>. Le rôle de base de données est représenté par l'objet <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> et le rôle d'application est représenté par l'objet <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole>.  
  
 Les privilèges associés au niveau serveur sont répertoriés sous la forme de propriétés de l'objet <xref:Microsoft.SqlServer.Management.Smo.ServerPermission>. Les privilèges au niveau serveur peuvent être accordés, refusés ou révoqués pour les comptes d'ouverture de session individuels.  
  
 Chaque objet <xref:Microsoft.SqlServer.Management.Smo.Database> a un objet <xref:Microsoft.SqlServer.Management.Smo.UserCollection> qui spécifie tous les utilisateurs de la base de données. Chaque utilisateur est associé à une ouverture de session. Une ouverture de session peut être associée à plusieurs utilisateurs d'une base de données. La méthode <xref:Microsoft.SqlServer.Management.Smo.Login> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> peut être utilisée pour répertorier tous les utilisateurs dans chaque base de données associée à l'ouverture de session. Ou bien, la propriété <xref:Microsoft.SqlServer.Management.Smo.User> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Login> spécifie l'ouverture de session qui est associée à l'utilisateur.  
  
 Les bases de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ont également des rôles qui spécifient un jeu de privilèges de niveau base de données qui permettent à un utilisateur d'effectuer des tâches spécifiques. Contrairement aux rôles de serveur, les rôles de base de données ne sont pas fixes. Ils peuvent être créés, modifiés et supprimés. Les privilèges et utilisateurs peuvent être attribués à un rôle de base de données pour une administration en masse.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple de code suivant, vous devez sélectionner l'environnement, le modèle et le langage de programmation à utiliser pour créer votre application. Pour plus d’informations, consultez [créer un projet SMO Visual Basic dans Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) et [créer un Visual C&#35; projet SMO dans Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="enumerating-logins-and-associated-users-in-visual-basic"></a>Énumération des connexions et des utilisateurs associés en Visual Basic  
 Chaque utilisateur d'une base de données est associé à une ouverture de session. L'ouverture de session peut être associée à plusieurs utilisateurs dans plusieurs bases de données. L'exemple de code montre comment appeler la méthode <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Login> pour répertorier tous les utilisateurs de la base de données qui sont associés à l'ouverture de session. L'exemple crée une ouverture de session et un utilisateur dans la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] pour garantir la présence d'informations de mappage à énumérer.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLogins1](SMO How to#SMO_VBLogins1)]  -->  
  
## <a name="enumerating-logins-and-associated-users-in-visual-c"></a>Énumération des connexions et des utilisateurs associés en Visual C#  
 Chaque utilisateur d'une base de données est associé à une ouverture de session. L'ouverture de session peut être associée à plusieurs utilisateurs dans plusieurs bases de données. L'exemple de code montre comment appeler la méthode <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Login> pour répertorier tous les utilisateurs de la base de données qui sont associés à l'ouverture de session. L'exemple crée une ouverture de session et un utilisateur dans la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] pour garantir la présence d'informations de mappage à énumérer.  
  
```  
{   
Server srv = new Server();   
//Iterate through each database and display.   
  
foreach ( Database db in srv.Databases) {   
   Console.WriteLine("========");   
   Console.WriteLine("Login Mappings for the database: " + db.Name);   
   Console.WriteLine(" ");   
   //Run the EnumLoginMappings method and return details of database user-login mappings to a DataTable object variable.   
   DataTable d;  
   d = db.EnumLoginMappings();   
   //Display the mapping information.   
   foreach (DataRow r in d.Rows) {   
      foreach (DataColumn c in r.Table.Columns) {   
         Console.WriteLine(c.ColumnName + " = " + r[c]);   
      }   
      Console.WriteLine(" ");   
   }   
}   
}  
```  
  
## <a name="enumerating-logins-and-associated-users-in-powershell"></a>Énumération des connexions et des utilisateurs associés dans PowerShell  
 Chaque utilisateur d'une base de données est associé à une ouverture de session. L'ouverture de session peut être associée à plusieurs utilisateurs dans plusieurs bases de données. L'exemple de code montre comment appeler la méthode <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Login> pour répertorier tous les utilisateurs de la base de données qui sont associés à l'ouverture de session. L'exemple crée une ouverture de session et un utilisateur dans la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] pour garantir la présence d'informations de mappage à énumérer.  
  
```  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\Default\Databases  
  
#Iterate through all databases  
 foreach ($db in Get-ChildItem)  
 {  
 "====="  
 "Login Mappings for the database: "+ $db.Name  
  
 #get the datatable containing the mapping from the smo database oject  
 $dt = $db.EnumLoginMappings()  
  
 #display the results  
 foreach($row in $dt.Rows)  
     {  
        foreach($col in $row.Table.Columns)  
      {  
        $col.ColumnName + "=" + $row[$col]  
       }  
  
     }  
 }  
```  
  
## <a name="managing-roles-and-users"></a>Gestion des rôles et des utilisateurs  
 Cet exemple montre comment gérer les rôles et les utilisateurs. Le premier exemple utilise C#, et le second Visual Basic. Ces exemples doivent référencer les assemblys suivants :  
  
-   Microsoft.SqlServer.Smo.dll  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
-   Microsoft.SqlServer.ConnectionInfo.dll  
  
-   Microsoft.SqlServer.SqlEnum.dll  
  
```  
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
public class A {  
   public static void Main() {  
      Server svr = new Server();  
      Database db = new Database(svr, "TESTDB");  
      db.Create();  
  
      // Creating Logins  
      Login login = new Login(svr, "Login1");  
      login.LoginType = LoginType.SqlLogin;  
      login.Create("password@1");  
  
      Login login2 = new Login(svr, "Login2");  
      login2.LoginType = LoginType.SqlLogin;  
      login2.Create("password@1");  
  
      // Creating Users in the database for the logins created  
      User user1 = new User(db, "User1");  
      user1.Login = "Login1";  
      user1.Create();  
  
      User user2 = new User(db, "User2");  
      user2.Login = "Login2";  
      user2.Create();  
  
      // Creating database permission Sets  
      DatabasePermissionSet dbPermSet = new DatabasePermissionSet(DatabasePermission.AlterAnySchema);  
      dbPermSet.Add(DatabasePermission.AlterAnyUser);  
  
      DatabasePermissionSet dbPermSet2 = new DatabasePermissionSet(DatabasePermission.CreateType);  
      dbPermSet2.Add(DatabasePermission.CreateSchema);  
      dbPermSet2.Add(DatabasePermission.CreateTable);  
  
      // Creating Database roles  
      DatabaseRole role1 = new DatabaseRole(db, "Role1");  
      role1.Create();  
  
      DatabaseRole role2 = new DatabaseRole(db, "Role2");  
      role2.Create();  
  
      // Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name);  
      db.Grant(dbPermSet2, role2.Name);  
  
      // Adding members (Users / Roles) to Role  
      role1.AddMember("User1");  
  
      role2.AddMember("User2");  
  
      // Role1 becomes a member of Role2  
      role2.AddMember("Role1");  
  
      // Enumerating through explicit permissions granted to Role1  
      // enumerates all database permissions for the Grantee  
      DatabasePermissionInfo[] dbPermsRole1 = db.EnumDatabasePermissions("Role1");     
      foreach (DatabasePermissionInfo dbp in dbPermsRole1) {  
         Console.WriteLine(dbp.Grantee + " has " + dbp.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine(" ");  
   }  
}  
```  
  
 Version Visual Basic :  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
  
Public Class A  
   Public Shared Sub Main()  
      Dim svr As New Server()  
      Dim db As New Database(svr, "TESTDB")  
      db.Create()  
  
      ' Creating Logins  
      Dim login As New Login(svr, "Login1")  
      login.LoginType = LoginType.SqlLogin  
      login.Create("password@1")  
  
      Dim login2 As New Login(svr, "Login2")  
      login2.LoginType = LoginType.SqlLogin  
      login2.Create("password@1")  
  
      ' Creating Users in the database for the logins created  
      Dim user1 As New User(db, "User1")  
      user1.Login = "Login1"  
      user1.Create()  
  
      Dim user2 As New User(db, "User2")  
      user2.Login = "Login2"  
      user2.Create()  
  
      ' Creating database permission Sets  
      Dim dbPermSet As New DatabasePermissionSet(DatabasePermission.AlterAnySchema)  
      dbPermSet.Add(DatabasePermission.AlterAnyUser)  
  
      Dim dbPermSet2 As New DatabasePermissionSet(DatabasePermission.CreateType)  
      dbPermSet2.Add(DatabasePermission.CreateSchema)  
      dbPermSet2.Add(DatabasePermission.CreateTable)  
  
      ' Creating Database roles  
      Dim role1 As New DatabaseRole(db, "Role1")  
      role1.Create()  
  
      Dim role2 As New DatabaseRole(db, "Role2")  
      role2.Create()  
  
      ' Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name)  
      db.Grant(dbPermSet2, role2.Name)  
  
      ' Adding members (Users / Roles) to Role  
      role1.AddMember("User1")  
  
      role2.AddMember("User2")  
  
      ' Role1 becomes a member of Role2  
      role2.AddMember("Role1")  
  
      ' Enumerating through explicit permissions granted to Role1  
      ' enumerates all database permissions for the Grantee  
      Dim dbPermsRole1 As DatabasePermissionInfo() = db.EnumDatabasePermissions("Role1")  
      For Each dbp As DatabasePermissionInfo In dbPermsRole1  
         Console.WriteLine(dbp.Grantee + " has " & dbp.PermissionType.ToString() & " permission.")  
      Next  
      Console.WriteLine(" ")  
   End Sub  
End Class  
```  
  
  
