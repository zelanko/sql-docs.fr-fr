---
title: "Étendre le flux de données avec le composant Script | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- data flow task [Integration Services], components
- data flow [Integration Services], extending
- debugging [Integration Services], components
- code design mode [Integration Services]
- metadata [Integration Services]
- scripts [Integration Services], extending data flow
- data flow components [Integration Services], Script component
- components [Integration Services], data flow
- Script component [Integration Services], about Script component
- Script component [Integration Services]
- data flow [Integration Services], components
ms.assetid: 072bc4b8-363a-4131-87c3-240338e2fa5c
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c58a854082fcbd12333be63995e4fcdf2d55aac7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="extending-the-data-flow-with-the-script-component"></a>Extension du flux de données avec le composant Script
  Le composant Script étend les fonctionnalités de flux de données de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages avec du code personnalisé écrit dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic ou [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual c# qui est compilé et exécuté au moment de l’exécution du package. Le composant Script simplifie le développement d'une source, transformation ou destination de flux de données personnalisée, lorsque les sources, les transformations et les destinations incluses dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ne répondent que partiellement à vos besoins. Une fois que vous avez configuré le composant avec les entrées et sorties attendues, celui-ci écrit tout le code d'infrastructure requis, ce qui vous permet de vous concentrer exclusivement sur le code nécessaire au traitement personnalisé.  
  
 Un composant de Script interagit avec le package qui le contient et le flux de données via les classes générées automatiquement dans le **ComponentWrapper** et **BufferWrapper** des éléments qui sont des instances de projet de la <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> et <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> respectivement des classes. Ces classes rendent disponibles les connexions, les variables et les autres éléments de package en tant qu'objets typés et gèrent les entrées et les sorties. Le composant Script peut également utiliser l'espace de noms [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] et la bibliothèque de classes [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ainsi que des assemblys personnalisés, pour implémenter des fonctionnalités personnalisées.  
  
 Le composant Script et le code d'infrastructure qu'il génère simplifient considérablement le processus qui consiste à développer un composant de flux de données personnalisé. Toutefois, pour comprendre le fonctionnement du composant Script, vous pouvez s’avérer utile de lire la section [développer un composant de flux de données personnalisé](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) pour comprendre les étapes du développement d’un composant de flux de données personnalisé.  
  
 Si vous créez une source, une transformation ou une destination que vous envisagez de réutiliser dans plusieurs packages, vous devez développer un composant personnalisé au lieu de vous servir du composant Script. Pour plus d’informations, consultez [Développement d’un composant de flux de données personnalisé](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes fournissent des informations supplémentaires sur le composant Script.  
  
 [Configuration du composant Script dans l’éditeur de composant Script.](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)  
 Les propriétés que vous configurez dans le **éditeur de Transformation de Script** affectent les fonctionnalités et les performances du code du composant Script.  
  
 [Codage et débogage du composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
 Vous utilisez la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] outils pour l’environnement de développement d’Applications (VSTA) pour développer les scripts contenus dans le composant Script.  
  
 [Présentation du modèle objet de composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md)  
 Un nouveau projet de composant Script contient trois éléments de projet avec plusieurs classes ainsi que des propriétés et méthodes générées automatiquement.  
  
 [Utilisation de Variables dans le composant de Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)  
 Le **ComponentWrapper** élément de projet contient les propriétés d’accesseur fortement typé pour les variables de package.  
  
 [Connexion aux Sources de données dans le composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)  
 Le **ComponentWrapper** élément de projet contient également des propriétés d’accesseur fortement typé pour les connexions définies dans le package.  
  
 [Le déclenchement d’événements dans le composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/raising-events-in-the-script-component.md)  
 Vous pouvez déclencher des événements pour signaler des problèmes et des erreurs.  
  
 [Journalisation dans le composant Script](../../../integration-services/extending-packages-scripting/data-flow-script-component/logging-in-the-script-component.md)  
 Vous pouvez enregistrer des informations dans les modules fournisseurs d'informations activés sur le package.  
  
 [Développement de Types spécifiques de composants de Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
 Ces exemples simples expliquent et montrent comment utiliser le composant Script pour développer des sources, transformations et destinations de flux de données.  
  
 [Exemples de composant de Script supplémentaires](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
 Ces exemples simples expliquent et montrent quelques utilisations possibles du composant Script.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de script](../../../integration-services/data-flow/transformations/script-component.md)   
 [Comparaison de la tâche de Script et le composant de Script](../../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  

