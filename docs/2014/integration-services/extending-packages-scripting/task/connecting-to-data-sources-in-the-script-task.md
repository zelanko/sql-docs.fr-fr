---
title: Connexion aux sources de données dans la tâche de script | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- connections [Integration Services], scripts
- Integration Services packages, connections
- connection managers [Integration Services], scripts
- scripts [Integration Services], connections
- SSIS packages, connections
- packages [Integration Services], connections
- Script task [Integration Services], connections
- Connections property
- SQL Server Integration Services packages, connections
- SSIS Script task, connections
ms.assetid: 9c008380-715b-455b-9da7-22572d67c388
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 50d0914efce0fd8b91d0a4ac2e93d01d910849e4
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967208"
---
# <a name="connecting-to-data-sources-in-the-script-task"></a>Connexion à des sources de données dans la tâche de script
  Les gestionnaires de connexions fournissent un accès à des sources de données qui ont été configurées dans le package. Pour plus d’informations, consultez [Connexions Integration Services &#40;SSIS&#41;](../../connection-manager/integration-services-ssis-connections.md).  
  
 La tâche de script peut accéder à ces gestionnaires de connexions via la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> de l’objet**Dts**. Chaque gestionnaire de connexions compris dans la collection <xref:Microsoft.SqlServer.Dts.Runtime.Connections> stocke des informations sur la manière d'établir une connexion à la source de données sous-jacente.  
  
 Lorsque vous appelez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> d'un gestionnaire de connexions, le gestionnaire de connexions se connecte à la source de données, s'il n'est pas déjà connecté, puis renvoie la connexion ou les informations de connexion appropriées que vous devez utiliser dans le code de votre tâche de script.  
  
> [!NOTE]  
>  Vous devez connaître le type de connexion renvoyé par le gestionnaire de connexions avant d’appeler `AcquireConnection` . Étant donné que la tâche de script a `Option Strict` activé, vous devez effectuer un cast de la connexion, qui est retournée en tant que type `Object`, vers le type de connexion approprié avant de pouvoir l'utiliser.  
  
 Vous pouvez utiliser la méthode <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> de la collection <xref:Microsoft.SqlServer.Dts.Runtime.Connections> renvoyée par la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> pour rechercher une connexion existante avant d'utiliser la connexion dans votre code.  
  
> [!IMPORTANT]  
>  Vous ne pouvez pas appeler la méthode AcquireConnection des gestionnaires de connexions qui renvoient des objets non managés, tels que le gestionnaire de connexions OLE DB et le gestionnaire de connexions Excel, dans le code managé d’une tâche de script. Toutefois, vous pouvez lire la propriété ConnectionString de ces gestionnaires de connexions et vous connecter directement à la source de données dans votre code en utilisant la chaîne de connexion avec un `OledbConnection` de l’espace de noms **System. Data. OleDb** .  
>   
>  Si vous devez appeler la méthode AcquireConnection d’un gestionnaire de connexions qui retourne un objet non managé, utilisez un gestionnaire de connexions [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]. Lorsque vous configurez le gestionnaire de connexions [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] afin d'utiliser un fournisseur OLE DB, il se connecte en utilisant le fournisseur de données [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] pour OLE DB. Dans ce cas, la méthode AcquireConnection retourne un `System.Data.OleDb.OleDbConnection` au lieu d’un objet non managé. Pour configurer un gestionnaire de connexions [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] en vue de son utilisation avec une source de données Excel, sélectionnez le fournisseur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB pour Jet, spécifiez un fichier Excel, puis entrez `Excel 8.0` (pour Excel 97 et versions ultérieures) comme valeur **Propriétés étendues** dans la page **Tout** de la boîte de dialogue **Gestionnaire de connexions**.  
  
## <a name="connections-example"></a>Exemple de connexions  
 L'exemple suivant montre comment accéder aux gestionnaires de connexions à partir de la tâche de script. Il est supposé dans l’exemple que vous avez créé et configuré un gestionnaire de connexions [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] nommé **Connexion ADO.NET test** et un gestionnaire de connexions de fichiers plats nommé **Connexion de fichiers plats test**. Notez que le gestionnaire de connexions [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] retourne un objet `SqlConnection` que vous pouvez utiliser immédiatement pour vous connecter à la source de données. Le gestionnaire de connexions de fichiers plats, en revanche, retourne uniquement une chaîne qui contient le chemin d'accès et le nom du fichier. Vous devez utiliser les méthodes de l'espace de noms `System.IO` pour ouvrir et utiliser le fichier plat.  
  
```vb  
Public Sub Main()  
  
    Dim myADONETConnection As SqlClient.SqlConnection  
    myADONETConnection = _  
        DirectCast(Dts.Connections("Test ADO.NET Connection").AcquireConnection(Dts.Transaction), _  
        SqlClient.SqlConnection)  
    MsgBox(myADONETConnection.ConnectionString, _  
        MsgBoxStyle.Information, "ADO.NET Connection")  
  
    Dim myFlatFileConnection As String  
    myFlatFileConnection = _  
        DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _  
        String)  
    MsgBox(myFlatFileConnection, MsgBoxStyle.Information, "Flat File Connection")  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
  
public class ScriptMain  
{  
  
        public void Main()  
        {  
            SqlConnection myADONETConnection = new SqlConnection();  
            myADONETConnection = (SqlConnection)(Dts.Connections["Test ADO.NET Connection"].AcquireConnection(Dts.Transaction)as SqlConnection);  
            MessageBox.Show(myADONETConnection.ConnectionString, "ADO.NET Connection");  
  
            string myFlatFileConnection;  
            myFlatFileConnection = (string)(Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);  
            MessageBox.Show(myFlatFileConnection, "Flat File Connection");  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
  
```  
  
![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40;les connexions de&#41; SSIS](../../connection-manager/integration-services-ssis-connections.md)   
 [Créer des gestionnaires de connexions](../../create-connection-managers.md)  
  
  
