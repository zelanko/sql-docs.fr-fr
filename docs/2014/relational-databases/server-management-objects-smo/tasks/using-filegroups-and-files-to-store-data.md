---
title: À l’aide de groupes de fichiers et de fichiers pour des données Store | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- filegroups [SMO]
- storing data [SMO]
- files [SMO]
- files [SMO], about files
- storage [SMO]
ms.assetid: 7e2327ce-e1a6-4904-83d1-0944b24a7b43
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bd05be78281375f75cca679b3cdbfcb269a984c2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324369"
---
# <a name="using-filegroups-and-files-to-store-data"></a>Utilisation de fichiers ou de groupes de fichiers pour stocker des données
  Les fichiers de données sont utilisés pour stocker les fichiers de base de données. Les fichiers de données se répartissent en plusieurs groupes de fichiers. L'objet <xref:Microsoft.SqlServer.Management.Smo.Database> a une propriété <xref:Microsoft.SqlServer.Management.Smo.Database.FileGroups%2A> qui référence un objet <xref:Microsoft.SqlServer.Management.Smo.FileGroupCollection>. Chaque objet <xref:Microsoft.SqlServer.Management.Smo.FileGroup> de cette collection a une propriété <xref:Microsoft.SqlServer.Management.Smo.FileGroup.Files%2A>. Cette propriété fait référence à une collection <xref:Microsoft.SqlServer.Management.Smo.DataFileCollection> qui contient tous les fichiers de données qui font partie de la base de données. Un groupe de fichiers est utilisé principalement pour regrouper les fichiers utilisés pour stocker un objet de base de données. L'étalement d'un objet de base de données sur plusieurs fichiers se justifie car cela permet d'améliorer les performances, surtout si les fichiers sont stockés sur les lecteurs de disques différents.  
  
 Chaque base de données créée automatiquement possède un groupe de fichiers nommé "Primary" et un fichier de données avec le même nom que la base de données. D'autres fichiers et groupes peuvent être ajoutés aux collections.  
  
## <a name="examples"></a>Exemples  
 Dans les exemples de code suivants, vous devez sélectionner l'environnement, le modèle et le langage de programmation à utiliser pour créer votre application. Pour plus d’informations, consultez [créer un projet SMO Visual Basic dans Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) et [créer un Visual C&#35; projet SMO dans Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="adding-filegroups-and-datafiles-to-a-database-in-visual-basic"></a>Ajout de groupes de fichiers et de fichiers de données à une base de données en Visual Basic  
 Le groupe de fichiers et le fichier de données primaires sont créés automatiquement avec les valeurs de propriété par défaut. L'exemple de code spécifie quelques valeurs de propriété que vous pouvez utiliser. Sinon, les valeurs de propriété par défaut sont utilisées.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBFileGroups1](SMO How to#SMO_VBFileGroups1)]  -->  
  
## <a name="adding-filegroups-and-datafiles-to-a-database-in-visual-c"></a>Ajout de groupes de fichiers et de fichiers de données à une base de données en Visual C#  
 Le groupe de fichiers et le fichier de données primaires sont créés automatiquement avec les valeurs de propriété par défaut. L'exemple de code spécifie quelques valeurs de propriété que vous pouvez utiliser. Sinon, les valeurs de propriété par défaut sont utilisées.  
  
```  
{  
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a FileGroup object called SECONDARY on the database.   
            FileGroup fg1 = default(FileGroup);  
            fg1 = new FileGroup(db, "SECONDARY");  
            //Call the Create method to create the file group on the instance of SQL Server.   
            fg1.Create();  
            //Define a DataFile object on the file group and set the FileName property.   
            DataFile df1 = default(DataFile);  
            df1 = new DataFile(fg1, "datafile1");  
            df1.FileName = "c:\\Program Files\\Microsoft SQL Server\\MSSQL.1\\MSSQL\\Data\\datafile2.ndf";  
            //Call the Create method to create the data file on the instance of SQL Server.   
            df1.Create();  
        }  
```  
  
## <a name="adding-filegroups-and-datafiles-to-a-database-in-powershell"></a>Ajout de groupes de fichiers et de fichiers de données à une base de données dans PowerShell  
 Le groupe de fichiers et le fichier de données primaires sont créés automatiquement avec les valeurs de propriété par défaut. L'exemple de code spécifie quelques valeurs de propriété que vous pouvez utiliser. Sinon, les valeurs de propriété par défaut sont utilisées.  
  
```  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default\Databases\  
  
#And the database object corresponding to AdventureWorks2012.  
$db = get-item AdventureWorks2012  
  
#Create a new filegroup  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "SECONDARY"  
$fg1.Create()  
  
#Define a DataFile object on the file group and set the FileName property.   
$df1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.DataFile -argumentlist $fg1, "datafile1"  
  
#Make sure to have a directory created to hold the designated data file  
$df1.FileName = "c:\\TestData\\datafile2.ndf"  
  
#Call the Create method to create the data file on the instance of SQL Server.   
$df1.Create()  
```  
  
## <a name="creating-altering-and-removing-a-log-file-in-visual-basic"></a>Création, modification et suppression d'un fichier journal en Visual Basic  
 L'exemple de code suivant crée un objet <xref:Microsoft.SqlServer.Management.Smo.LogFile>, modifie l'une de ses propriétés, puis le supprime de la base de données.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBFileGroups3](SMO How to#SMO_VBFileGroups3)]  -->  
  
## <a name="creating-altering-and-removing-a-log-file-in-visual-c"></a>Création, modification et suppression d'un fichier journal en Visual C#  
 L'exemple de code suivant crée un objet <xref:Microsoft.SqlServer.Management.Smo.LogFile>, modifie l'une de ses propriétés, puis le supprime de la base de données.  
  
```  
//Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a LogFile object and set the database, name, and file name properties in the constructor.   
            LogFile lf1 = default(LogFile);  
            lf1 = new LogFile(db, "logfile1", "c:\\Program Files\\Microsoft SQL Server\\MSSQL.10_50.MSSQLSERVER\\MSSQL\\Data\\logfile1.ldf");  
            //Set the file growth to 6%.   
            lf1.GrowthType = FileGrowthType.Percent;  
            lf1.Growth = 6;  
            //Run the Create method to create the log file on the instance of SQL Server.   
            lf1.Create();  
            //Alter the growth percentage.   
            lf1.Growth = 7;  
            lf1.Alter();  
            //Remove the log file.   
            lf1.Drop();  
  
```  
  
## <a name="creating-altering-and-removing-a-log-file-in-powershell"></a>Création, modification et suppression d'un fichier journal dans PowerShell  
 L'exemple de code suivant crée un objet <xref:Microsoft.SqlServer.Management.Smo.LogFile>, modifie l'une de ses propriétés, puis le supprime de la base de données.  
  
```  
#Load the assembly containing the enums used in this example  
[reflection.assembly]::LoadWithPartialName("Microsoft.SqlServer.SqlEnum")  
  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default\Databases\  
  
#And the database object corresponding to AdventureWorks2012  
$db = get-item AdventureWorks2012  
  
#Create a filegroup  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Secondary"  
  
#Call the Create method to create the file group on the instance of SQL Server.   
$fg1.Create()  
  
#Define a LogFile object on the file group and set the FileName property.   
$lf1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LogFile -argumentlist $db, "LogFile2"  
  
#Set a location for it - make sure the directory exists  
$lf1.FileName = "logfile1", "c:\\Program Files\\Microsoft SQL Server\\MSSQL.10_50.MSSQLSERVER\\MSSQL\\Data\\logfile1.ldf"  
  
#Set file growth to 6%  
$lf1.GrowthType = [Microsoft.SqlServer.Management.Smo.FileGrowthType]::Percent  
$lf1.Growth = 6.0  
  
#Call the Create method to create the data file on the instance of SQL Server.   
$lf1.Create()  
  
#Alter a value and drop the log file  
$lf1.Growth = 7.0  
$lf1.Alter()  
$lf1.Drop()  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.SqlServer.Management.Smo.FileGroup>   
 [Groupes de fichiers et fichiers de base de données](../../databases/database-files-and-filegroups.md)  
  
  
