---
title: "Création d’une liste de la boucle ForEach avec la tâche de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- Foreach Loop containers
- Script task [Integration Services], Foreach loops
- Script task [Integration Services], examples
- SSIS Script task, Foreach loops
ms.assetid: 694f0462-d0c5-4191-b64e-821b1bdef055
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b1bd133c2fdc8c500db9c07df9c54e954db327bf
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="gathering-a-list-for-the-foreach-loop-with-the-script-task"></a>Création d'une liste pour la boucle Foreach à l'aide de la tâche de script
  L'énumérateur Foreach à partir d'une variable énumère les éléments d'une liste qui lui est transmise via une variable et effectue les mêmes tâches sur chaque élément. Vous pouvez utiliser le code personnalisé dans une tâche de script pour remplir une liste à cet effet. Pour plus d’informations sur l’énumérateur, consultez [conteneur de boucles Foreach](../../integration-services/control-flow/foreach-loop-container.md).  
  
> [!NOTE]  
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a> Description  
 L’exemple suivant utilise des méthodes de la **System.IO** espace de noms pour dresser la liste des classeurs Excel sur l’ordinateur qui sont antérieurs à un nombre de jours spécifié par l’utilisateur dans une variable ou plus récents. Il effectue une recherche récursive dans les répertoires du lecteur C pour trouver des fichiers dotés de l'extension .xls et examine la date de dernière modification de chaque fichier pour déterminer s'il appartient à la liste. Il ajoute les fichiers éligibles à une **ArrayList** et enregistre le **ArrayList** à une variable pour une utilisation ultérieure dans un conteneur de boucle Foreach. Le conteneur de boucles Foreach est configuré pour utiliser l'énumérateur Foreach à partir d'une variable.  
  
> [!NOTE]  
>  La variable que vous utilisez avec l’énumérateur Foreach à partir Variable doit être de type **objet**. L’objet que vous placez dans la variable doit implémenter l’une des interfaces suivantes : **pas ' System.Collections.IEnumerable '**, **System.Runtime.InteropServices.ComTypes.IEnumVARIANT**, **System.ComponentModel IListSource**, ou **Microsoft.SqlServer.Dts.Runtime.Wrapper.ForEachEnumeratorHost**. Un **tableau** ou **ArrayList** est couramment utilisé. Le **ArrayList** requiert une référence et un **importations** instruction pour le **System.Collections** espace de noms.  
  
 Vous pouvez apprendre à manipuler cette tâche en attribuant différentes valeurs, positives et négatives, à la variable de package `FileAge`. Par exemple, vous pouvez entrer 5 pour rechercher les fichiers créés au cours des cinq derniers jours ou entrer -3 pour rechercher les fichiers créés il y a plus de trois jours. Cette tâche peut prendre une minute ou deux sur un lecteur contenant de nombreux dossiers à rechercher.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Créez une variable de package nommée `FileAge` de type entier et entrez une valeur entière positive ou négative. Selon que la valeur est positive ou négative, le code recherche respectivement les fichiers postérieurs ou antérieurs à la date spécifiée (en nombre de jours).  
  
2.  Créez une variable de package nommée `FileList` de type **objet** pour recevoir la liste de fichiers dressée par la tâche de Script pour une utilisation ultérieure par Foreach à partir de l’énumérateur de la Variable.  
  
3.  Ajouter le `FileAge` variable à la tâche de Script **ReadOnlyVariables** propriété et ajouter la `FileList` variable à la **ReadWriteVariables** propriété.  
  
4.  Dans votre code, importez le **System.Collections** et **System.IO** espaces de noms.  
  
### <a name="code"></a>Code  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Collections  
Imports System.IO  
  
Public Class ScriptMain  
  
  Private Const FILE_AGE As Integer = -50  
  
  Private Const FILE_ROOT As String = "C:\"  
  Private Const FILE_FILTER As String = "*.xls"  
  
  Private isCheckForNewer As Boolean = True  
  Dim fileAgeLimit As Integer  
  Private listForEnumerator As ArrayList  
  
  Public Sub Main()  
  
    fileAgeLimit = DirectCast(Dts.Variables("FileAge").Value, Integer)  
  
    ' If value provided is positive, we want files NEWER THAN n days.  
    '  If negative, we want files OLDER THAN n days.  
    If fileAgeLimit < 0 Then  
      isCheckForNewer = False  
    End If  
    ' Extract number of days as positive integer.  
    fileAgeLimit = Math.Abs(fileAgeLimit)  
  
    listForEnumerator = New ArrayList  
  
    GetFilesInFolder(FILE_ROOT)  
  
    ' Return the list of files to the variable  
    '  for later use by the Foreach from Variable enumerator.  
    System.Windows.Forms.MessageBox.Show("Matching files: " & listForEnumerator.Count.ToString, "Results", Windows.Forms.MessageBoxButtons.OK, Windows.Forms.MessageBoxIcon.Information)  
    Dts.Variables("FileList").Value = listForEnumerator  
  
    Dts.TaskResult = ScriptResults.Success  
  
  End Sub  
  
  Private Sub GetFilesInFolder(ByVal folderPath As String)  
  
    Dim localFiles() As String  
    Dim localFile As String  
    Dim fileChangeDate As Date  
    Dim fileAge As TimeSpan  
    Dim fileAgeInDays As Integer  
    Dim childFolder As String  
  
    Try  
      localFiles = Directory.GetFiles(folderPath, FILE_FILTER)  
      For Each localFile In localFiles  
        fileChangeDate = File.GetLastWriteTime(localFile)  
        fileAge = DateTime.Now.Subtract(fileChangeDate)  
        fileAgeInDays = fileAge.Days  
        CheckAgeOfFile(localFile, fileAgeInDays)  
      Next  
  
      If Directory.GetDirectories(folderPath).Length > 0 Then  
        For Each childFolder In Directory.GetDirectories(folderPath)  
          GetFilesInFolder(childFolder)  
        Next  
      End If  
  
    Catch  
      ' Ignore exceptions on special folders such as System Volume Information.  
    End Try  
  
  End Sub  
  
  Private Sub CheckAgeOfFile(ByVal localFile As String, ByVal fileAgeInDays As Integer)  
  
    If isCheckForNewer Then  
      If fileAgeInDays <= fileAgeLimit Then  
        listForEnumerator.Add(localFile)  
      End If  
    Else  
      If fileAgeInDays > fileAgeLimit Then  
        listForEnumerator.Add(localFile)  
      End If  
    End If  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Math;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Collections;  
using System.IO;  
  
public partial class ScriptMain : Microsoft.SqlServer.Dts.Tasks.ScriptTask.VSTARTScriptObjectModelBase  
    {  
  
        private const int FILE_AGE = -50;  
  
        private const string FILE_ROOT = "C:\\";  
        private const string FILE_FILTER = "*.xls";  
  
        private bool isCheckForNewer = true;  
        int fileAgeLimit;  
        private ArrayList listForEnumerator;  
  
        public void Main()  
  {  
  
    fileAgeLimit = (int)(Dts.Variables["FileAge"].Value);  
  
    // If value provided is positive, we want files NEWER THAN n days.  
    // If negative, we want files OLDER THAN n days.  
    if (fileAgeLimit<0)  
    {  
      isCheckForNewer = false;  
    }  
    // Extract number of days as positive integer.  
    fileAgeLimit = Math.Abs(fileAgeLimit);  
  
    ArrayList listForEnumerator = new ArrayList();  
  
    GetFilesInFolder(FILE_ROOT);  
  
    // Return the list of files to the variable  
    // for later use by the Foreach from Variable enumerator.  
    System.Windows.Forms.MessageBox.Show("Matching files: "+ listForEnumerator.Count, "Results",   
MessageBoxButtons.OK, MessageBoxIcon.Information);  
    Dts.Variables["FileList"].Value = listForEnumerator;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  
  }  
  
        private void GetFilesInFolder(string folderPath)  
        {  
  
            string[] localFiles;  
            DateTime fileChangeDate;  
            TimeSpan fileAge;  
            int fileAgeInDays;  
  
            try  
            {  
                localFiles = Directory.GetFiles(folderPath, FILE_FILTER);  
                foreach (string localFile in localFiles)  
                {  
                    fileChangeDate = File.GetLastWriteTime(localFile);  
                    fileAge = DateTime.Now.Subtract(fileChangeDate);  
                    fileAgeInDays = fileAge.Days;  
                    CheckAgeOfFile(localFile, fileAgeInDays);  
                }  
  
                if (Directory.GetDirectories(folderPath).Length > 0)  
                {  
                    foreach (string childFolder in Directory.GetDirectories(folderPath))  
                    {  
                        GetFilesInFolder(childFolder);  
                    }  
                }  
  
            }  
            catch  
            {  
                // Ignore exceptions on special folders, such as System Volume Information.  
            }  
  
        }  
  
        private void CheckAgeOfFile(string localFile, int fileAgeInDays)  
        {  
  
            if (isCheckForNewer)  
            {  
                if (fileAgeInDays <= fileAgeLimit)  
                {  
                    listForEnumerator.Add(localFile);  
                }  
            }  
            else  
            {  
                if (fileAgeInDays > fileAgeLimit)  
                {  
                    listForEnumerator.Add(localFile);  
                }  
            }  
  
        }  
  
    }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneur de boucles foreach](../../integration-services/control-flow/foreach-loop-container.md)   
 [Configurer un conteneur de boucles Foreach](http://msdn.microsoft.com/library/519c6f96-5e1f-47d2-b96a-d49946948c25)  
  
  
