---
title: Connexion à des sources de données dans une tâche personnalisée | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ConnectionManager objects
- connection managers [Integration Services], external data sources
- data sources [Integration Services], external
- custom tasks [Integration Services], external data sources
- external data sources [Integration Services]
- connections [Integration Services], external data sources
- SSIS custom tasks, external data sources
ms.assetid: 9f0b3a43-3eaa-4b3c-bb08-29b630c11306
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1aceb12a66d20f8999f96e5bbee32fdbcaee4b33
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53368611"
---
# <a name="connecting-to-data-sources-in-a-custom-task"></a>Connexion à des sources de données dans une tâche personnalisée
  Les tâches se connectent à des sources de données externes pour extraire ou enregistrer des données à l'aide d'un gestionnaire de connexions. Au moment de la conception, un gestionnaire de connexions représente une connexion logique et décrit des informations clés telles que le nom du serveur et des propriétés d'authentification. Au moment de l'exécution, les tâches appellent la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> du gestionnaire de connexions pour établir la connexion physique à la source de données.  
  
 Étant donné qu'un package peut contenir de nombreuses tâches, lesquelles peuvent chacune avoir des connexions à des sources de données différentes, le package suit tous les gestionnaires de connexions dans une collection, la collection <xref:Microsoft.SqlServer.Dts.Runtime.Connections>. Les tâches utilisent la collection de leur package pour rechercher le gestionnaire de connexions qu'elles utiliseront pendant la validation et l'exécution. La collection <xref:Microsoft.SqlServer.Dts.Runtime.Connections> constitue le premier paramètre des méthodes <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> et <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>.  
  
 Vous pouvez empêcher la tâche d'utiliser le mauvais gestionnaire de connexions en présentant les objets <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> de la collection à l'utilisateur, en utilisant une boîte de dialogue ou une liste déroulante dans l'interface utilisateur graphique. Cela permet à l'utilisateur de disposer d'un moyen d'effectuer une sélection uniquement parmi les objets <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> du type approprié et contenus dans le package.  
  
 Les tâches appellent la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> pour établir la connexion physique à la source de données. La méthode renvoie l'objet de connexion sous-jacent qui peut alors être utilisé par la tâche. Étant donné que le gestionnaire de connexions isole de la tâche les détails d'implémentation de l'objet de connexion sous-jacent, la tâche doit seulement appeler la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> pour établir la connexion et n'a pas à s'occuper des autres aspects de la connexion.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre la validation du nom <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> dans les méthodes Validate et Execute, puis indique comment utiliser la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> pour établir la connexion physique dans la méthode Execute.  
  
```csharp  
private string connectionManagerName = "";  
  
public string ConnectionManagerName  
{  
  get { return this.connectionManagerName; }  
  set { this.connectionManagerName = value; }  
}  
  
public override DTSExecResult Validate(  
  Connections connections, VariableDispenser variableDispenser,  
  IDTSComponentEvents componentEvents, IDTSLogging log)  
{  
  // If the connection manager exists, validation is successful;  
  // otherwise, fail validation.  
  try  
  {  
    ConnectionManager cm = connections[this.connectionManagerName];  
    return DTSExecResult.Success;  
  }  
  catch (System.Exception e)  
  {  
    componentEvents.FireError(0, "SampleTask", "Invalid connection manager.", "", 0);  
    return DTSExecResult.Failure;  
  }  
}  
  
public override DTSExecResult Execute(Connections connections,   
  VariableDispenser variableDispenser, IDTSComponentEvents componentEvents,   
  IDTSLogging log, object transaction)  
{  
  try  
  {  
    ConnectionManager cm = connections[this.connectionManagerName];  
    object connection = cm.AcquireConnection(transaction);  
    return DTSExecResult.Success;  
  }  
  catch (System.Exception exception)  
  {  
    componentEvents.FireError(0, "SampleTask", exception.Message, "", 0);  
    return DTSExecResult.Failure;  
  }  
}  
```  
  
```vb  
Private _connectionManagerName As String = ""  
  
Public Property ConnectionManagerName() As String  
  Get  
    Return Me._connectionManagerName  
  End Get  
  Set(ByVal Value As String)  
    Me._connectionManagerName = value  
  End Set  
End Property  
  
Public Overrides Function Validate( _  
  ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, _  
  ByVal variableDispenser As Microsoft.SqlServer.Dts.Runtime.VariableDispenser, _  
  ByVal componentEvents As Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents, _  
  ByVal log As Microsoft.SqlServer.Dts.Runtime.IDTSLogging) _  
  As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  ' If the connection manager exists, validation is successful;  
  ' otherwise fail validation.  
  Try  
    Dim cm As ConnectionManager = connections(Me._connectionManagerName)  
    Return DTSExecResult.Success  
  Catch e As System.Exception  
    componentEvents.FireError(0, "SampleTask", "Invalid connection manager.", "", 0)  
    Return DTSExecResult.Failure  
  End Try  
  
End Function  
  
Public Overrides Function Execute( _  
  ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, _  
  ByVal variableDispenser As Microsoft.SqlServer.Dts.Runtime.VariableDispenser, _  
  ByVal componentEvents As Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents, _  
  ByVal log As Microsoft.SqlServer.Dts.Runtime.IDTSLogging, ByVal transaction As Object) _  
  As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  Try  
    Dim cm As ConnectionManager = connections(Me._connectionManagerName)  
    Dim connection As Object = cm.AcquireConnection(transaction)  
    Return DTSExecResult.Success  
  Catch exception As System.Exception  
    componentEvents.FireError(0, "SampleTask", exception.Message, "", 0)  
    Return DTSExecResult.Failure  
  End Try  
  
End Function  
```  
  
![Icône Integration Services (petite)](../../media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions Integration Services &#40;SSIS&#41;](../../connection-manager/integration-services-ssis-connections.md)   
 [Créer des gestionnaires de connexions](../../create-connection-managers.md)  
  
  
