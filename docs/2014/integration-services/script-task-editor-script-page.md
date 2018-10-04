---
title: Éditeur de tâche de script (Page Script) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.script.f1
helpviewer_keywords:
- Script Task Editor
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5ee7bb13e8a9fa4826297cd0c55b82881aee5296
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48198079"
---
# <a name="script-task-editor-script-page"></a>Éditeur de tâche de script (page Script)
  Utilisez la page **Script** de la boîte de dialogue **Éditeur de tâche de script** pour définir les propriétés du script et vérifier les variables auxquelles le script peut accéder.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] et les versions ultérieures, tous les scripts sont précompilés. Dans les versions antérieures, vous définissez une propriété **PrecompileScriptIntoBinaryCode** pour spécifier que le script a été précompilé.  
  
 Pour en savoir plus sur la tâche de script, consultez [Script Task](control-flow/script-task.md) et [Configuring the Script Task in the Script Task Editor](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md). Pour en savoir plus sur la programmation de la tâche de script, consultez [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md).  
  
## <a name="options"></a>Options  
 **ScriptLanguage**  
 Sélectionnez le langage de script pour la tâche, [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.  
  
 Après avoir créé un script pour la tâche, vous ne pouvez pas modifier la valeur de la propriété **ScriptLanguage** .  
  
 Pour définir le langage de script par défaut pour la tâche de script, utilisez l'option **Langage de script** dans la page **Général** de la boîte de dialogue **Options** . Pour plus d'informations, consultez [General Page](general-page-of-integration-services-designers-options.md).  
  
 **EntryPoint**  
 Spécifiez la méthode que le runtime [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] appelle comme point d’entrée dans le code de la tâche de script. La méthode spécifiée doit se trouver dans la classe ScriptMain (classe par défaut générée par les modèles de script) du projet [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA).  
  
 Si vous modifiez le nom de la méthode dans le projet VSTA, vous devez modifier la valeur de la propriété **EntryPoint** .  
  
 **ReadOnlyVariables**  
 Tapez une liste séparée par des virgules des variables en lecture seule accessibles au script ou cliquez sur le bouton de sélection (**…**) et sélectionnez les variables dans la boîte de dialogue **Sélectionner des variables** .  
  
> [!NOTE]  
>  Les noms des variables tiennent compte de la casse.  
  
 **ReadWriteVariables**  
 Tapez une liste séparée par des virgules des variables en lecture/écriture accessibles au script ou cliquez sur le bouton de sélection (**…**) et sélectionnez les variables dans la boîte de dialogue **Sélectionner des variables** .  
  
> [!NOTE]  
>  Les noms des variables tiennent compte de la casse.  
  
 **Modifier le script**  
 Ouvre l'environnement de développement intégré VSTA dans lequel vous pouvez créer ou modifier le script.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Page Général](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche de script &#40;Page Général&#41;](../../2014/integration-services/script-task-editor-general-page.md)   
 [Page expressions](expressions/expressions-page.md)   
 [Exemples de tâche de script](extending-packages-scripting-task-examples/script-task-examples.md)   
 [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md)   
 [Ajouter, supprimer, modifier l’étendue d’une variable définie par l’utilisateur dans un package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
