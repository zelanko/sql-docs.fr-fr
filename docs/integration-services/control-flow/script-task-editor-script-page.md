---
title: "&#201;diteur de t&#226;che de script (page Script) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.scripttask.script.f1"
helpviewer_keywords: 
  - "Éditeur de tâche de script"
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# &#201;diteur de t&#226;che de script (page Script)
  Utilisez la page **Script** de la boîte de dialogue **Éditeur de tâche de script** pour définir les propriétés du script et vérifier les variables auxquelles le script peut accéder.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] et les versions ultérieures, tous les scripts sont précompilés. Dans les versions antérieures, vous définissez une propriété **PrecompileScriptIntoBinaryCode** pour spécifier que le script a été précompilé.  
  
 Pour en savoir plus sur la tâche de script, consultez [Script Task](../../integration-services/control-flow/script-task.md) et [Configuring the Script Task in the Script Task Editor](../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md). Pour en savoir plus sur la programmation de la tâche de script, consultez [Extending the Package with the Script Task](../../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md).  
  
## Options  
 **ScriptLanguage**  
 Sélectionnez le langage de script pour la tâche, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Après avoir créé un script pour la tâche, vous ne pouvez pas modifier la valeur de la propriété **ScriptLanguage** .  
  
 Pour définir le langage de script par défaut pour la tâche de script, utilisez l'option **Langage de script** dans la page **Général** de la boîte de dialogue **Options** . Pour plus d'informations, consultez [General Page](../Topic/General%20Page.md).  
  
 **EntryPoint**  
 Spécifiez la méthode que le runtime [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] appelle comme point d’entrée dans le code de la tâche de script. La méthode spécifiée doit se trouver dans la classe ScriptMain (classe par défaut générée par les modèles de script) du projet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Tools for Applications (VSTA).  
  
 Si vous modifiez le nom de la méthode dans le projet VSTA, vous devez modifier la valeur de la propriété **EntryPoint** .  
  
 **ReadOnlyVariables**  
 Tapez une liste séparée par des virgules des variables en lecture seule accessibles au script ou cliquez sur le bouton de sélection (**…**) et sélectionnez les variables dans la boîte de dialogue **Sélectionner des variables**.  
  
> [!NOTE]  
>  Les noms des variables tiennent compte de la casse.  
  
 **ReadWriteVariables**  
 Tapez une liste séparée par des virgules des variables en lecture/écriture accessibles au script ou cliquez sur le bouton de sélection (**…**) et sélectionnez les variables dans la boîte de dialogue **Sélectionner des variables**.  
  
> [!NOTE]  
>  Les noms des variables tiennent compte de la casse.  
  
 **Modifier le script**  
 Ouvre l'environnement de développement intégré VSTA dans lequel vous pouvez créer ou modifier le script.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Page Général](../Topic/General%20Page.md)   
 [Éditeur de tâche de script &#40;page Général&#41;](../../integration-services/control-flow/script-task-editor-general-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)   
 [Exemples de tâche de script](../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)   
 [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md)   
 [Ajouter, supprimer, modifier l'étendue de la variable définie par l'utilisateur dans un package](../Topic/Add,%20Delete,%20Change%20Scope%20of%20User-Defined%20Variable%20in%20a%20Package.md)  
  
  