---
title: Transfert de données | Microsoft Docs
ms.custom: ''
ms.date: 10/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- data transfers [SMO]
- transferring data
ms.assetid: eea255c3-8251-40f0-973b-fe4ef6cb5261
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a51364838173f70c4d5daac794176caa6ea01221
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "72796540"
---
# <a name="transferring-data"></a>Transfert de données
  La classe <xref:Microsoft.SqlServer.Management.Smo.Transfer> est une classe utilitaire qui fournit des outils pour transférer des objets et des données.  
  
 Les objets du schéma de base de données sont transférés en exécutant un script généré sur le serveur cible. Les données <xref:Microsoft.SqlServer.Management.Smo.Table> sont transférées avec un package DTS créé dynamiquement.  
  
 L'objet <xref:Microsoft.SqlServer.Management.Smo.Transfer> contient toutes les fonctionnalités des objets <xref:Microsoft.SqlServer.Management.Smo.Transfer> dans DMO, de même que des fonctionnalités [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supplémentaires. Toutefois, dans SMO dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], l' <xref:Microsoft.SqlServer.Management.Smo.Transfer> objet utilise l’API [SQLBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy\(v=VS.90\).aspx) pour transférer des données. Par ailleurs, les méthodes et les propriétés utilisées pour effectuer les transferts de données résident sur l'objet <xref:Microsoft.SqlServer.Management.Smo.Transfer> et non sur l'objet <xref:Microsoft.SqlServer.Management.Smo.Database>. Le déplacement de fonctionnalités des classes d'instance vers les classes utilitaires est compatible avec un modèle objet plus léger car le code de tâches spécifiques est chargé uniquement lorsqu'il est requis.  
  
 L'objet <xref:Microsoft.SqlServer.Management.Smo.Transfer> ne prend pas en charge les transferts de données vers une base de données cible dont un <xref:Microsoft.SqlServer.Management.Smo.Database.CompatibilityLevel%2A> est inférieur à la version de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Exemple  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-basic"></a>Transfert de schéma et de données d'une base de données vers une autre en Visual Basic  
 Cet exemple de code indique comment transférer un schéma et des données d'une base de données vers une autre à l'aide de l'objet <xref:Microsoft.SqlServer.Management.Smo.Transfer>.  
  
```vb
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Create a new database that is to be destination database.
Dim dbCopy As Database
dbCopy = New Database(srv, "AdventureWorks2012Copy")
dbCopy.Create()
'Define a Transfer object and set the required options and properties.
Dim xfr As Transfer
xfr = New Transfer(db)
xfr.CopyAllTables = True
xfr.Options.WithDependencies = True
xfr.Options.ContinueScriptingOnError = True
xfr.DestinationDatabase = "AdventureWorks2012Copy"
xfr.DestinationServer = srv.Name
xfr.DestinationLoginSecure = True
xfr.CopySchema = True
'Script the transfer. Alternatively perform immediate data transfer with TransferData method.
xfr.ScriptTransfer()
```
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-c"></a>Transfert de schéma et de données d'une base de données vers une autre en Visual C#  
 Cet exemple de code indique comment transférer un schéma et des données d'une base de données vers une autre à l'aide de l'objet <xref:Microsoft.SqlServer.Management.Smo.Transfer>.  
  
```csharp
{  
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Create a new database that is to be destination database.   
            Database dbCopy;  
            dbCopy = new Database(srv, "AdventureWorks2012Copy");  
            dbCopy.Create();  
            //Define a Transfer object and set the required options and properties.   
            Transfer xfr;  
            xfr = new Transfer(db);  
            xfr.CopyAllTables = true;  
            xfr.Options.WithDependencies = true;  
            xfr.Options.ContinueScriptingOnError = true;  
            xfr.DestinationDatabase = "AdventureWorks2012Copy";  
            xfr.DestinationServer = srv.Name;  
            xfr.DestinationLoginSecure = true;  
            xfr.CopySchema = true;  
            //Script the transfer. Alternatively perform immediate data transfer   
            // with TransferData method.   
            xfr.ScriptTransfer();  
        }   
```  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-powershell"></a>Transfert de schéma et de données d'une base de données vers une autre dans PowerShell  
 Cet exemple de code indique comment transférer un schéma et des données d'une base de données vers une autre à l'aide de l'objet <xref:Microsoft.SqlServer.Management.Smo.Transfer>.  
  
```powershell
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Reference the AdventureWorks2012 database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a database to hold the copy of AdventureWorks  
$dbCopy = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Database -ArgumentList $srv, "AdventureWorksCopy"  
$dbCopy.Create()  
  
#Define a Transfer object and set the required options and properties.  
$xfr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Transfer -ArgumentList $db  
  
#Set this objects properties  
$xfr.CopyAllTables = $true  
$xfr.Options.WithDependencies = $true  
$xfr.Options.ContinueScriptingOnError = $true  
$xfr.DestinationDatabase = "AdventureWorksCopy"  
$xfr.DestinationServer = $srv.Name  
$xfr.DestinationLoginSecure = $true  
$xfr.CopySchema = $true  
"Scripting Data Transfer"  
#Script the transfer. Alternatively perform immediate data transfer with TransferData method.  
$xfr.ScriptTransfer()  
```  
