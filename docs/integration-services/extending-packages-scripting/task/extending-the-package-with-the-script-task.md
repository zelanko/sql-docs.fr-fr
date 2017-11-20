---
title: "Extension du Package avec la tâche de Script | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- scripts [Integration Services]
- SSIS Script task
- tasks [Integration Services], scripts
- Script task [Integration Services], about Script task
- scripts [Integration Services], about Script task with packages
- SSIS Script task, about Script task
ms.assetid: 911e6d26-a6fd-4fc3-a111-bf5f048e9bff
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b2e0b0a933568f8313cefd2f1d6dbdd02f5d3cbc
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="extending-the-package-with-the-script-task"></a>Extension du package à l'aide de la tâche de script
  La tâche de Script étend les fonctionnalités de l’exécution de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages avec du code personnalisé écrit dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual c# qui est compilé et exécuté au moment de l’exécution du package. La tâche de script simplifie le développement d'une tâche d'exécution personnalisée lorsque les tâches incluses dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ne répondent pas complètement à vos besoins. La tâche de script écrit tout le code d'infrastructure requis à votre place, ce qui vous permet de vous concentrer exclusivement sur le code requis pour votre traitement personnalisé.  
  
 Une tâche de Script interagit avec le package conteneur via global **Dts** (objet), une instance de la <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> classe qui est exposée dans l’environnement de script. Vous pouvez écrire le code dans une tâche de script qui modifie les valeurs stockées dans les variables [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ; le package peut ensuite utiliser ces valeurs mises à jour pour déterminer le chemin d'accès de son flux de travail. La tâche de script peut également utiliser l'espace de noms [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] et la bibliothèque de classes [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ainsi que des assemblys personnalisés, pour implémenter des fonctionnalités personnalisées.  
  
 La tâche de script et le code d'infrastructure qu'elle génère simplifient considérablement le processus qui consiste à développer une tâche personnalisée. Toutefois, pour comprendre le fonctionnement de la tâche de Script, vous pouvez s’avérer utile de lire la section [développer une tâche personnalisée](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md) pour comprendre les étapes du développement d’une tâche personnalisée.  
  
 Si vous créez une tâche que vous projetez de réutiliser dans plusieurs packages, vous devez envisager de développer une tâche personnalisée au lieu d'utiliser la tâche de script. Pour plus d’informations, consultez [comparaison des Solutions de script et des objets personnalisés](../../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes fournissent des informations supplémentaires sur la tâche de script.  
  
 [Configuration de la tâche de Script dans l’éditeur de tâche de Script.](../../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)  
 Explique comment les propriétés que vous configurez dans le **éditeur de tâche de Script** affectent les fonctionnalités et les performances du code dans la tâche de Script.  
  
 [Codage et débogage de la tâche de Script](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)  
 Explique comment utiliser [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) pour développer les scripts contenus dans la tâche de Script.  
  
 [Utilisation de Variables dans la tâche de Script](../../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 Explique comment utiliser des variables via la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>.  
  
 [Connexion aux Sources de données dans la tâche de Script](../../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 Explique comment utiliser des connexions via la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>.  
  
 [Le déclenchement d’événements dans la tâche de Script](../../../integration-services/extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 Explique comment déclencher des événements via la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>.  
  
 [Journalisation dans la tâche de Script](../../../integration-services/extending-packages-scripting/task/logging-in-the-script-task.md)  
 Explique comment journaliser des informations via la méthode <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>.  
  
 [Retourner les résultats de la tâche de Script](../../../integration-services/extending-packages-scripting/task/returning-results-from-the-script-task.md)  
 Explique comment renvoyer des résultats via la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> et la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>.  
  
 [Exemples de tâche de script](../../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)  
 Fournit des exemples simples qui montrent plusieurs utilisations possibles d'une tâche de script.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche de script](../../../integration-services/control-flow/script-task.md)   
 [Comparaison de la tâche de Script et le composant de Script](../../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  

