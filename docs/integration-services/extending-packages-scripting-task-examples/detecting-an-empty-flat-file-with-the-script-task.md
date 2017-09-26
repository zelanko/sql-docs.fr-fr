---
title: "Détection d’un fichier plat vide avec la tâche de Script | Documents Microsoft"
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
helpviewer_keywords:
- flat files
- Script task [Integration Services], empty flat files
- SSIS Script task, empty flat files
- Script task [Integration Services], examples
ms.assetid: 1b4defb8-886a-483d-8056-d1b91d37bc90
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 40deae6a08a597114fbc721271a789895e1d8fa2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="detecting-an-empty-flat-file-with-the-script-task"></a>Détection d'un fichier plat vide à l'aide de la tâche de script
  La source de fichier plat ne détermine pas si un fichier plat contient des lignes de données avant de tenter de les traiter. Vous pouvez améliorer l'efficacité d'un package, notamment d'un package qui parcourt de nombreux fichiers plats, en ignorant les fichiers qui ne contiennent aucune ligne de données. La tâche de script peut rechercher un fichier plat vide avant que le package ne commence à traiter le flux de données.  
  
> [!NOTE]  
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a> Description  
 L’exemple suivant utilise des méthodes de la **System.IO** espace de noms pour tester le fichier plat spécifié dans un gestionnaire de connexions de fichier plat pour déterminer si le fichier est vide, ou s’il contient uniquement attendu de lignes de données non-tels que les en-têtes de colonne ou une ligne vide. Le script vérifie d'abord la taille du fichier ; une taille de zéro octets indique que le fichier est vide. Si la taille du fichier est supérieure à zéro, le script lit les lignes du fichier jusqu'à la dernière, ou jusqu'à ce que le nombre de lignes dépasse le nombre attendu de lignes ne correspondant pas à des données. Si le nombre de lignes dans le fichier est inférieur ou égal au nombre attendu de lignes ne correspondant pas à des données, le fichier est considéré comme vide. Le résultat est retourné sous la forme d'une valeur booléenne dans une variable utilisateur, dont la valeur peut être utilisée pour le branchement du flux de contrôle du package. Le **FireInformation** méthode affiche également le résultat dans le **sortie** fenêtre de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Créer et configurer un gestionnaire de connexions de fichier plat nommé **EmptyFlatFileTest**.  
  
2.  Créez une variable de type entier appelée `FFNonDataRows` et attribuez-lui une valeur égale au nombre attendu de lignes ne correspondant pas à des données dans le fichier plat.  
  
3.  Créez une variable booléenne appelée `FFIsEmpty`.  
  
4.  Ajouter le `FFNonDataRows` variable à la tâche de Script **ReadOnlyVariables** propriété.  
  
5.  Ajouter le `FFIsEmpty` variable à la tâche de Script **ReadWriteVariables** propriété.  
  
6.  Dans votre code, importez le **System.IO** espace de noms.  
  
 Si vous parcourez les fichiers avec un énumérateur Foreach File, au lieu d'utiliser un seul gestionnaire de connexions de fichiers plats, vous devez modifier l'exemple de code ci-dessous pour obtenir le nom et le chemin d'accès du fichier à partir de la variable dans laquelle la valeur énumérée est stockée et non à partir du gestionnaire de connexions.  
  
### <a name="code"></a>Code  
  
```vb  
Public Sub Main()  
  
  Dim nonDataRows As Integer = _  
      DirectCast(Dts.Variables("FFNonDataRows").Value, Integer)  
  Dim ffConnection As String = _  
      DirectCast(Dts.Connections("EmptyFlatFileTest").AcquireConnection(Nothing), _  
      String)  
  Dim flatFileInfo As New FileInfo(ffConnection)  
  ' If file size is 0 bytes, flat file does not contain data.  
  Dim fileSize As Long = flatFileInfo.Length  
  If fileSize > 0 Then  
    Dim lineCount As Integer = 0  
    Dim line As String  
    Dim fsFlatFile As New StreamReader(ffConnection)  
    Do Until fsFlatFile.EndOfStream  
      line = fsFlatFile.ReadLine  
      lineCount += 1  
      ' If line count > expected number of non-data rows,  
      '  flat file contains data (default value).  
      If lineCount > nonDataRows Then  
        Exit Do  
      End If  
      ' If line count <= expected number of non-data rows,  
      '  flat file does not contain data.  
      If lineCount <= nonDataRows Then  
        Dts.Variables("FFIsEmpty").Value = True  
      End If  
    Loop  
  Else  
    Dts.Variables("FFIsEmpty").Value = True  
  End If  
  
  Dim fireAgain As Boolean = False  
  Dts.Events.FireInformation(0, "Script Task", _  
      String.Format("{0}: {1}", ffConnection, _  
      Dts.Variables("FFIsEmpty").Value.ToString), _  
      String.Empty, 0, fireAgain)  
  
  Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
public void Main()  
        {  
  
            int nonDataRows = (int)(Dts.Variables["FFNonDataRows"].Value);  
            string ffConnection = (string)(Dts.Connections["EmptyFlatFileTest"].AcquireConnection(null) as String);  
            FileInfo flatFileInfo = new FileInfo(ffConnection);  
            // If file size is 0 bytes, flat file does not contain data.  
            long fileSize = flatFileInfo.Length;  
            if (fileSize > 0)  
            {  
  
                int lineCount = 0;  
                string line;  
                StreamReader fsFlatFile = new StreamReader(ffConnection);  
                while (!(fsFlatFile.EndOfStream))  
                {  
                    Console.WriteLine (fsFlatFile.ReadLine());  
                    lineCount += 1;  
                    // If line count > expected number of non-data rows,  
                    //  flat file contains data (default value).  
                    if (lineCount > nonDataRows)  
                    {  
                        break;  
                    }  
                    // If line count <= expected number of non-data rows,  
                    //  flat file does not contain data.  
                    if (lineCount <= nonDataRows)  
                    {  
                        Dts.Variables["FFIsEmpty"].Value = true;  
                    }  
                }  
            }  
            else  
            {  
                Dts.Variables["FFIsEmpty"].Value = true;  
            }  
  
            bool fireAgain = false;  
            Dts.Events.FireInformation(0, "Script Task", String.Format("{0}: {1}", ffConnection, Dts.Variables["FFIsEmpty"].Value), String.Empty, 0, ref fireAgain);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de tâche de script](../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)  
  
  
