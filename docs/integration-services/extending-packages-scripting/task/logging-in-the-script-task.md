---
title: "Journalisation dans la tâche de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- logs [Integration Services], scripts
- Integration Services packages, logs
- Log method
- SSIS Script task, logs
- Script task [Integration Services], logs
- packages [Integration Services], logs
ms.assetid: 2e11fc15-df18-4309-bd2d-fc58aa4b9b7a
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 98859dafe0b023954f10239fe11e8b76f36ab28b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="logging-in-the-script-task"></a>Journalisation dans la tâche de script
  L’utilisation de la journalisation dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] permet de packages que vous enregistrez des informations détaillées sur des problèmes, les résultats et la progression de l’exécution en enregistrant des événements prédéfinis ou des messages définis par l’utilisateur pour une analyse ultérieure. La tâche de Script peut utiliser le <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> méthode de la **Dts** objet pour enregistrer les données définies par l’utilisateur. Si la journalisation est activée et le **ScriptTaskLogEntry** événement est sélectionné pour la journalisation le **détails** onglet de la **configurer les journaux SSIS** boîte de dialogue, un seul appel à la <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> méthode stocke les informations sur les événements de tous les modules fournisseurs d’informations configurés pour la tâche.  
  
> [!NOTE]  
>  Bien qu'il soit possible d'exécuter la journalisation directement à partir de la tâche de script, il peut être préférable d'implémenter des événements plutôt que la journalisation. Lors de l’utilisation des événements, non seulement vous pouvez activer la journalisation des messages d’événement, mais vous pouvez également répondre à l’événement par défaut ou les gestionnaires d’événements définis par l’utilisateur.  
  
 Pour plus d’informations sur la journalisation, consultez [Integration Services &#40; SSIS &#41; Journalisation](../../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="logging-example"></a>Exemple de journalisation  
 L'exemple suivant montre la journalisation d'une valeur représentant le nombre de lignes traitées à partir de la tâche de script.  
  
```vb  
Public Sub Main()  
  
    Dim rowsProcessed As Integer = 100  
    Dim emptyBytes(0) As Byte  
  
    Try  
        Dts.Log("Rows processed: " & rowsProcessed.ToString, _  
            0, _  
            emptyBytes)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
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
            //  
            int rowsProcessed = 100;  
            byte[] emptyBytes = new byte[0];  
  
            try  
            {  
                Dts.Log("Rows processed: " + rowsProcessed.ToString(), 0, emptyBytes);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                //An error occurred.  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
```  
  
 }  
  
## <a name="external-resources"></a>Ressources externes  
  
-   Entrée de blog, [journalisation des événements personnalisés pour les tâches Integration Services](http://go.microsoft.com/fwlink/?LinkId=165644), sur dougbert.com  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40; SSIS &#41; Journalisation](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  

