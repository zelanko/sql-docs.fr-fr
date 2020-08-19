---
description: Gestion des exceptions SMO
title: Gestion des exceptions SMO | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 92167925e38e2029ac94d83b7ca4c9566e41527f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448071"
---
# <a name="handling-smo-exceptions"></a>Gestion des exceptions SMO
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  En code managé, des exceptions sont levées lorsqu'une erreur se produit. Les méthodes et propriétés SMO ne signalent ni la réussite ni l'échec dans la valeur de retour. Au lieu de cela, les exceptions peuvent être interceptées et gérées par un gestionnaire d'exceptions.  
  
 Il existe différentes classes d'exceptions SMO. Les informations sur l'exception peuvent être extraites des propriétés d'exception telles que la propriété **Message** qui donne un message texte concernant l'exception.  
  
 Les instructions de gestion des exceptions sont spécifiques au langage de programmation. Par exemple, dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic, il s'agit de l'instruction **Catch** .  
  
## <a name="inner-exceptions"></a>Exceptions internes  
 Les exceptions peuvent être générales ou spécifiques. Les exceptions générales contiennent un jeu d'exceptions spécifiques. Plusieurs instructions **Catch** peuvent être utilisées pour gérer les erreurs anticipées et faire passer les erreurs restantes au code de gestion des exceptions générales. Les exceptions se produisent souvent dans une séquence en cascade. Il arrive fréquemment qu'une exception SMO soit provoquée par une exception SQL. Pour le savoir, utilisez successivement la propriété **InnerException** pour déterminer l'exception d'origine ayant provoqué l'exception finale de niveau supérieur.  
  
> [!NOTE]  
>  L’exception **SqlException** est déclarée dans l’espace de noms **System. Data. SqlClient** .  
  
 ![Diagramme illustrant les niveaux à partir desquels une exception s'est produite](../../../relational-databases/server-management-objects-smo/create-program/media/exception-flow.gif "Diagramme illustrant les niveaux à partir desquels une exception s'est produite")  
  
 Le diagramme affiche le flux d'exceptions à travers les couches de l'application.  
  
## <a name="example"></a>Exemple  
 Pour utiliser un exemple de code qui est fourni, vous devrez choisir l'environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un projet Visual C&#35; Smo dans Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).
  
## <a name="catching-an-exception-in-visual-basic"></a>Interception d'une exception en Visual Basic  
 Cet exemple de code montre comment utiliser la méthode **try... Catch... Finally** [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] pour intercepter une exception Smo. Toutes les exceptions SMO possèdent le type SmoException et sont répertoriées dans la référence SMO. La séquence d'exceptions internes est affichée pour indiquer la racine de l'erreur. Pour plus d'informations, consultez la documentation [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET.  
  
```VBNET
'This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace is included.
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.
'Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.
Dim op As [Operator]
op = New [Operator](srv.JobServer, "Test_Operator")
op.Create()
'Start exception handling.
Try
    'Create the operator again to cause an SMO exception.
    Dim opx As OperatorCategory
    opx = New OperatorCategory(srv.JobServer, "Test_Operator")
    opx.Create()
    'Catch the SMO exception
Catch smoex As SmoException
    Console.WriteLine("This is an SMO Exception")
    'Display the SMO exception message.
    Console.WriteLine(smoex.Message)
    'Display the sequence of non-SMO exceptions that caused the SMO exception.
    Dim ex As Exception
    ex = smoex.InnerException
    Do While ex.InnerException IsNot (Nothing)
        Console.WriteLine(ex.InnerException.Message)
        ex = ex.InnerException
    Loop
    'Catch other non-SMO exceptions.
Catch ex As Exception
    Console.WriteLine("This is not an SMO exception.")
End Try
``` 
  
## <a name="catching-an-exception-in-visual-c"></a>Interception d'une exception en Visual C#  
 Cet exemple de code montre comment utiliser la méthode **try... Catch... Finally** (instruction Visual C#) pour intercepter une exception Smo. Toutes les exceptions SMO possèdent le type SmoException et sont répertoriées dans la référence SMO. La séquence d'exceptions internes est affichée pour indiquer la racine de l'erreur. Pour plus d'informations, consultez la documentation Visual C#.  
  
```csharp  
{   
//This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace to be included.   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.   
//Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.   
op = new Operator(srv.JobServer, "Test_Operator");   
op.Create();   
//Start exception handling.   
try {   
    //Create the operator again to cause an SMO exception.   
    OperatorCategory opx;   
    opx = new OperatorCategory(srv.JobServer, "Test_Operator");   
    opx.Create();   
}   
//Catch the SMO exception   
catch (SmoException smoex) {   
    Console.WriteLine("This is an SMO Exception");   
   //Display the SMO exception message.   
   Console.WriteLine(smoex.Message);   
   //Display the sequence of non-SMO exceptions that caused the SMO exception.   
   Exception ex;   
   ex = smoex.InnerException;   
   while (!object.ReferenceEquals(ex.InnerException, (null))) {   
      Console.WriteLine(ex.InnerException.Message);   
      ex = ex.InnerException;   
    }   
    }   
   //Catch other non-SMO exceptions.   
   catch (Exception ex) {   
      Console.WriteLine("This is not an SMO exception.");   
}   
}  
```  
  
  
