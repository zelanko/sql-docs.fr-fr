---
title: Éditeur de tâche de script (page script) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.script.f1
helpviewer_keywords:
- Script Task Editor
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 037b176dfacd9420fba64a405d8c851c558e93e3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66056186"
---
# <a name="script-task-editor-script-page"></a>Éditeur de tâche de script (page Script)
  Utilisez la page **Script** de la boîte de dialogue **Éditeur de tâche de script** pour définir les propriétés du script et vérifier les variables auxquelles le script peut accéder.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] et les versions ultérieures, tous les scripts sont précompilés. Dans les versions antérieures, vous définissez une propriété **PrecompileScriptIntoBinaryCode** pour spécifier que le script a été précompilé.  
  
 Pour en savoir plus sur la tâche de script, consultez [Script Task](control-flow/script-task.md) et [Configuration de la tâche de script dans l'éditeur de tâche de script](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md). Pour en savoir plus sur la programmation de la tâche de script, consultez [Extension du package à l'aide de la tâche de script](extending-packages-scripting/task/extending-the-package-with-the-script-task.md).  
  
## <a name="options"></a>Options  
 **ScriptLanguage**  
 Sélectionnez le langage de script pour la tâche, [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.  
  
 Après avoir créé un script pour la tâche, vous ne pouvez pas modifier la valeur de la propriété **ScriptLanguage** .  
  
 Pour définir le langage de script par défaut pour la tâche de script, utilisez l'option **Langage de script** dans la page **Général** de la boîte de dialogue **Options** . Pour plus d'informations, consultez [General Page](general-page-of-integration-services-designers-options.md).  
  
 **EntryPoint**  
 Spécifiez la méthode que le runtime [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] appelle comme point d’entrée dans le code de la tâche de script. La méthode spécifiée doit se trouver dans la classe ScriptMain du [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projet Tools for Applications (VSTA) la classe ScriptMain est la classe par défaut générée par les modèles de script.  
  
 Si vous modifiez le nom de la méthode dans le projet VSTA, vous devez modifier la valeur de la propriété **EntryPoint** .  
  
 **ReadOnlyVariables**  
 Tapez une liste séparée par des virgules des variables en lecture seule accessibles au script ou cliquez sur le bouton de sélection (**...**) et sélectionnez les variables dans la boîte de dialogue **Sélectionner des variables** .  
  
> [!NOTE]  
>  Les noms des variables tiennent compte de la casse.  
  
 **ReadWriteVariables**  
 Tapez une liste séparée par des virgules des variables en lecture/écriture accessibles au script ou cliquez sur le bouton de sélection (**...**) et sélectionnez les variables dans la boîte de dialogue **Sélectionner des variables** .  
  
> [!NOTE]  
>  Les noms des variables tiennent compte de la casse.  
  
 **Modifier le script**  
 Ouvre l'environnement de développement intégré VSTA dans lequel vous pouvez créer ou modifier le script.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Page général](general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche de script &#40;page général&#41;](../../2014/integration-services/script-task-editor-general-page.md)   
 [Page expressions](expressions/expressions-page.md)   
 [Exemples de tâche de script](extending-packages-scripting-task-examples/script-task-examples.md)   
 [Integration Services &#40;les variables de&#41; SSIS](integration-services-ssis-variables.md)   
 [Ajouter, supprimer, modifier l'étendue de la variable définie par l'utilisateur dans un package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
