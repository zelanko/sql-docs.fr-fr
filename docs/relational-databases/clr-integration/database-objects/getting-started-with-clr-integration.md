---
title: Prise en main avec l’intégration du CLR | Microsoft Docs
description: Cet article décrit les espaces de noms et les bibliothèques requis pour compiler des objets de base de données à l’aide de l’intégration Microsoft SQL Server avec le CLR .NET Framework.
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: quickstart
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration]
- namespaces [CLR integration]
- database objects [CLR integration], about CLR integration
- stored procedures [CLR integration]
- common language runtime [SQL Server], about CLR integration
- building database objects [CLR integration], about CLR integration
- common language runtime [SQL Server], stored procedures
- common language runtime [SQL Server], namespaces
- Hello World example [CLR integration]
- library [CLR integration]
ms.assetid: c73e628a-f54a-411a-bfe3-6dae519316cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 6b560aa650140e4b94bbea4491fb28e5f1bf656f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717894"
---
# <a name="getting-started-with-clr-integration"></a>Mise en route avec l'intégration du CLR

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]

Cette rubrique fournit une vue d’ensemble des espaces de noms et des bibliothèques requis pour compiler des objets de base de données à l’aide de l' [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] intégration avec l' .NET Framework Common Language Runtime (CLR). La rubrique vous indique également comment écrire, compiler et exécuter une procédure stockée CLR simple écrite dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.  
  
## <a name="required-namespaces"></a>Espaces de noms requis  

Les composants requis pour développer des objets de base de données CLR de base sont installés avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Les fonctionnalités d'intégration du CLR sont exposées dans un assembly appelé system.data.dll, qui fait partie du .NET Framework. Cet assembly se trouve dans le Global Assembly Cache (GAC), ainsi que dans le répertoire .NET Framework. Une référence à cet assembly est ajoutée en général automatiquement par les outils en ligne de commande et [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio, afin qu'il ne soit pas nécessaire de l'ajouter manuellement.  
  
L'assembly system.data.dll contient les espaces de noms suivants, qui sont requis pour compiler les objets de base de données CLR :  
  
- `System.Data`  
- `System.Data.Sql`  
- `Microsoft.SqlServer.Server`  
- `System.Data.SqlTypes`  

> [!TIP]
> Le chargement d’objets de base de données CLR sur Linux est pris en charge, mais ils doivent être générés avec le .NET Framework (SQL Server l’intégration du CLR ne prend pas en charge .NET Core). En outre, les assemblys CLR avec le EXTERNAL_ACCESS ou un jeu d’autorisations unsafe ne sont pas pris en charge sur Linux.

## <a name="writing-a-simple-hello-world-stored-procedure"></a>Écriture d'une procédure stockée "Hello World" simple  

Copiez et collez le code Visual C# ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic suivant dans un éditeur de texte et enregistrez-le dans un fichier nommé "helloworld.cs" ou "helloworld.vb".  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlTypes;  
  
public class HelloWorldProc  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld(out string text)  
    {  
        SqlContext.Pipe.Send("Hello world!" + Environment.NewLine);  
        text = "Hello world!";  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlTypes  
Imports System.Runtime.InteropServices  
  
Public Class HelloWorldProc  
    \<Microsoft.SqlServer.Server.SqlProcedure> _   
    Public Shared  Sub HelloWorld(\<Out()> ByRef text as String)  
        SqlContext.Pipe.Send("Hello world!" & Environment.NewLine)  
        text = "Hello world!"  
    End Sub  
End Class  
  
```  
  
Ce programme simple contient une méthode statique unique sur une classe publique. Cette méthode utilise deux nouvelles classes, **[SqlContext](https://msdn.microsoft.com/library/microsoft.sqlserver.server.sqlcontext.aspx)** et **[SqlPipe](https://msdn.microsoft.com/library/microsoft.sqlserver.server.sqlpipe.aspx)**, pour créer des objets de base de données managés afin de générer un message texte simple. La méthode assigne également la chaîne « Hello World ! » comme valeur d’un paramètre de sortie. Cette méthode peut être déclarée comme une procédure stockée dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], puis s'exécuter de la même manière qu'une procédure stockée [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
Compilez ce programme en tant que bibliothèque, chargez-le dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et exécutez-le en tant que procédure stockée.  
  
## <a name="compile-the-hello-world-stored-procedure"></a>Compiler la procédure stockée « Hello World »  

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installe par défaut les fichiers de redistribution [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Ces fichiers incluent csc.exe et vbc.exe, les compilateurs de ligne de commande pour les programmes Visual C# et Visual Basic. Pour compiler notre exemple, vous devez modifier votre variable de chemin d'accès pour pointer sur le répertoire qui contient csc.exe ou vbc.exe. Le chemin d'installation par défaut du .NET Framework est le suivant :  
  
`C:\Windows\Microsoft.NET\Framework\(version)`  
  
La version contient le numéro de version du programme redistribuable .NET Framework installé. Par exemple :  
  
`C:\Windows\Microsoft.NET\Framework\v4.6.1`

Une fois que vous avez ajouté le répertoire .NET Framework à votre chemin d'accès, vous pouvez compiler l'exemple de procédure stockée en assembly à l'aide de la commande ci-dessous. L’option **/target** vous permet de la compiler dans un assembly.  
  
Pour les fichiers sources Visual C# :  
  
`csc /target:library helloworld.cs`  
  
 Pour les fichiers sources Visual Basic :  
  
`vbc /target:library helloworld.vb`  
  
Ces commandes lancent le compilateur Visual C# ou Visual Basic en utilisant l'option /target pour spécifier la génération d'une DLL de bibliothèque.  
  
## <a name="loading-and-running-the-hello-world-stored-procedure-in-sql-server"></a>Chargement et exécution de la procédure stockée "Hello World" dans SQL Server  

Une fois que l'exemple de procédure a été compilé avec succès, vous pouvez le tester dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour cela, ouvrez [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et créez une nouvelle requête, en vous connectant à une base de données de test appropriée (par exemple, l'exemple de base de données AdventureWorks).  
  
La fonctionnalité d'exécution du code CLR est désactivée par défaut dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le code CLR peut être activé à l’aide de la procédure stockée système **sp_configure** . Pour plus d’informations, consultez [Activation de l’intégration du CLR](../../../relational-databases/clr-integration/clr-integration-enabling.md).  
  
Il est nécessaire de créer l'assembly afin de pouvoir accéder à la procédure stockée. Pour cet exemple, nous supposerons que vous avez créé l'assembly helloworld.dll dans le répertoire C:\. Ajoutez l'instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] suivante à votre requête.  
  
`CREATE ASSEMBLY helloworld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE`  
  
Une fois l'assembly créé, il est possible d'accéder à la méthode HelloWorld en utilisant l'instruction CREATE PROCEDURE. Nous appellerons la procédure stockée "hello" :  
  
```sql
CREATE PROCEDURE hello  
@i nchar(25) OUTPUT  
AS  
EXTERNAL NAME helloworld.HelloWorldProc.HelloWorld  
-- if the HelloWorldProc class is inside a namespace (called MyNS),  
-- the last line in the create procedure statement would be  
-- EXTERNAL NAME helloworld.[MyNS.HelloWorldProc].HelloWorld  
```  
  
Une fois la procédure créée, elle peut être exécutée tout comme une procédure stockée normale écrite dans [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Exécutez la commande suivante :  
  
```sql
DECLARE @J nchar(25)  
EXEC hello @J out  
PRINT @J  
```  
  
Cela doit générer la sortie ci-dessous dans la fenêtre des messages [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
```
Hello world!  
Hello world!  
```  
  
## <a name="removing-the-hello-world-stored-procedure-sample"></a>Suppression de l'exemple de procédure stockée "Hello World"  

Lorsque vous avez terminé d'exécuter l'exemple de procédure stockée, vous pouvez supprimer la procédure et l'assembly de votre base de données de test.  
  
En premier lieu, supprimez la procédure à l'aide de la commande drop procedure.  
  
```sql
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'hello')  
   drop procedure hello  
```  
  
Une fois la procédure supprimée, vous pouvez supprimer l'assembly qui contient votre exemple de code.  
  
```sql
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'helloworld')  
   drop assembly helloworld  
```  
  
## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’intégration du CLR dans SQL Server, consultez les articles suivants :

- [Procédures stockées CLR](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)
- [Extensions spécifiques in-process de SQL Server à ADO.NET](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)
- [Débogage d'objets de base de données CLR](../../../relational-databases/clr-integration/debugging-clr-database-objects.md)
- [Sécurité de l'intégration du CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md)
