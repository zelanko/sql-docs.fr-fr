---
title: Interrogation d’Active Directory avec la tâche de script | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Active Directory access
- SSIS Script task, Active Directory access
- Script task [Integration Services], examples
- Active Directory [Integration Services]
ms.assetid: a88fefbb-9ea2-4a86-b836-e71315bac68e
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 142cef139d315d3db492651716c2ec8fb9b6e03c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968489"
---
# <a name="querying-the-active-directory-with-the-script-task"></a>Interrogation d'Active Directory avec la tâche de script
  Les applications de traitement des données d'entreprise, telles que les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], ont souvent besoin de traiter des données différemment selon l'échelon, le poste ou d'autres caractéristiques des employés stockés dans Active Directory. Active Directory est un service d’annuaire [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows qui fournit un magasin centralisé de métadonnées, non seulement sur les utilisateurs, mais aussi sur d’autres ressources organisationnelles, comme les ordinateurs et les imprimantes. L'espace de noms `System.DirectoryServices` dans le Microsoft .NET Framework fournit des classes à utiliser avec Active Directory, pour vous aider à diriger le flux de travail du traitement des données selon les informations qu'il stocke.  
  
> [!NOTE]  
>  Si vous souhaitez créer une tâche plus facilement réutilisable sur plusieurs packages, envisagez d'utiliser le code indiqué dans l'exemple de tâche de script comme point de départ d'une tâche personnalisée. Pour plus d’informations, consultez [Développement d’une tâche personnalisée](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## <a name="description"></a>Description  
 L'exemple suivant extrait le nom, le titre et le numéro de téléphone d'un employé dans Active Directory selon la valeur de la variable `email`, laquelle contient l'adresse de messagerie de l'employé. Les contraintes de précédence dans le package peuvent utiliser les informations extraites pour déterminer, par exemple, s'il faut envoyer un message électronique de priorité basse ou une page prioritaire, selon le poste de l'employé.  
  
#### <a name="to-configure-this-script-task-example"></a>Pour configurer cet exemple de tâche de script  
  
1.  Créez les trois variables de chaîne `email`, `name` et `title`. Entrez une adresse de messagerie professionnelle valide en tant que valeur de la variable `email`.  
  
2.  Dans la page **script** de l **'éditeur de tâche de script**, ajoutez la `email` variable à la `ReadOnlyVariables` propriété.  
  
3.  Ajoutez les variables `name` et `title` à la propriété `ReadWriteVariables`.  
  
4.  Dans le projet de script, ajoutez une référence à l' `System.DirectoryServices` espace de noms.  
  
5.  . Dans votre code, utilisez une instruction `Imports` pour importer l'espace de noms `DirectoryServices`.  
  
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
  
-   Article technique, [Processing Active Directory Information in SSIS](https://go.microsoft.com/fwlink/?LinkId=199588), sur social.technet.microsoft.com  
  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
  
