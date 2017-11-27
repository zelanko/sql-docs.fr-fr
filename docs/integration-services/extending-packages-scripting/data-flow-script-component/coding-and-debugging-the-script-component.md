---
title: "Codage et débogage du composant Script | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, development environment
- Script component [Integration Services], debugging
- Script component [Integration Services], coding
- SSIS Script component, debugging
- Script component [Integration Services], development environment
- debugging [Integration Services], scripts
- SSIS Script component, coding
- VSTA
ms.assetid: c3913c15-66aa-4b61-89b5-68488fa5f0a4
caps.latest.revision: 66
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ff6c9814547a83439717f8a88d3bd52be80c4ca5
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="coding-and-debugging-the-script-component"></a>Codage et débogage du composant Script
  Dans le Concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)], le composant Script propose deux modes : le mode Création des métadonnées et le mode Création du code. Lorsque vous ouvrez le **éditeur de Transformation de Script**, le composant entre le mode de création de métadonnées, dans laquelle vous configurez des métadonnées et définissez les propriétés du composant. Après avoir défini les propriétés du composant Script et avoir configuré l'entrée et les sorties en mode Création des métadonnées, vous pouvez basculer vers le mode Création du code pour écrire votre script personnalisé. Pour plus d’informations sur le mode Création de métadonnées et le mode de création de code, consultez [configuration du composant Script dans l’éditeur de composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
## <a name="writing-the-script-in-code-design-mode"></a>Écriture du script en mode Création du code  
  
### <a name="script-component-development-environment"></a>Environnement de développement du composant Script  
 Pour écrire votre script, cliquez sur **modifier le Script** sur la **Script** page de la **éditeur de Transformation de Script** pour ouvrir le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE. L'environnement de développement intégré VSTA contient l'ensemble des fonctionnalités standard de l'environnement [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET, telles que l'éditeur [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] à code de couleurs, IntelliSense et l'Explorateur d'objets.  
  
 Le code de script est écrit dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#. Vous spécifiez le langage de script en définissant le **ScriptLanguage** propriété dans le **éditeur de Transformation de Script**. Si vous préférez utiliser un autre langage de programmation, vous pouvez développer un assembly personnalisé dans le langage de votre choix et appeler ses fonctionnalités à partir du code inclus dans le composant Script.  
  
 Le script que vous créez dans le composant Script est stocké dans la définition du package. Aucun fichier de script distinct n'est créé. Par conséquent, l'utilisation du composant Script n'affecte pas le déploiement du package.  
  
> [!NOTE]  
>  Lorsque vous concevez le package, le code de script est écrit temporairement dans un fichier projet. Étant donné que le stockage d'informations sensibles dans un fichier représente un risque potentiel en termes de sécurité, nous vous recommandons de ne pas inclure d'informations sensibles telles que des mots de passe dans le code de script.  
  
 Par défaut, **Option Strict** est désactivé dans l’IDE.  
  
### <a name="script-component-project-structure"></a>Structure du projet de composant Script  
 La force du composant Script réside dans sa capacité à générer un code d'infrastructure qui réduit la quantité de code à écrire. Cette fonctionnalité repose sur le fait que les entrées et sorties et leurs colonnes et propriétés sont fixes et connues à l'avance. Par conséquent, toutes les modifications ultérieures que vous apportez aux métadonnées du composant peuvent invalider le code que vous avez écrit. Cela provoque des erreurs de compilation pendant l'exécution du package.  
  
#### <a name="project-items-and-classes-in-the-script-component-project"></a>Éléments et classe de projet dans le projet de composant Script  
 Lorsque vous basculez en mode de création de code, l’IDE VSTA s’ouvre et affiche le **ScriptMain** élément de projet. Le **ScriptMain** élément de projet contient le texte modifiable **ScriptMain** (classe), qui sert de l’entrée pour le script et qui est où vous écrivez votre code. Les éléments de code inclus dans la classe varient selon le langage de programmation que vous avez sélectionné pour la tâche de script.  
  
 Le projet de script contient deux autres éléments de projet en lecture seule générés automatiquement :  
  
-   Le **ComponentWrapper** élément de projet contient trois classes :  
  
    -   Le **UserComponent** (classe), qui hérite de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> et contient les méthodes et propriétés que vous allez utiliser pour traiter les données et d’interagir avec le package. Le **ScriptMain** classe hérite de la **UserComponent** classe.  
  
    -   A **connexions** classe de collection qui contient des références aux connexions sélectionnées dans la page Gestionnaire de connexions de l’éditeur de Transformation de Script.  
  
    -   A **Variables** classe de collection qui contient des références aux variables entrées dans le **ReadOnlyVariable** et **ReadWriteVariables** propriétés sur le **Script** page de la **éditeur de Transformation de Script**.  
  
-   Le **BufferWrapper** élément de projet contient une classe qui hérite de <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> pour chaque entrée et sortie configurée sur le **entrées et sorties** page de la **éditeur de Transformation de Script**. Chacune de ces classes contient des propriétés d'accesseur typées qui correspondent aux colonnes d'entrée et de sortie configurées, ainsi que des tampons de flux de données qui contiennent les colonnes.  
  
 Pour plus d’informations sur l’utilisation de ces objets, méthodes et propriétés, consultez [présentation du modèle objet de composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md). Pour plus d’informations sur la façon d’utiliser les méthodes et propriétés de ces classes dans un type particulier de composant de Script, consultez la section [des exemples supplémentaires de composant de Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md). Les rubriques d'exemples contiennent également des exemples de code complets.  
  
 Lorsque vous configurez le composant de Script en tant que transformation, le **ScriptMain** élément de projet contient le code généré automatiquement suivant. Le modèle de code fournit également une vue d'ensemble du composant Script, ainsi que des informations supplémentaires sur la récupération et la manipulation des objets SSIS, tels que les variables, les événements et les connexions.  
  
```vb  
' Microsoft SQL Server Integration Services Script Component  
' Write scripts using Microsoft Visual Basic 2008.  
' ScriptMain is the entry point class of the script.  
  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper  
  
<Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute> _  
<CLSCompliant(False)> _  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Public Overrides Sub PreExecute()  
        MyBase.PreExecute()  
        '  
        ' Add your code here for preprocessing or remove if not needed  
        '  
    End Sub  
  
    Public Overrides Sub PostExecute()  
        MyBase.PostExecute()  
        '  
        ' Add your code here for postprocessing or remove if not needed  
        ' You can set read/write variables here, for example:  
        ' Me.Variables.MyIntVar = 100  
        '  
    End Sub  
  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
        '  
        ' Add your code here  
        '  
    End Sub  
  
End Class  
```  
  
```csharp  
/* Microsoft SQL Server Integration Services user script component  
*  Write scripts using Microsoft Visual C# 2008.  
*  ScriptMain is the entry point class of the script.*/  
  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
  
[Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute]  
public class ScriptMain : UserComponent  
{  
  
    public override void PreExecute()  
    {  
        base.PreExecute();  
        /*  
          Add your code here for preprocessing or remove if not needed  
        */  
    }  
  
    public override void PostExecute()  
    {  
        base.PostExecute();  
        /*  
          Add your code here for postprocessing or remove if not needed  
          You can set read/write variables here, for example:  
          Variables.MyIntVar = 100  
        */  
    }  
  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
        /*  
          Add your code here  
        */  
    }  
  
}  
```  
  
#### <a name="additional-project-items-in-the-script-component-project"></a>Autres éléments de projet dans le projet de composant Script  
 Le projet de composant Script peut inclure des éléments autres que la valeur par défaut **ScriptMain** élément. Vous pouvez ajouter des classes, des modules, des fichiers de code et des dossiers au projet, et vous pouvez utiliser des dossiers pour organiser des groupes d'éléments.  
  
 Tous les éléments que vous ajoutez sont rendus persistants à l'intérieur du package.  
  
#### <a name="references-in-the-script-component-project"></a>Références dans le projet de composant Script  
 Vous pouvez ajouter des références à des assemblys managés en cliquant sur le projet de tâche de Script dans **Explorateur de projets**, puis en cliquant sur **ajouter une référence**. Pour plus d’informations, consultez [faisant référence à d’autres assemblys dans les Solutions de script](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md).  
  
> [!NOTE]  
>  Vous pouvez afficher les références de projet dans l’IDE VSTA **affichage de classes** ou dans **Explorateur de projets**. Vous ouvrez un de ces fenêtres à partir de la **vue** menu. Vous pouvez ajouter une nouvelle référence à partir de la **projet** menu, à partir de **Explorateur de projets**, ou à partir de **affichage de classes**.  
  
## <a name="interacting-with-the-package-in-the-script-component"></a>Interaction avec le package dans le composant Script  
 Le script personnalisé que vous écrivez dans le composant Script peut accéder à des variables et gestionnaires de connexions afin de les utiliser, à partir du package conteneur, via des accesseurs fortement typés dans les classes de base générées automatiquement. Toutefois, vous devez configurer à la fois les variables et les gestionnaires de connexions avant de passer en mode Création du code si vous souhaitez les rendre disponibles pour votre script. Vous pouvez également déclencher des événements et effectuer une journalisation à partir de votre code de composant Script.  
  
 Les éléments de projet générés automatiquement dans le projet de composant Script fournissent les objets, méthodes et propriétés ci-après pour interagir avec le package.  
  
|Fonctionnalité du package|Méthode d'accès|  
|---------------------|-------------------|  
|Variables|Utiliser les propriétés d’accesseur typées et nommées de la **Variables** classe de collection dans le **ComponentWrapper** l’élément de projet, exposée via la **Variables** propriété de la **ScriptMain** classe.<br /><br /> Le **PreExecute** méthode peut accéder uniquement les variables en lecture seule. Le **PostExecute** méthode peut accéder en lecture seule et en lecture/écriture de variables.|  
|Connexions|Utiliser les propriétés d’accesseur typées et nommées de la **connexions** classe de collection dans le **ComponentWrapper** l’élément de projet, exposée via la **connexions** propriété de la **ScriptMain** classe.|  
|Événements|Déclencher des événements à l’aide de la <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> propriété de la **ScriptMain** classe et le **incendie\<X >** méthodes de la <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface.|  
|Journalisation|Exécuter la journalisation à l’aide de la <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> méthode de la **ScriptMain** classe.|  
  
## <a name="debugging-the-script-component"></a>Débogage du composant Script  
 Pour déboguer le code dans votre composant Script, définissez au moins un point d'arrêt dans le code, puis fermez l'environnement de développement intégré VISTA pour exécuter le package dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Lorsque l'exécution du package entre le composant Script, l'environnement de développement intégré s'ouvre à nouveau et affiche votre code en lecture seule. Lorsque l'exécution atteint le point d'arrêt, vous pouvez examiner les valeurs des variables et exécuter pas à pas le code restant.  
  
> [!NOTE]  
>  Vous ne pouvez pas déboguer un composant Script si vous l'exécutez dans le cadre d'un package enfant exécuté à partir d'une tâche d'exécution de package. Dans ce cas, les points d'arrêt définis dans le composant Script dans le package enfant sont ignorés. Vous pouvez déboguer normalement le package enfant en l'exécutant séparément.  
  
> [!NOTE]  
>  Lorsque vous déboguez un package qui contient plusieurs composants de script, le débogueur n'en débogue qu'un seul. Le système peut déboguer un autre composant script si le débogueur a terminé, comme dans le cas d'une boucle Foreach ou du conteneur de boucles For.  
  
 Vous pouvez également surveiller l'exécution du composant Script en utilisant les méthodes suivantes :  
  
-   Interrompez l’exécution et afficher un message modal en utilisant le **MessageBox.Show** méthode dans le **System.Windows.Forms** espace de noms. (Supprimez ce code une fois que vous avez terminé le processus de débogage.)  
  
-   Déclenchez des événements pour les messages d'information, les avertissements et les erreurs. Les méthodes FireInformation, FireWarning et FireError affichent la description des événements dans Visual Studio **sortie** fenêtre. Toutefois, la FireProgress (méthode), le Console.Write (méthode) et Console.WriteLine (méthode) n’affichent pas toutes les informations dans le **sortie** fenêtre. Les messages à partir de l’événement FireProgress apparaissent sur le **progression** onglet de [!INCLUDE[ssIS](../../../includes/ssis-md.md)] concepteur. Pour plus d’informations, consultez [déclenchement d’événements dans le composant de Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/raising-events-in-the-script-component.md).  
  
-   Journalisez les événements ou les messages définis par l'utilisateur dans les modules fournisseurs d'informations activés. Pour plus d’informations, consultez [journalisation dans le composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/logging-in-the-script-component.md).  
  
 Si vous souhaitez simplement examiner la sortie d’un composant Script configuré en tant que source ou en tant que transformation, sans enregistrer les données vers une destination, vous pouvez arrêter le flux de données avec un [Row Count Transformation](../../../integration-services/data-flow/transformations/row-count-transformation.md) et attachez une visionneuse de données à la sortie du composant Script. Pour plus d’informations sur les visionneuses de données, consultez [débogage de flux de données](../../../integration-services/troubleshooting/debugging-data-flow.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 Pour plus d'informations sur le codage du composant Script, consultez les rubriques suivantes de cette section.  
  
 [Présentation du modèle objet de composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md)  
 Explique comment utiliser les objets, méthodes et propriétés disponibles dans le composant Script.  
  
 [Référencer d’autres assemblys dans les Solutions de script](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)  
 Explique comment référencer des objets de la bibliothèque de classes [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] dans le composant Script.  
  
 [Simulation d’une sortie d’erreur du composant de Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)  
 Explique comment simuler une sortie d'erreur pour les lignes qui déclenchent des erreurs lors du traitement par le composant Script.  
  
## <a name="external-resources"></a>Ressources externes  
  
-   Entrée de blog, [VSTA le programme d’installation et problèmes de configuration pour les installations SSIS 2008 et R2](http://go.microsoft.com/fwlink/?LinkId=215661), sur blogs.msdn.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration du composant Script dans l’éditeur de composant Script.](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)  
  
  

