---
title: "Connexion aux Sources de données dans la tâche de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
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
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 825ff059476614085a338dd9c568031885bed64b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="connecting-to-data-sources-in-the-script-task"></a>Connexion à des sources de données dans la tâche de script
  Les gestionnaires de connexions fournissent un accès à des sources de données qui ont été configurées dans le package. Pour plus d’informations, consultez [Connexions Integration Services &#40;SSIS&#41;](../../../integration-services/connection-manager/integration-services-ssis-connections.md).  
  
 La tâche de Script peut accéder à ces gestionnaires de connexions via la <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> propriété de la **Dts** objet. Chaque gestionnaire de connexions compris dans la collection <xref:Microsoft.SqlServer.Dts.Runtime.Connections> stocke des informations sur la manière d'établir une connexion à la source de données sous-jacente.  
  
 Lorsque vous appelez la méthode <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> d'un gestionnaire de connexions, le gestionnaire de connexions se connecte à la source de données, s'il n'est pas déjà connecté, puis renvoie la connexion ou les informations de connexion appropriées que vous devez utiliser dans le code de votre tâche de script.  
  
> [!NOTE]  
>  Vous devez connaître le type de connexion renvoyé par le Gestionnaire de connexions avant d’appeler **AcquireConnection**. Étant donné que la tâche de Script a **Option Strict** activé, vous devez caster la connexion, ce qui est retournée en tant que type **objet**, pour le type de connexion approprié avant que vous puissiez l’utiliser.  
  
 Vous pouvez utiliser la méthode <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> de la collection <xref:Microsoft.SqlServer.Dts.Runtime.Connections> renvoyée par la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> pour rechercher une connexion existante avant d'utiliser la connexion dans votre code.  
  
> [!IMPORTANT]  
>  Vous ne pouvez pas appeler la méthode AcquireConnection des gestionnaires de connexions qui retournent des objets non managés, tels que le Gestionnaire de connexions OLE DB et le Gestionnaire de connexions Excel, dans le code managé d’une tâche de Script. Toutefois, vous pouvez lire la propriété ConnectionString de ces gestionnaires de connexions et vous connecter à la source de données directement dans votre code à l’aide de la chaîne de connexion avec un **OledbConnection** à partir de la **System.Data.OleDb** espace de noms.  
>   
>  Si vous devez appeler la méthode AcquireConnection d’une connexion de gestionnaire qui retourne un objet non managé, utilisez un [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] Gestionnaire de connexions. Lorsque vous configurez le gestionnaire de connexions [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] afin d'utiliser un fournisseur OLE DB, il se connecte en utilisant le fournisseur de données [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] pour OLE DB. Dans ce cas, la méthode AcquireConnection retourne un **System.Data.OleDb.OleDbConnection** au lieu d’un objet non managé. Pour configurer un [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] Gestionnaire de connexions pour une utilisation avec une source de données Excel, sélectionnez le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] fournisseur OLE DB pour Jet, spécifiez un fichier Excel, puis entrez `Excel 8.0` (pour Excel 97 et versions ultérieures) comme valeur de **propriétés étendues** sur la **tous les** page de la **Gestionnaire de connexions** boîte de dialogue.  
  
## <a name="connections-example"></a>Exemple de connexions  
 L'exemple suivant montre comment accéder aux gestionnaires de connexions à partir de la tâche de script. L’exemple part du principe que vous avez créé et configuré un [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] Gestionnaire de connexions nommé **connexion ADO.NET Test** et un gestionnaire de connexions de fichier plat nommé **connexion de fichiers plats Test**. Notez que la [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] Gestionnaire de connexions renvoie un **SqlConnection** objet que vous pouvez utiliser immédiatement pour se connecter à la source de données. Le gestionnaire de connexions de fichiers plats, en revanche, retourne uniquement une chaîne qui contient le chemin d'accès et le nom du fichier. Vous devez utiliser les méthodes de la **System.IO** espace de noms pour l’ouvrir et travailler avec le fichier plat.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40; SSIS &#41; Connexions](../../../integration-services/connection-manager/integration-services-ssis-connections.md)   
 [Créer des gestionnaires de connexions](http://msdn.microsoft.com/library/6ca317b8-0061-4d9d-b830-ee8c21268345)  
  
  
