---
title: Gestion des Exceptions SMO | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 595da161660b60845c02d71e22411a2a4eba009c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63192099"
---
# <a name="handling-smo-exceptions"></a>Gestion des exceptions SMO
  En code managé, des exceptions sont levées lorsqu'une erreur se produit. Les méthodes et propriétés SMO ne signalent ni la réussite ni l'échec dans la valeur de retour. Au lieu de cela, les exceptions peuvent être interceptées et gérées par un gestionnaire d'exceptions.  
  
 Il existe différentes classes d'exceptions SMO. Les informations sur l'exception peuvent être extraites des propriétés d'exception telles que la propriété `Message` qui donne un message texte concernant l'exception.  
  
 Les instructions de gestion des exceptions sont spécifiques au langage de programmation. Par exemple, dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic, il s'agit de l'instruction `Catch`.  
  
## <a name="inner-exceptions"></a>Exceptions internes  
 Les exceptions peuvent être générales ou spécifiques. Les exceptions générales contiennent un jeu d'exceptions spécifiques. Plusieurs instructions `Catch` peuvent être utilisées pour gérer les erreurs anticipées et faire passer les erreurs restantes au code de gestion des exceptions générales. Les exceptions se produisent souvent dans une séquence en cascade. Il arrive fréquemment qu'une exception SMO soit provoquée par une exception SQL. Pour le savoir, utilisez successivement la propriété `InnerException` pour déterminer l'exception d'origine ayant provoqué l'exception finale de niveau supérieur.  
  
> [!NOTE]  
>  Le `SQLException` exception est déclarée dans le **System.Data.SqlClient** espace de noms.  
  
 ![Un diagramme qui montre les niveaux à partir de laquelle un excp](../../../database-engine/dev-guide/media/exception-flow.gif "un diagramme qui montre les niveaux à partir de laquelle un excp")  
  
 Le diagramme affiche le flux d'exceptions à travers les couches de l'application.  
  
## <a name="example"></a>Exemple  
 Pour utiliser un exemple de code qui est fourni, vous devrez choisir l'environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un Visual C&#35; projet SMO dans Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md) ou [créer un projet SMO Visual Basic dans Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md).  
  
## <a name="catching-an-exception-in-visual-basic"></a>Interception d'une exception en Visual Basic  
 Cet exemple de code montre comment utiliser l'instruction [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]`Try...Catch...Finally` pour intercepter une exception SMO. Toutes les exceptions SMO possèdent le type SmoException et sont répertoriées dans la référence SMO. La séquence d'exceptions internes est affichée pour indiquer la racine de l'erreur. Pour plus d'informations, consultez la documentation [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBExceptions1](SMO How to#SMO_VBExceptions1)]  -->  
  
## <a name="catching-an-exception-in-visual-c"></a>Interception d'une exception en Visual C#  
 Cet exemple de code montre comment utiliser l'instruction Visual C# `Try...Catch...Finally` pour intercepter une exception SMO. Toutes les exceptions SMO possèdent le type SmoException et sont répertoriées dans la référence SMO. La séquence d'exceptions internes est affichée pour indiquer la racine de l'erreur. Pour plus d'informations, consultez la documentation Visual C#.  
  
```  
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
  
  
