---
title: "À l’aide de Mode de Capture | Documents Microsoft"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, capture mode
- capture mode [SMO]
- SMO [SQL Server], capture mode
ms.assetid: ace29bf0-705a-434f-82e4-db99d01c5008
caps.latest.revision: "39"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5632d4e1c8df64ae77f9da90fecbc81f9244c7fa
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="using-capture-mode"></a>Utilisation du mode de capture
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Programmes SMO peuvent capturer et enregistrer l’équivalent [!INCLUDE[tsql](../../../includes/tsql-md.md)] instructions émises par le programme à la place d’ou en plus, les instructions sont exécutées par le programme. Le mode de capture est activé au moyen de l'objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ou de la propriété <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Server>.  
  
## <a name="example"></a>Exemple  
Pour utiliser un exemple de code fourni, vous devrez sélectionner l'environnement, le modèle et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un Visual C &#35; Projet SMO dans Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  

  
## <a name="enabling-capture-mode-in-visual-basic"></a>Activation du mode de capture en Visual Basic  
 Cet exemple de code active le mode de capture, puis affiche les commandes [!INCLUDE[tsql](../../../includes/tsql-md.md)] conservées dans la mémoire tampon de capture.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Set the execution mode to CaptureSql for the connection.
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.CaptureSql
'Make a modification to the server that is to be captured.
srv.UserOptions.AnsiNulls = True
srv.Alter()
'Iterate through the strings in the capture buffer and display the captured statements.
Dim s As String
For Each s In srv.ConnectionContext.CapturedSql.Text
    Console.WriteLine(s)
Next
'Execute the captured statements.
srv.ConnectionContext.ExecuteNonQuery(srv.ConnectionContext.CapturedSql.Text)
'Revert to immediate execution mode. 
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql
```
  
## <a name="enabling-capture-mode-in-visual-c"></a>Activation du mode de capture en Visual C#  
 Cet exemple de code active le mode de capture, puis affiche les commandes [!INCLUDE[tsql](../../../includes/tsql-md.md)] conservées dans la mémoire tampon de capture.  
  
```csharp  
{   
// Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
// Set the execution mode to CaptureSql for the connection.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.CaptureSql;   
// Make a modification to the server that is to be captured.   
srv.UserOptions.AnsiNulls = true;   
srv.Alter();   
// Iterate through the strings in the capture buffer and display the captured statements.   
string s;   
foreach ( String p_s in srv.ConnectionContext.CapturedSql.Text ) {   
   Console.WriteLine(p_s);   
}   
// Execute the captured statements.   
srv.ConnectionContext.ExecuteNonQuery(srv.ConnectionContext.CapturedSql.Text);   
// Revert to immediate execution mode.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
  
