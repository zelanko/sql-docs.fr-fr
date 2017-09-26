---
title: "Vue d’ensemble de la programmation d’Integration Services | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Integration Services, programming
- architecture [Integration Services]
- assemblies [Integration Services]
- SSIS, programming
- SQL Server Integration Services, programming
- run-time engine [Integration Services]
- packages [Integration Services], programming
- data flow engine [Integration Services]
- languages [Integration Services]
ms.assetid: 262babc6-eea5-4609-bc65-07d64cbcfee9
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 47cb31613e30199902335d891b9f5777757feed3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="integration-services-programming-overview"></a>Vue d'ensemble de la programmation Integration Services
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] possède une architecture qui sépare le déplacement des données et transformation de gestion et de flux de contrôle du package. Cette architecture se définit par deux moteurs distincts qui peuvent être automatisés et étendus lors de la programmation [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Le moteur d'exécution implémente l'infrastructure de flux de contrôle et de gestion de packages qui permet aux développeurs de contrôler le flux d'exécution et de définir des options pour la journalisation, les gestionnaires d'événements et les variables. Le moteur de flux de données est un moteur spécialisé, hautement performant, exclusivement dédié à l'extraction, la transformation et le chargement de données. La programmation [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] s'effectue à partir de ces deux moteurs.  
  
 L'image suivante représente l'architecture d'[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 ![Architecture de Services d’intégration](../integration-services/media/mw-dts-01.gif "architecture d’Integration Services")  
  
## <a name="integration-services-run-time-engine"></a>Moteur d'exécution Integration Services  
 Le moteur d'exécution [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contrôle la gestion et l'exécution de packages, en implémentant l'infrastructure qui active l'ordre d'exécution, la journalisation, les variables et la gestion d'événements. La programmation du moteur d'exécution [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] permet aux développeurs d'automatiser la création, la configuration et l'exécution de packages et de créer des tâches personnalisées et d'autres extensions.  
  
 Pour plus d’informations, consultez [extension du Package avec la tâche de Script](../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md), [développement d’une tâche personnalisée](../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md), et [génération de Packages par programme](../integration-services/building-packages-programmatically/building-packages-programmatically.md).  
  
## <a name="integration-services-data-flow-engine"></a>Moteur de flux de données Integration Services  
 Le moteur de flux de données gère la tâche de flux de données, qui est une tâche spécialisée, hautement performante, destinée à déplacer et transformer les données provenant de sources disparates. Contrairement à d'autres tâches, la tâche de flux de données contient des objets supplémentaires, appelés composants de flux de données, qui peuvent être des sources, des transformations ou des destinations. Ces composants constituent les principaux éléments en mouvement de la tâche. Ils définissent le déplacement et la transformation des données. La programmation du moteur de flux de données permet aux développeurs d'automatiser la création et la configuration des composants dans une tâche de flux de données et de créer des composants personnalisés.  
  
 Pour plus d’informations, consultez [étendre le flux de données avec le composant Script](../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md), [développer un composant de flux de données personnalisé](../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), et [génération de Packages par programme](../integration-services/building-packages-programmatically/building-packages-programmatically.md).  
  
## <a name="supported-languages"></a>Langues prises en charge  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]prend entièrement en charge la [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Les développeurs peuvent ainsi programmer [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans les langages compatibles .NET de leur choix. Bien qu'ils soient écrits en code natif, le moteur d'exécution et le moteur de flux de données sont accessibles par le biais d'un modèle objet entièrement managé.  
  
 Vous pouvez programmer [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages, des tâches personnalisées et des composants dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou dans un autre éditeur de code ou de texte. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offre de nombreux outils et fonctionnalités au développeur pour simplifier et accélérer les cycles itératifs du codage, du débogage et du test. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] facilite également le déploiement. Toutefois, vous n'avez pas besoin de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour compiler et générer des projets de code [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Le Kit de développement [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK inclut les compilateurs et les outils connexes [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] et [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
> [!IMPORTANT]  
>  Le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] est installé par défaut avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], mais pas le Kit de développement [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. Les liens vers les rubriques relatives au Kit de développement figurant dans cette section ne fonctionnent que si le Kit de développement est installé sur l'ordinateur et que la documentation qui lui est propre figure dans la documentation en ligne. Après avoir installé le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK, vous pouvez ajouter la documentation du Kit de développement logiciel à la collection de la documentation en ligne et de la table des matières en suivant les instructions de [ajouter ou supprimer de Documentation produit de SQL Server](http://msdn.microsoft.com/library/ef798cc8-87cf-4d60-a7bf-9e061bdd0052).  
  
 Le [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tâche de Script et composant Script utilisent [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) comme environnement de script incorporé. VSTA prend en charge [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic et [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.  
  
> [!NOTE]  
>  Les interfaces de programmation d'applications [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sont incompatibles avec les langages de script COM, tels que VBScript.  
  
## <a name="locating-assemblies"></a>Recherche d'assemblys  
 Dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], les assemblys [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ont été mis à niveau vers le .NET 4.0. Il existe un global assembly cache distinct pour .NET 4, situé dans * \<lecteur >*: \Windows\Microsoft.NET\assembly. Vous trouverez tous les assemblys [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sous ce chemin d'accès, en général dans le dossier GAC_MSIL.  
  
 Comme dans les versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], le cœur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fichiers .dll d’extensibilité se trouvent également dans * \<lecteur >*: \Program Files\Microsoft SQL Server\100\SDK\Assemblies.  
  
## <a name="commonly-used-assemblies"></a>Assemblys couramment utilisés  
 Le tableau suivant répertorie les assemblys fréquemment utilisés lors de la programmation [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] à l'aide du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
|Assembly| Description|  
|--------------|-----------------|  
|Microsoft.SqlServer.ManagedDTS.dll|Contient le moteur d'exécution managé.|  
|Microsoft.SqlServer.RuntimeWrapper.dll|Contient l'assembly PIA (Primary Interop Assembly), ou wrapper, du moteur d'exécution natif.|  
|Microsoft.SqlServer.PipelineHost.dll|Contient le moteur de flux de données managé.|  
|Microsoft.SqlServer.PipelineWrapper.dll|Contient l'assembly PIA (Primary Interop Assembly), ou wrapper, du moteur de flux de données natif.|  
  
  
