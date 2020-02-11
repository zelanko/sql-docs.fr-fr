---
title: Extension du flux de données avec le composant Script | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 051f2ed14e8218a3909a43052f08e0e339138dab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62894803"
---
# <a name="extending-the-data-flow-with-the-script-component"></a>Extension du flux de données avec le composant Script
  Le composant script étend les fonctionnalités de transmission de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] données des packages à l’aide [!INCLUDE[msCoName](../../../includes/msconame-md.md)] de code [!INCLUDE[msCoName](../../../includes/msconame-md.md)] personnalisé écrit en Visual Basic ou Visual C# qui est compilé et exécuté au moment de l’exécution du package. Le composant Script simplifie le développement d'une source, transformation ou destination de flux de données personnalisée, lorsque les sources, les transformations et les destinations incluses dans [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ne répondent que partiellement à vos besoins. Une fois que vous avez configuré le composant avec les entrées et sorties attendues, celui-ci écrit tout le code d'infrastructure requis, ce qui vous permet de vous concentrer exclusivement sur le code nécessaire au traitement personnalisé.  
  
 Un composant Script interagit avec le package qui le contient et le flux de données au moyen des classes générées automatiquement dans les éléments de projet `ComponentWrapper` et `BufferWrapper`, qui sont respectivement des instances des classes <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> et <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>. Ces classes rendent disponibles les connexions, les variables et les autres éléments de package en tant qu'objets typés et gèrent les entrées et les sorties. Le composant Script peut également utiliser l'espace de noms [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] et la bibliothèque de classes [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ainsi que des assemblys personnalisés, pour implémenter des fonctionnalités personnalisées.  
  
 Le composant Script et le code d'infrastructure qu'il génère simplifient considérablement le processus qui consiste à développer un composant de flux de données personnalisé. Toutefois, pour comprendre le fonctionnement du composant Script, il peut être utile de lire la section [Développement d’un composant de flux de données personnalisé](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) pour maîtriser les étapes du développement d’un composant de flux de données personnalisé.  
  
 Si vous créez une source, une transformation ou une destination que vous envisagez de réutiliser dans plusieurs packages, vous devez développer un composant personnalisé au lieu de vous servir du composant Script. Pour plus d’informations, consultez [Développement d’un composant de flux de données personnalisé](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes fournissent des informations supplémentaires sur le composant Script.  
  
 [Configuration du composant Script dans l'éditeur de composant de script](configuring-the-script-component-in-the-script-component-editor.md)  
 Les propriétés que vous configurez dans l’**Éditeur de transformation de script** affectent les fonctionnalités et les performances du code du composant Script.  
  
 [Codage et débogage du composant Script] (coding-and-debugging-the-script-component.md  
 Vous utilisez l' [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] environnement de développement Tools for Applications (VSTA) pour développer les scripts contenus dans le composant script.  
  
 [Présentation du modèle objet du composant Script](understanding-the-script-component-object-model.md)  
 Un nouveau projet de composant Script contient trois éléments de projet avec plusieurs classes ainsi que des propriétés et méthodes générées automatiquement.  
  
 [Utilisation de variables dans le composant Script](using-variables-in-the-script-component.md)  
 L'élément de projet `ComponentWrapper` contient des propriétés d'accesseur fortement typées pour les variables de package.  
  
 [Connexion aux sources de données dans le composant Script](connecting-to-data-sources-in-the-script-component.md)  
 L'élément de projet `ComponentWrapper` contient également des propriétés d'accesseur fortement typées pour les connexions définies dans le package.  
  
 [Déclenchement d'événements dans le composant Script](raising-events-in-the-script-component.md)  
 Vous pouvez déclencher des événements pour signaler des problèmes et des erreurs.  
  
 [Journalisation dans le composant Script](logging-in-the-script-component.md)  
 Vous pouvez enregistrer des informations dans les modules fournisseurs d'informations activés sur le package.  
  
 [Développement de types spécifiques de composants Script](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
 Ces exemples simples expliquent et montrent comment utiliser le composant Script pour développer des sources, transformations et destinations de flux de données.  
  
 [Exemples supplémentaires du composant Script](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
 Ces exemples simples expliquent et montrent quelques utilisations possibles du composant Script.  
  
![Icône de Integration Services (petite)](../../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les téléchargements, articles, exemples et vidéos les plus récents de [!INCLUDE[msCoName](../../../includes/msconame-md.md)], ainsi que les solutions retenues par la communauté informatique, consultez la page [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant script](../../data-flow/transformations/script-component.md)   
 [Comparaison de la tâche de script et du composant Script](../comparing-the-script-task-and-the-script-component.md)  
  
  
