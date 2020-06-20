---
title: Extension du package à l’aide de la tâche de script | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
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
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b67b80bafd052a095acaf9b5a4763ed74af3ab1e
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967209"
---
# <a name="extending-the-package-with-the-script-task"></a>Extension du package à l'aide de la tâche de script
  La tâche de script étend les fonctionnalités d’exécution des packages [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] à l’aide de code personnalisé écrit dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# qui est compilé et exécuté au moment de l’exécution des packages. La tâche de script simplifie le développement d'une tâche d'exécution personnalisée lorsque les tâches incluses dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ne répondent pas complètement à vos besoins. La tâche de script écrit tout le code d'infrastructure requis à votre place, ce qui vous permet de vous concentrer exclusivement sur le code requis pour votre traitement personnalisé.  
  
 Une tâche de script interagit avec le package conteneur via l'objet `Dts` global, une instance de la classe <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> exposée dans l'environnement de script. Vous pouvez écrire le code dans une tâche de script qui modifie les valeurs stockées dans les variables [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ; le package peut ensuite utiliser ces valeurs mises à jour pour déterminer le chemin d'accès de son flux de travail. La tâche de script peut également utiliser l'espace de noms [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] et la bibliothèque de classes [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ainsi que des assemblys personnalisés, pour implémenter des fonctionnalités personnalisées.  
  
 La tâche de script et le code d'infrastructure qu'elle génère simplifient considérablement le processus qui consiste à développer une tâche personnalisée. Toutefois, pour comprendre le fonctionnement de la tâche de script, il peut s’avérer utile de lire la section [Développement d’une tâche personnalisée](../../extending-packages-custom-objects/task/developing-a-custom-task.md) afin de maîtriser les étapes du développement d’une tâche personnalisée.  
  
 Si vous créez une tâche que vous projetez de réutiliser dans plusieurs packages, vous devez envisager de développer une tâche personnalisée au lieu d'utiliser la tâche de script. Pour plus d’informations, consultez [Comparaison des solutions de script et des objets personnalisés](../comparing-scripting-solutions-and-custom-objects.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes fournissent des informations supplémentaires sur la tâche de script.  
  
 [Configuration de la tâche de script dans l’éditeur de tâche de script](configuring-the-script-task-in-the-script-task-editor.md)  
 Explique de quelle manière les propriétés que vous configurez dans l’**éditeur de tâche de script** affectent les fonctionnalités et les performances du code de la tâche de script.  
  
 [Codage et débogage de la tâche de script](../../control-flow/script-task.md)  
 Explique comment utiliser [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) pour développer les scripts contenus dans la tâche de script.  
  
 [Utilisation de variables dans la tâche de script](using-variables-in-the-script-task.md)  
 Explique comment utiliser des variables via la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>.  
  
 [Connexion à des sources de données dans la tâche de script](connecting-to-data-sources-in-the-script-task.md)  
 Explique comment utiliser des connexions via la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>.  
  
 [Déclenchement d’événements dans la tâche de script](raising-events-in-the-script-task.md)  
 Explique comment déclencher des événements via la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>.  
  
 [Journalisation dans la tâche de script](logging-in-the-script-task.md)  
 Explique comment journaliser des informations via la méthode <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>.  
  
 [Retour de résultats de la tâche de script](returning-results-from-the-script-task.md)  
 Explique comment renvoyer des résultats via la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> et la propriété <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>.  
  
 [Exemples de tâche de script](../../extending-packages-scripting-task-examples/script-task-examples.md)  
 Fournit des exemples simples qui montrent plusieurs utilisations possibles d'une tâche de script.  
  
![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les téléchargements, articles, exemples et vidéos les plus récents de [!INCLUDE[msCoName](../../../includes/msconame-md.md)], ainsi que les solutions retenues par la communauté informatique, consultez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche de script](../../control-flow/script-task.md)   
 [Comparaison de la tâche de script et du composant Script](../../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  
