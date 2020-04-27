---
title: Conteneurs Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS containers
- containers [Integration Services]
- containers [Integration Services], about containers
- control flow [Integration Services], containers
- SQL Server Integration Services containers
ms.assetid: 1b725922-ec59-4a47-9d55-e079463058f3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 172aa2a77293dd7e9a9ee50bfe0002a71c59cbb9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62831257"
---
# <a name="integration-services-containers"></a>Conteneurs Integration Services
  Les conteneurs sont des objets de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui fournissent une structure aux packages et des services aux tâches. Ils prennent en charge les flux de contrôle répétitifs dans les packages, et regroupent les tâches et les conteneurs en unités de travail significatives. Outre des tâches, les conteneurs peuvent comprendre d'autres conteneurs.  
  
 Les packages utilisent les conteneurs aux fins suivantes :  
  
-   Répéter des tâches pour tous les éléments d'une collection, tels que les fichiers d'un dossier, des schémas ou des objets SMO ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects). Par exemple, un package peut exécuter des instructions Transact-SQL résidant dans plusieurs fichiers.  
  
-   Répéter des tâches jusqu'à ce qu'une expression spécifiée renvoie la valeur `false`. Par exemple, un package peut envoyer un message électronique différent sept fois, à raison d'une fois par jour de la semaine.  
  
-   Regrouper les tâches et les conteneurs qui doivent réussir ou échouer en tant qu'unité. Par exemple, un package peut regrouper les tâches qui suppriment et ajoutent des lignes dans une table de base de données, puis valider ou annuler toutes les tâches si l'une d'elles échoue.  
  
## <a name="container-types"></a>Types de conteneurs  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fournit quatre types de conteneurs pour la création de packages. Le tableau suivant décrit ces types de conteneurs.  
  
|Conteneur|Description|  
|---------------|-----------------|  
|[Conteneur de boucles Foreach](foreach-loop-container.md)|Exécute un flux de contrôle de façon répétitive à l'aide d'un énumérateur.|  
|[Conteneur de boucles For](for-loop-container.md)|Exécute un flux de contrôle de façon répétitive en testant une condition.|  
|[Conteneur de séquences](sequence-container.md)|Regroupe les tâches et les conteneurs en flux de contrôle représentant des sous-ensembles du flux de contrôle des packages.|  
|[Conteneur d’hôte de tâche](task-host-container.md)|Fournit des services à une seule tâche.|  
  
 Les packages et les gestionnaires d'événements sont également des types de conteneurs. Pour plus d’informations, consultez [Packages Integration Services &#40;SSIS&#41;](../integration-services-ssis-packages.md) et [Gestionnaires d’événements Integration Services &#40;SSIS&#41;](../integration-services-ssis-event-handlers.md).  
  
### <a name="summary-of-container-properties"></a>Résumé des propriétés de conteneur  
 Tous les types de conteneurs possèdent un ensemble de propriétés communes. Si vous créez des packages à l’aide des outils graphiques fournis par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , la fenêtre Propriétés répertorie les propriétés suivantes pour les conteneurs de boucles Foreach, de boucles For et de séquences. Les propriétés du conteneur d'hôte de tâche sont configurées dans le cadre de la configuration de la tâche encapsulée par l'hôte de tâche. Définissez les propriétés de l'hôte de tâche lorsque vous configurez la tâche.  
  
|Propriété|Description|  
|--------------|-----------------|  
|`DelayValidation`|Valeur booléenne qui indique si la validation du conteneur est retardée jusqu'à l'exécution. La valeur par défaut de cette propriété est `False`.<br /><br /> Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.DelayValidation%2A>.|  
|`Description`|Description du conteneur. La propriété contient une chaîne mais peut être est vide.<br /><br /> Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Description%2A>.|  
|`Disable`|Valeur booléenne qui indique si le conteneur s'exécute. La valeur par défaut de cette propriété est `False`.<br /><br /> Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Disable%2A>.|  
|`DisableEventHandlers`|Valeur booléenne qui indique si les gestionnaires d'événements associés au conteneur s'exécutent. La valeur par défaut de cette propriété est `False`.|  
|`FailPackageOnFailure`|Valeur booléenne qui indique si le package échoue en cas d'erreur dans le conteneur. La valeur par défaut de cette propriété est `False`.<br /><br /> Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailPackageOnFailure%2A>.|  
|`FailParentOnFailure`|Valeur booléenne qui indique si le conteneur parent échoue en cas d'erreur dans le conteneur. La valeur par défaut de cette propriété est `False`.<br /><br /> Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailParentOnFailure%2A>.|  
|`ForcedExecutionValue`|Si `ForceExecutionValue` a pour valeur `True`, il s'agit de l'objet qui contient la valeur d'exécution facultative du conteneur. La valeur par défaut de cette propriété est **0**.<br /><br /> Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForcedExecutionValue%2A>.|  
|`ForcedExecutionValueType`|Le type de données `ForcedExecutionValue`. La valeur par défaut de cette propriété est `Int32`.|  
|`ForceExecutionResult`|Valeur qui indique le résultat forcé de l'exécution du package ou conteneur. Cette propriété peut prendre les valeurs `None`, `Success`, `Failure` et `Completion`. La valeur par défaut de cette propriété est `None`.<br /><br /> Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionResult%2A>.|  
|`ForceExecutionValue`|Valeur booléenne qui indique si la valeur d'exécution facultative du conteneur doit être forcée de contenir une valeur particulière. La valeur par défaut de cette propriété est `False`.<br /><br /> Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionValue%2A>.|  
|`ID`|Identificateur global unique du conteneur, affecté lors de la création du package. Cette propriété est en lecture seule.<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ID%2A>.|  
|`IsolationLevel`|Niveau d'isolation de la transaction sur conteneur. Cette propriété peut prendre les valeurs `Unspecified`, `Chaos`, `ReadUncommitted`, `ReadCommitted`, `RepeatableRead`, `Serializable` et `Snapshot`. La valeur par défaut de cette propriété est `Serializable`. Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.IsolationLevel%2A>.|  
|`LocaleID`|Paramètre régional Microsoft Win32. La valeur par défaut de cette propriété est le paramètre régional du système d'exploitation sur l'ordinateur local.<br /><br /> Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LocaleID%2A>.|  
|`LoggingMode`|Valeur qui indique le comportement de journalisation du conteneur. Ces valeurs sont `Disabled`, `Enabled` et `UseParentSetting`. La valeur par défaut de cette propriété est `UseParentSetting`. Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode>.|  
|`MaximumErrorCount`|Nombre maximal d'erreurs pouvant se produire avant l'arrêt de l'exécution d'un conteneur. La valeur par défaut de cette propriété est **1**.<br /><br /> Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.MaximumErrorCount%2A>.|  
|`Name`|nom du conteneur.<br /><br /> Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Name%2A>.|  
|`TransactionOption`|Participation transactionnelle du conteneur. Cette propriété peut prendre les valeurs `NotSupported`, `Supported` et `Required`. La valeur par défaut de cette propriété est `Supported`. Pour plus d’informations, consultez <xref:Microsoft.SqlServer.Dts.Runtime.DTSTransactionOption>.|  
  
 Pour plus d'informations sur toutes les propriétés disponibles pour les conteneurs de boucle Foreach, les conteneurs de boucle For, les conteneurs Sequence et les conteneurs d'hôte de tâche lorsqu'ils sont configurés par programmation, consultez les rubriques API [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] suivantes :  
  
-   T:Microsoft.SqlServer.Dts.Runtime.ForEachLoop  
  
-   T:Microsoft.SqlServer.Dts.Runtime.ForLoop  
  
-   T:Microsoft.SqlServer.Dts.Runtime.Sequence  
  
-   T:Microsoft.SqlServer.Dts.Runtime.TaskHost  
  
## <a name="objects-that-extend-container-functionality"></a>Objets étendant les fonctionnalités des conteneurs  
 Les conteneurs comprennent des flux de contrôle composés d'exécutables et de contraintes de précédence, et peuvent utiliser des gestionnaires d'événements et des variables. Le conteneur d'hôte de tâche est une exception : étant donné que celui-ci encapsule une seule tâche, il n'utilise pas de contraintes de précédence.  
  
### <a name="executables"></a>Exécutables  
 Les exécutables désignent les tâches de niveau conteneur et tous les conteneurs se trouvant dans le conteneur. Un exécutable peut être l’une des tâches et l’un des conteneurs fournis par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , ou bien une tâche personnalisée. Pour plus d’informations, consultez [Integration Services des tâches](integration-services-tasks.md) et des conteneurs de [Integration Services](integration-services-containers.md).  
  
### <a name="precedence-constraints"></a>Contraintes de précédence  
 Les contraintes de priorité relient en un flux de contrôle ordonné les conteneurs et les tâches figurant dans le même conteneur parent. Pour plus d’informations, consultez [Contraintes de précédence](precedence-constraints.md).  
  
### <a name="event-handlers"></a>Gestionnaires d'événements  
 Les gestionnaires d'événements au niveau conteneur répondent aux événements déclenchés par le conteneur ou par les objets figurant dans celui-ci. Pour plus d’informations, consultez [Gestionnaires d’événements Integration Services &#40;SSIS&#41;](../integration-services-ssis-event-handlers.md).  
  
### <a name="variables"></a>Variables  
 Les variables utilisées dans les conteneurs comprennent les variables système de niveau conteneur fournies par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les variables définies par l’utilisateur utilisées par le conteneur. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md).  
  
## <a name="break-points"></a>Points d’arrêt  
 Quand vous définissez un point d’arrêt sur un conteneur et que la condition d’arrêt est **Arrêter lorsque le conteneur reçoit l’événement OnVariableValueChanged**, définissez la variable dans l’étendue du conteneur.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](control-flow.md)  
  
  
