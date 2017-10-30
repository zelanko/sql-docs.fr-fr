---
title: "Interrogation d’Active Directory avec la tâche de Script | Documents Microsoft"
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
- Script task [Integration Services], Active Directory access
- SSIS Script task, Active Directory access
- Script task [Integration Services], examples
- Active Directory [Integration Services]
ms.assetid: a88fefbb-9ea2-4a86-b836-e71315bac68e
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ee5a82829785e78554b105e1f3bf3bd24f05b778
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="querying-the-active-directory-with-the-script-task"></a>Interrogation d'Active Directory avec la tâche de script
  Les applications de traitement des données d'entreprise, telles que les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], ont souvent besoin de traiter des données différemment selon l'échelon, le poste ou d'autres caractéristiques des employés stockés dans Active Directory. Active Directory est un [!INCLUDE[msCoName](../../includes/msconame-md.md)] service d’annuaire Windows qui fournit un magasin centralisé de métadonnées, non seulement sur les utilisateurs, mais également sur d’autres ressources organisationnelles telles que les ordinateurs et les imprimantes. Le **System.DirectoryServices** espace de noms dans Microsoft .NET Framework fournit des classes pour travailler avec Active Directory, pour vous aider à direct le traitement des données de flux de travail basé sur les informations qu’elle stocke.  
  
> [!NOTE]  
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a> Description  
 L'exemple suivant extrait le nom, le titre et le numéro de téléphone d'un employé dans Active Directory selon la valeur de la variable `email`, laquelle contient l'adresse de messagerie de l'employé. Les contraintes de précédence dans le package peuvent utiliser les informations extraites pour déterminer, par exemple, s'il faut envoyer un message électronique de priorité basse ou une page prioritaire, selon la fonction de l'employé.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Créez les trois variables de chaîne `email`, `name` et `title`. Entrez une adresse de messagerie professionnelle valide en tant que valeur de la variable `email`.  
  
2.  Sur le **Script** page de la **éditeur de tâche de Script**, ajouter le `email` variable à la **ReadOnlyVariables** propriété.  
  
3.  Ajouter le `name` et `title` variables à la **ReadWriteVariables** propriété.  
  
4.  Dans le projet de script, ajoutez une référence à la **System.DirectoryServices** espace de noms.  
  
5.  . Dans votre code, utilisez une **importations** statement pour importer le **DirectoryServices** espace de noms.  
  
> [!NOTE]  
>  Pour exécuter ce script correctement, votre entreprise doit utiliser Active Directory sur son réseau et stocker les informations sur l'employé que cet exemple utilise.  
  
### <a name="code"></a>Code  
  
```vb  
Public Sub Main()  
  
    Dim directory As DirectoryServices.DirectorySearcher  
    Dim result As DirectoryServices.SearchResult  
    Dim email As String  
  
    email = Dts.Variables("email").Value.ToString  
  
    Try  
        directory = New _  
            DirectoryServices.DirectorySearcher("(mail=" & email & ")")  
        result = directory.FindOne  
        Dts.Variables("name").Value = _  
            result.Properties("displayname").ToString  
        Dts.Variables("title").Value = _  
            result.Properties("title").ToString  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
public void Main()  
{  
    //  
    DirectorySearcher directory;  
    SearchResult result;  
    string email;  
  
    email = (string)Dts.Variables["email"].Value;  
  
    try  
    {  
        directory = new DirectorySearcher("(mail=" + email + ")");  
        result = directory.FindOne();  
        Dts.Variables["name"].Value = result.Properties["displayname"].ToString();  
        Dts.Variables["title"].Value = result.Properties["title"].ToString();  
        Dts.TaskResult = (int)ScriptResults.Success;  
    }  
    catch (Exception ex)  
    {  
        Dts.Events.FireError(0, "Script Task Example", ex.Message + "\n" + ex.StackTrace, String.Empty, 0);  
        Dts.TaskResult = (int)ScriptResults.Failure;  
    }  
  
}  
```  
  
## <a name="external-resources"></a>Ressources externes  
  
-   Article technique, [Processing Active Directory Information in SSIS](http://go.microsoft.com/fwlink/?LinkId=199588), sur social.technet.microsoft.com  
  
  

