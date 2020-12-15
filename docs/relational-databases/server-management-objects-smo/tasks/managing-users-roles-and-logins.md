---
description: Gestion des utilisateurs, rôles et connexions
title: Gestion des utilisateurs, rôles et connexions
ms.custom: seo-dt-2019
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- logins [SMO]
- roles [SMO]
- users [SMO]
ms.assetid: 74e411fa-74ed-49ec-ab58-68c250f2280e
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 365d9ef4654ad196f8d43de3b491c6d810d169e8
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475510"
---
# <a name="managing-users-roles-and-logins"></a>Gestion des utilisateurs, rôles et connexions
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Dans SMO, les connexions sont représentées par l'objet <xref:Microsoft.SqlServer.Management.Smo.Login>. Lorsque la connexion existe dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], elle peut être ajoutée à un rôle serveur. Le rôle de serveur est représenté par l'objet <xref:Microsoft.SqlServer.Management.Smo.ServerRole>. Le rôle de base de données est représenté par l'objet <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> et le rôle d'application est représenté par l'objet <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole>.  
  
 Les privilèges associés au niveau serveur sont répertoriés sous la forme de propriétés de l'objet <xref:Microsoft.SqlServer.Management.Smo.ServerPermission>. Les privilèges au niveau serveur peuvent être accordés, refusés ou révoqués pour les comptes d'ouverture de session individuels.  
  
 Chaque objet <xref:Microsoft.SqlServer.Management.Smo.Database> a un objet <xref:Microsoft.SqlServer.Management.Smo.UserCollection> qui spécifie tous les utilisateurs de la base de données. Chaque utilisateur est associé à une ouverture de session. Une ouverture de session peut être associée à plusieurs utilisateurs d'une base de données. La méthode <xref:Microsoft.SqlServer.Management.Smo.Login> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> peut être utilisée pour répertorier tous les utilisateurs dans chaque base de données associée à l'ouverture de session. Ou bien, la propriété <xref:Microsoft.SqlServer.Management.Smo.User> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Login> spécifie l'ouverture de session qui est associée à l'utilisateur.  
  
 Les bases de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ont également des rôles qui spécifient un jeu de privilèges de niveau base de données qui permettent à un utilisateur d'effectuer des tâches spécifiques. Contrairement aux rôles de serveur, les rôles de base de données ne sont pas fixes. Ils peuvent être créés, modifiés et supprimés. Les privilèges et utilisateurs peuvent être attribués à un rôle de base de données pour une administration en masse.  
  
## <a name="example"></a>Exemple  
 Dans les exemples de code suivants, vous devez sélectionner l'environnement, le modèle et le langage de programmation à utiliser pour créer votre application. Pour plus d’informations, consultez [créer un projet Visual C&#35; Smo dans Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="enumerating-logins-and-associated-users-in-visual-c"></a>Énumération des connexions et des utilisateurs associés en Visual C#  
 Chaque utilisateur d'une base de données est associé à une ouverture de session. L'ouverture de session peut être associée à plusieurs utilisateurs dans plusieurs bases de données. L'exemple de code montre comment appeler la méthode <xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Login> pour répertorier tous les utilisateurs de la base de données qui sont associés à l'ouverture de session. L'exemple crée une ouverture de session et un utilisateur dans la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] pour garantir la présence d'informations de mappage à énumérer.  
  
```csharp  
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
  
```powershell  
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
 Cet exemple montre comment gérer les rôles et les utilisateurs. Pour exécuter cet exemple, vous devez référencer les assemblys suivants :  
  
-   Microsoft.SqlServer.Smo.dll  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
-   Microsoft.SqlServer.ConnectionInfo.dll  
  
-   Microsoft.SqlServer.SqlEnum.dll  
  
```csharp  
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
  
  
