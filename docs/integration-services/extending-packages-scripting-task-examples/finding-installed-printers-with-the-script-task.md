---
title: "Recherche d’imprimantes installées avec la tâche de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- System.Drawing.Printing namespace
- printers [Integration Services]
- SSIS Script task, printers
- locating printers
- Printing namespace
- Script task [Integration Services], examples
- finding printers [SQL Server]
- Script task [Integration Services], printers
ms.assetid: 50a55014-e2c3-4ecd-84e1-3e877c55a260
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 1de1fae5c30648eba7cb62840ef3ff9f9aac13f9
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="finding-installed-printers-with-the-script-task"></a>Recherche d'imprimantes installées à l'aide de la tâche de script
  La destination finale des données transformées par les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est souvent un rapport imprimé. Le **System.Drawing.Printing** espace de noms dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] fournit des classes pour l’utilisation d’imprimantes.  
  
> [!NOTE]  
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a> Description  
 L'exemple suivant recherche les imprimantes installées sur le serveur qui prennent en charge le format de papier standard (utilisé en France). Le code permettant de vérifier les formats de papier pris en charge est encapsulé dans une fonction privée. Pour vous permettre de suivre la progression du script pendant qu'il vérifie les paramètres de chaque imprimante, le script utilise la méthode <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> qui déclenche un message d'information pour les imprimantes qui utilisent le format de papier standard et un avertissement pour les imprimantes qui ne l'utilisent pas. Ces messages apparaissent dans le **sortie** fenêtre de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE lorsque vous exécutez le package dans le concepteur.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Créez la variable nommée `PrinterList` avec le type **objet**.  
  
2.  Sur le **Script** page de la **éditeur de tâche de Script**, ajoutez cette variable à la propriété ReadWriteVariables.  
  
3.  Dans le projet de script, ajoutez une référence à la **System.Drawing** espace de noms.  
  
4.  Dans votre code, utilisez **importations** instructions pour importer le **System.Collections** et **System.Drawing.Printing** espaces de noms.  
  
### <a name="code"></a>Code  
  
```vb  
Public Sub Main()  
  
    Dim printerName As String  
    Dim currentPrinter As New PrinterSettings  
    Dim size As PaperSize  
  
    Dim printerList As New ArrayList  
    For Each printerName In PrinterSettings.InstalledPrinters  
        currentPrinter.PrinterName = printerName  
        If PrinterHasLegalPaper(currentPrinter) Then  
            printerList.Add(printerName)  
            Dts.Events.FireInformation(0, "Example", _  
                "Printer " & printerName & " has legal paper.", _  
                String.Empty, 0, False)  
        Else  
            Dts.Events.FireWarning(0, "Example", _  
                "Printer " & printerName & " DOES NOT have legal paper.", _  
                String.Empty, 0)  
        End If  
    Next  
  
    Dts.Variables("PrinterList").Value = printerList  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
  
Private Function PrinterHasLegalPaper( _  
    ByVal thisPrinter As PrinterSettings) As Boolean  
  
    Dim size As PaperSize  
    Dim hasLegal As Boolean = False  
  
    For Each size In thisPrinter.PaperSizes  
        If size.Kind = PaperKind.Legal Then  
            hasLegal = True  
        End If  
    Next  
  
    Return hasLegal  
  
End Function  
```  
  
```csharp  
public void Main()  
        {  
  
            PrinterSettings currentPrinter = new PrinterSettings();  
            PaperSize size;  
            Boolean Flag = false;  
  
            ArrayList printerList = new ArrayList();  
            foreach (string printerName in PrinterSettings.InstalledPrinters)  
            {  
                currentPrinter.PrinterName = printerName;  
                if (PrinterHasLegalPaper(currentPrinter))  
                {  
                    printerList.Add(printerName);  
                    Dts.Events.FireInformation(0, "Example", "Printer " + printerName + " has legal paper.", String.Empty, 0, ref Flag);  
                }  
                else  
                {  
                    Dts.Events.FireWarning(0, "Example", "Printer " + printerName + " DOES NOT have legal paper.", String.Empty, 0);  
                }  
            }  
  
            Dts.Variables["PrinterList"].Value = printerList;  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
        private bool PrinterHasLegalPaper(PrinterSettings thisPrinter)  
        {  
  
            bool hasLegal = false;  
  
            foreach (PaperSize size in thisPrinter.PaperSizes)  
            {  
                if (size.Kind == PaperKind.Legal)  
                {  
                    hasLegal = true;  
                }  
            }  
  
            return hasLegal;  
  
        }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de tâche de script](../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)  
  
  

