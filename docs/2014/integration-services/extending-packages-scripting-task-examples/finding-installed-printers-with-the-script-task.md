---
title: Recherche d’imprimantes installées à l’aide de la tâche de script | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 956a73f76e113eb0a50f628150e47ed33791cc97
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176238"
---
# <a name="finding-installed-printers-with-the-script-task"></a>Recherche d'imprimantes installées à l'aide de la tâche de script
  La destination finale des données transformées par les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est souvent un rapport imprimé. L' `System.Drawing.Printing` espace de noms [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] dans le fournit des classes pour l’utilisation des imprimantes.

> [!NOTE]
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../extending-packages-custom-objects/task/developing-a-custom-task.md).

## <a name="description"></a>Description
 L'exemple suivant recherche les imprimantes installées sur le serveur qui prennent en charge le format de papier standard (utilisé en France). Le code permettant de vérifier les formats de papier pris en charge est encapsulé dans une fonction privée. Pour vous permettre de suivre la progression du script pendant qu'il vérifie les paramètres de chaque imprimante, le script utilise la méthode <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> qui déclenche un message d'information pour les imprimantes qui utilisent le format de papier standard et un avertissement pour les imprimantes qui ne l'utilisent pas. Ces messages apparaissent dans la fenêtre **Sortie** de l’environnement de développement intégré [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) lorsque vous exécutez le package dans le concepteur.

#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script

1.  Créez la variable nommée `PrinterList` avec le type `Object`.

2.  Dans la page **Script** de l’**Éditeur de tâche de script**, ajoutez cette variable à la propriété ReadWriteVariables.

3.  Dans le projet de script, ajoutez une référence à l’espace de noms **System.Xml**.

4.  Dans votre code, utilisez `Imports` des instructions pour importer les **System. Collections** et `System.Drawing.Printing` les espaces de noms.

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

![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.

## <a name="see-also"></a>Voir aussi
 [Exemples de tâche de script](../extending-packages-scripting-task-examples/script-task-examples.md)


