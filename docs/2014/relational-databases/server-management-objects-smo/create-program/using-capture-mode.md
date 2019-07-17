---
title: À l’aide de Mode de Capture | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, capture mode
- capture mode [SMO]
- SMO [SQL Server], capture mode
ms.assetid: ace29bf0-705a-434f-82e4-db99d01c5008
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9ab758f83bde2cb587d3cfab8764fd7eb8fe2577
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68197990"
---
# <a name="using-capture-mode"></a>Utilisation du mode de capture
  Les programmes SMO peuvent capturer et enregistrer les instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] équivalentes publiées par le programme à la place ou en plus des instructions exécutées par le programme. Le mode de capture est activé au moyen de l'objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ou de la propriété <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Server>.  
  
## <a name="example"></a>Exemple  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="enabling-capture-mode-in-visual-basic"></a>Activation du mode de capture en Visual Basic  
 Cet exemple de code active le mode de capture, puis affiche les commandes [!INCLUDE[tsql](../../../includes/tsql-md.md)] conservées dans la mémoire tampon de capture.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCapture1](SMO How to#SMO_VBCapture1)]  -->  
  
## <a name="enabling-capture-mode-in-visual-c"></a>Activation du mode de capture en Visual C#  
 Cet exemple de code active le mode de capture, puis affiche les commandes [!INCLUDE[tsql](../../../includes/tsql-md.md)] conservées dans la mémoire tampon de capture.  
  
```  
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
  
  
