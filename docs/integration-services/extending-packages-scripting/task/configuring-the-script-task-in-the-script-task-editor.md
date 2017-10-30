---
title: "Configuration de la tâche de Script dans l’éditeur de tâche de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], configuring
- Script Task Editor
- SSIS Script task, configuring
ms.assetid: 232de0c9-b24d-4c38-861d-6c1f4a75bdf3
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 182a7b8f04c2339a8f3d3b986c978a7998c8a9c3
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="configuring-the-script-task-in-the-script-task-editor"></a>Configuration de la tâche de script dans l'éditeur de tâche de script
  Avant d’écrire un code personnalisé dans la tâche de Script, vous configurez ses propriétés principales dans les trois pages de la **éditeur de tâche de Script**. Vous pouvez configurer des propriétés de tâche supplémentaires qui ne sont pas propres à la tâche de script à l'aide de la fenêtre Propriétés.  
  
> [!NOTE]  
>  Contrairement aux versions antérieures pour lesquelles il était possible d'indiquer si les scripts étaient précompilés, tous les scripts sont compilés à partir de [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)].  
  
## <a name="general-page-of-the-script-task-editor"></a>Page Général de l'éditeur de tâche de script  
 Sur le **général** page de la **éditeur de tâche de Script**, vous affectez un nom unique et une description pour la tâche de Script.  
  
## <a name="script-page-of-the-script-task-editor"></a>Page Script de l'éditeur de tâche de script  
 Le **Script** page de la **éditeur de tâche de Script** affiche les propriétés personnalisées de la tâche de Script.  
  
### <a name="scriptlanguage-property"></a>Propriété ScriptLanguage  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) prend en charge la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] langages de programmation Visual c#. Après avoir créé un script dans la tâche de Script, vous ne pouvez pas modifier la valeur de la **ScriptLanguage** propriété.  
  
 Pour définir le langage de script par défaut pour les tâches de Script et des composants de Script, utilisez la **ScriptLanguage** propriété sur le **général** page de la **Options** boîte de dialogue. Pour plus d'informations, consultez [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
### <a name="entrypoint-property"></a>Propriété EntryPoint  
 Le **EntryPoint** propriété spécifie la méthode sur le **ScriptMain** de projet qui classe les VSTA le [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime appelle comme point d’entrée dans le code de tâche de Script. Le **ScriptMain** classe est la classe par défaut générée par les modèles de script.  
  
 Si vous modifiez le nom de la méthode dans le projet VSTA, vous devez modifier la valeur de la propriété **EntryPoint** .  
  
### <a name="readonlyvariables-and-readwritevariables-properties"></a>Propriétés ReadOnlyVariables et ReadWriteVariables  
 Vous pouvez entrer des listes délimitées par des virgules de variables existantes comme valeurs de ces propriétés pour rendre les variables accessibles en lecture seule ou en lecture/écriture dans le code de tâche de script. Deux types de variables sont accessibles dans le code via la <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> propriété de la **Dts** objet. Pour plus d’informations, consultez [Utilisation de variables dans la tâche de script](../../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md).  
  
> [!NOTE]  
>  Les noms de variable respectent la casse.  
  
 Pour sélectionner les variables, cliquez sur le bouton de sélection (**...** ) bouton en regard du champ de propriété. Pour plus d’informations, consultez [la Page Sélectionner les Variables](../../../integration-services/control-flow/select-variables-page.md).  
  
### <a name="edit-script-button"></a>Bouton Modifier le script  
 Le **modifier le Script** bouton lance l’environnement de développement VSTA dans laquelle vous écrivez votre script personnalisé. Pour plus d’informations, consultez [codage et débogage de la tâche de Script](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md).  
  
## <a name="expressions-page-of-the-script-task-editor"></a>Page Expressions de l'éditeur de tâche de script  
 Sur le **Expressions** page de la **éditeur de tâche de Script**, vous pouvez utiliser des expressions pour fournir des valeurs pour les propriétés de la tâche de Script répertoriées ci-dessus et pour de nombreuses autres propriétés de la tâche. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](../../../integration-services/expressions/integration-services-ssis-expressions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Codage et débogage de la tâche de Script](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)  
  
  

