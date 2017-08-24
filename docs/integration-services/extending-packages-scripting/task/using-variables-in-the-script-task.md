---
title: "Utilisation de Variables dans la tâche de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
caps.latest.revision: 63
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ccfd7ce8e8f53d12dac3b021d5f62bd03947413d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="using-variables-in-the-script-task"></a>Utilisation de variables dans la tâche de script
  Les variables permettent à la tâche de script d'échanger des données avec d'autres objets dans le package. Pour plus d’informations, consultez [Integration Services &#40;SSIS&#41; Variables](../../../integration-services/integration-services-ssis-variables.md).  
  
 La tâche de Script utilise le <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> propriété de la **Dts** objet à lire et écrire à <xref:Microsoft.SqlServer.Dts.Runtime.Variable> objets dans le package.  
  
> [!NOTE]  
>  Le <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> propriété de la <xref:Microsoft.SqlServer.Dts.Runtime.Variable> classe est de type **objet**. Étant donné que la tâche de Script a **Option Strict** activé, vous devez effectuer un cast du <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> propriété vers le type approprié avant que vous puissiez l’utiliser.  
  
 Vous ajoutez des variables existantes pour le <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> et <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> répertorie dans le **éditeur de tâche de Script** pour les rendre disponibles pour le script personnalisé. N'oubliez pas que les noms de variables respectent la casse. Dans le script, vous accéder aux variables des deux types via la <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> propriété de la **Dts** objet. Utilisez le **valeur** propriété en lecture et en écriture aux variables individuelles. La tâche de script gère de façon transparente le verrouillage pendant que le script lit et modifie les valeurs des variables.  
  
 La méthode <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> de la collection <xref:Microsoft.SqlServer.Dts.Runtime.Variables> retournée par la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> vous permet de vérifier l'existence d'une variable avant de l'utiliser dans votre code.  
  
 Vous pouvez également utiliser le <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> propriété (Dts.VariableDispenser) pour utiliser des variables dans la tâche de Script. Lorsque vous utilisez la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, vous devez gérer à la fois la sémantique de verrouillage et la conversion des types de données pour les valeurs de variables dans votre propre code. Vous pourriez devoir utiliser la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> à la place de la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> si vous souhaitez utiliser une variable qui n'est pas disponible au moment de la conception mais qui est créée par programme au moment de l'exécution.  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a>Utilisation de la tâche de script dans un conteneur de boucles Foreach  
 Lorsqu'une tâche de script s'exécute à plusieurs reprises dans un conteneur de boucles Foreach, le script doit généralement utiliser le contenu de l'élément actif dans l'énumérateur. Par exemple, lors de l'utilisation d'un énumérateur Foreach File, le script doit connaître le nom du fichier actif ; lors de l'utilisation d'un énumérateur ADO Foreach, le script doit connaître le contenu des colonnes dans la ligne de données en cours.  
  
 Les variables permettent d'établir cette communication entre le conteneur de boucles Foreach et la tâche de script. Sur le **mappages de variables** page de la **éditeur de boucle Foreach**, affecter des variables à chaque élément de données qui sont retournées par un seul élément énuméré. Par exemple, un énumérateur Foreach File retourne uniquement un nom de fichier à l'index 0 et ne requiert donc qu'un seul mappage de variables, alors qu'un énumérateur qui retourne plusieurs colonnes de données dans chaque ligne requiert que vous mappiez une variable différente à chaque colonne que vous souhaitez utiliser dans la tâche de script.  
  
 Après avoir mappé les éléments énumérés aux variables, vous devez ajouter les variables mappées à la **ReadOnlyVariables** propriété sur le **Script** page de la **éditeur de tâche de Script** pour les rendre disponibles pour votre script. Pour obtenir un exemple d’une tâche de Script dans un conteneur de boucle Foreach qui traite les fichiers image dans un dossier, consultez [utilisation des Images avec la tâche de Script](../../../integration-services/extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md).  
  
## <a name="variables-example"></a>Exemple de variables  
 L'exemple suivant montre comment accéder à des variables et les utiliser dans une tâche de script pour déterminer le chemin d'accès du flux de travail du package. L’exemple part du principe que vous avez créé des variables de type entier nommées `CustomerCount` et `MaxRecordCount` et ajoutées à la **ReadOnlyVariables** collection dans le **éditeur de tâche de Script**. La variable `CustomerCount` contient le nombre d'enregistrements de client à importer. Si sa valeur est supérieure à la valeur de `MaxRecordCount`, la tâche de script signale une défaillance. Lorsqu'une défaillance se produit en raison du dépassement du seuil `MaxRecordCount`, le chemin d'accès aux erreurs du flux de travail peut implémenter les opérations de nettoyage requises.  
  
 Pour compiler correctement l'exemple, vous devez ajouter une référence à l'assembly Microsoft.SqlServer.ScriptTask.  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
    {  
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40; SSIS &#41; Variables](../../../integration-services/integration-services-ssis-variables.md)   
 [Utiliser des Variables dans des Packages](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  
