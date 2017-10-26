---
title: "Création d’un Package par programme | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: e44bcc70-32d3-43e8-a84b-29aef819d5d3
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 58a8201d68cb6d942bd98ca3c53b6cf98336284e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="creating-a-package-programmatically"></a>Création d'un package par programme
  L'objet <xref:Microsoft.SqlServer.Dts.Runtime.Package> correspond au conteneur de niveau supérieur de tous les autres objets inclus dans une solution de projet [!INCLUDE[ssIS](../../includes/ssis-md.md)]. En tant que conteneur de niveau supérieur, le package est le premier objet créé, puis des objets suivants lui sont ajoutés, puis ils sont exécutés dans le contexte du package. Le package lui-même ne déplace pas et ne transforme pas de données. Il se repose sur les tâches qu'il contient pour effectuer le travail. Les tâches effectuent la plupart du travail d'un package et définissent ses fonctionnalités. Un package est créé et exécuté avec seulement trois lignes de code, mais différentes tâches et objets <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> sont ajoutés pour lui donner des fonctionnalités supplémentaires. Cette section décrit comment créer un package par programme. Elle ne fournit pas d'informations sur la manière de créer les tâches ou les objets <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>. Ceux-ci sont traités dans les sections ultérieures.  
  
## <a name="example"></a>Exemple  
 Pour écrire du code à l'aide de l'environnement de développement intégré Visual Studio, une référence à Microsoft.SqlServer.ManagedDTS.DLL est requise afin de créer une instruction `using` (`Imports` dans Visual Basic .NET) dans Microsoft.SqlServer.Dts.Runtime. L'exemple de code suivant présente la création d'un package vide.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package;  
      package = new Package();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Package  
    package = New Package  
  
  End Sub  
  
End Module  
```  
  
 Pour compiler et exécuter l'exemple, appuyez sur F5 dans Visual Studio. Pour générer le code à l’aide du compilateur c#, **csc.exe**, à l’invite de commandes pour compiler, utilisez la commande suivante et en remplaçant les références de fichiers la  *\<filename >* avec le nom de fichier .cs ou .vb et en lui donnant un  *\<outputfilename >* de votre choix.  
  
 **csc/target : library/out : \<outputfilename > .dll \<filename > .cs /r:Microsoft.SqlServer.Managed DTS.dll « r**  
  
 Pour générer le code à l’aide du compilateur Visual Basic .NET, **vbc.exe**, à l’invite de commandes pour compiler, utilisez la commande suivante et les références de fichiers.  
  
 **vbc/target : library/out : \<outputfilename > .dll \<filename > .vb /r:Microsoft.SqlServer.Managed DTS.dll « r**  
  
 Vous pouvez également créer un package en chargeant un package existant enregistré sur le disque, dans le système de fichiers ou dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La différence est que le <xref:Microsoft.SqlServer.Dts.Runtime.Application> objet est créé, puis l’objet de package est remplie par une des méthodes surchargées de l’Application : **LoadPackage est** pour les fichiers plats, **LoadFromSQLServer** pour les packages enregistrés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> pour les packages enregistrés dans le système de fichiers. L'exemple suivant charge un package existant à partir du disque, puis consulte plusieurs propriétés sur le package.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class ApplicationTests  
  {  
    static void Main(string[] args)  
    {  
      // The variable pkg points to the location of the  
      // ExecuteProcess package sample that was installed with  
      // the SSIS samples.  
      string pkg = @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx";  
  
      Application app = new Application();  
      Package p = app.LoadPackage(pkg, null);  
  
      // Now that the package is loaded, we can query on  
      // its properties.  
      int n = p.Configurations.Count;  
      DtsProperty p2 = p.Properties["VersionGUID"];  
      DTSProtectionLevel pl = p.ProtectionLevel;  
  
      Console.WriteLine("Number of configurations = " + n.ToString());  
      Console.WriteLine("VersionGUID = " + (string)p2.GetValue(p));  
      Console.WriteLine("ProtectionLevel = " + pl.ToString());  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module ApplicationTests  
  
  Sub Main()  
  
    ' The variable pkg points to the location of the  
    ' ExecuteProcess package sample that was installed with  
    ' the SSIS samples.  
    Dim pkg As String = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx"  
  
    Dim app As Application = New Application()  
    Dim p As Package = app.LoadPackage(pkg, Nothing)  
  
    ' Now that the package is loaded, we can query on  
    ' its properties.  
    Dim n As Integer = p.Configurations.Count  
    Dim p2 As DtsProperty = p.Properties("VersionGUID")  
    Dim pl As DTSProtectionLevel = p.ProtectionLevel  
  
    Console.WriteLine("Number of configurations = " & n.ToString())  
    Console.WriteLine("VersionGUID = " & CType(p2.GetValue(p), String))  
    Console.WriteLine("ProtectionLevel = " & pl.ToString())  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 **Exemple de sortie :**  
  
 `Number of configurations = 2`  
  
 `VersionGUID = {09016682-89B8-4406-AAC9-AF1E527FF50F}`  
  
 `ProtectionLevel = DontSaveSensitive`  
  
## <a name="external-resources"></a>Ressources externes  
  
-   Entrée de blog, [API Sample - OleDB source et destination d’OleDB](http://go.microsoft.com/fwlink/?LinkId=220824), sur blogs.msdn.com.  
  
-   Entrée de blog, [EzAPI – mise à jour pour SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=243223), sur blogs.msdn.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de tâches par programmation](../../integration-services/building-packages-programmatically/adding-tasks-programmatically.md)  
  
  

