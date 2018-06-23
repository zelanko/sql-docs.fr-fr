---
title: Exécuter le processus, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.executeprocesstask.f1
helpviewer_keywords:
- Execute Process task [Integration Services]
ms.assetid: aca5a0b5-34a9-45bc-a234-8e63ea51a1ee
caps.latest.revision: 65
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3b67903b59934fb8d43d8dafe2bfc8392ab56462
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139639"
---
# <a name="execute-process-task"></a>Tâche d'exécution de processus
  La tâche d’exécution de processus exécute une application ou un fichier de commandes dans le cadre d’un flux de travail de package [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Bien qu’il soit possible d’utiliser la tâche d’exécution de processus pour ouvrir des applications standard telles que [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] ou [!INCLUDE[ofprword](../../includes/ofprword-md.md)], il est courant de l’utiliser pour exécuter des applications de gestion ou des fichiers de commandes fonctionnant sur une source de données. Par exemple, vous pouvez utiliser la tâche d'exécution de processus pour développer un fichier texte compressé. Ensuite, le package peut utiliser le fichier texte comme source de données pour le flux de données de ce package. Vous pouvez aussi utiliser la tâche d'exécution de processus pour démarrer une application [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] personnalisée qui génère quotidiennement un état des ventes. Ensuite, vous pouvez associer le rapport à une tâche Envoyer un message pour le transmettre à une liste de distribution.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] comprend d’autres tâches qui effectuent des opérations de flux de travail, telles que l’exécution de packages. Pour plus d’informations, consultez [Tâche d’exécution de package](execute-package-task.md).  
  
## <a name="custom-log-entries-available-on-the-execute-process-task"></a>Entrées de journal personnalisées disponibles dans la tâche d'exécution de processus  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche d'exécution de processus. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`ExecuteProcessExecutingProcess`|Fournit des informations sur le processus que la tâche est chargée d'exécuter.<br /><br /> Deux entrées de journal sont écrites. La première contient des informations sur le nom et l'emplacement de l'exécutable que la tâche exécute ; la deuxième enregistre la sortie de l'exécutable.|  
|`ExecuteProcessVariableRouting`|Fournit des informations sur les variables qui doivent être acheminées vers l'entrée et les sorties de l'exécutable. Les entrées du journal sont écrites pour stdin (l'entrée), stdout (la sortie) et stderr (la sortie des erreurs).|  
  
## <a name="configuration-of-the-execute-process-task"></a>Configuration de la tâche d’exécution de processus  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche de processus d’exécution &#40;Page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur de tâche de processus d’exécution &#40;traiter la Page&#41;](../execute-process-task-editor-process-page.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="property-settings"></a>Paramètres de propriété  
 Lorsque la tâche d'exécution de processus exécute une application personnalisée, elle fournit l'entrée à l'application via l'une des méthodes suivantes, ou les deux :  
  
-   Une variable que vous spécifiez dans le paramètre de propriété **StandardInputVariable**. Pour plus d’informations sur les variables, consultez [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md) et [Utiliser des variables dans des packages](../use-variables-in-packages.md).  
  
-   Un argument que vous spécifiez dans le paramètre de propriété **Arguments**. (Par exemple, si la tâche ouvre un document dans Word, l'argument peut nommer le fichier .doc.)  
  
 Pour passer plusieurs arguments à une application personnalisée dans une tâche d'exécution de processus, utilisez des espaces pour délimiter les arguments. Un argument ne peut pas inclure d'espace ; sinon, la tâche ne s'exécutera pas. Vous pouvez utiliser une expression pour passer une valeur variable comme argument. Dans l'exemple suivant, l'expression passe deux valeurs variables comme arguments et utilise un espace pour délimiter les arguments :  
  
 `@variable1 + " " + @variable2`  
  
 Vous pouvez utiliser une expression pour définir différentes propriétés de tâche d'exécution de processus.  
  
 Lorsque vous utilisez la **StandardInputVariable** propriété pour configurer la tâche d’exécution de processus pour fournir l’entrée, appelez le `Console.ReadLine` méthode à partir de l’application de lire l’entrée. Pour plus d’informations, consultez la rubrique [Console.ReadLine, méthode](http://go.microsoft.com/fwlink/?LinkId=129201)de la bibliothèque de classes [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
 Quand vous configurez la tâche d’exécution de processus à l’aide de la propriété **Arguments** pour fournir l’entrée, effectuez l’une des étapes suivantes pour obtenir les arguments :  
  
-   Si vous utilisez Microsoft Visual Basic pour écrire l’application, définissez la `My.Application.CommandLineArgs` propriété. L'exemple suivant définit la propriété `My.Application.CommandLineArgs` pour extraire deux arguments :  
  
    ```  
    Dim variable1 As String = My.Application.CommandLineArgs.Item(0)  
    Dim variable2 As String = My.Application.CommandLineArgs.Item(1)   
    ```  
  
     Pour plus d’informations, consultez la rubrique [My.Application.CommandLineArgs, propriété](http://go.microsoft.com/fwlink/?LinkId=129200)dans la Référence [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .  
  
-   Si vous utilisez Microsoft Visual C# pour écrire l'application, utilisez la méthode `Main`.  
  
     Pour plus d’informations, consultez la rubrique [Arguments de ligne de commande (Guide de programmation C#)](http://go.microsoft.com/fwlink/?LinkId=129406)du Guide de programmation C#.  
  
 La tâche d’exécution de processus comprend également les propriétés **StandardOutputVariable** et **StandardErrorVariable** à l’aide desquelles vous pouvez spécifier les variables qui exploitent la sortie et la sortie d’erreur standard de l’application, respectivement.  
  
 En outre, vous pouvez configurer la tâche d'exécution de processus de manière à spécifier un répertoire de travail, un délai d'attente ou une valeur pour indiquer que l'exécutable s'est correctement exécuté. La tâche peut également être configurée de manière à échouer si l'exécutable est introuvable à l'emplacement spécifié ou que le code de retour de l'exécutable ne correspond pas à la valeur indiquant la réussite.  
  
## <a name="programmatic-configuration-of-the-execute-process-task"></a>Configuration par programmation de la tâche d'exécution de processus  
 Pour plus d'informations sur la définition par programme de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteProcess.ExecuteProcess>  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](integration-services-tasks.md)   
 [Flux de contrôle](control-flow.md)  
  
  