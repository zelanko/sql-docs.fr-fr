---
title: Développement de types spécifiques de composants Script | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e0a811b88537d784c9e1db892003391914d50f5d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58387147"
---
# <a name="developing-specific-types-of-script-components"></a>Développement de types spécifiques de composants Script
  Le composant Script est un outil configurable que vous pouvez utiliser dans le flux de données d'un package pour remplir presque toutes les conditions qui ne sont pas satisfaites par les sources, les transformations et les destinations incluses dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Cette section contient des exemples de code du composant Script qui illustrent les quatre options de configuration du composant Script :  
  
-   en tant que source ;  
  
-   en tant que transformation à sorties synchrones ;  
  
-   en tant que transformation à sorties asynchrones ;  
  
-   en tant que destination.  
  
 Pour obtenir des exemples supplémentaires du composant Script, consultez [Exemples supplémentaires du composant Script](../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d’une source à l’aide du composant Script](creating-a-source-with-the-script-component.md)  
 Explique et montre comment créer une source de flux de données en utilisant le composant Script.  
  
 [Création d’une transformation synchrone à l’aide du composant Script](creating-a-synchronous-transformation-with-the-script-component.md)  
 Explique et montre comment créer une transformation de flux de données à sorties synchrones en utilisant le composant Script. Ce type de transformation modifie des lignes de données en place lorsqu'elles franchissent le composant.  
  
 [Création d’une transformation asynchrone à l’aide du composant Script](../extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 Explique et montre comment créer une transformation de flux de données à sorties asynchrones en utilisant le composant Script. Ce type de transformation doit lire toutes les lignes de données avant de pouvoir ajouter d'autres informations, telles que des agrégats calculés, aux données qui franchissent le composant.  
  
 [Création d’une destination à l’aide du composant Script](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 Explique et montre comment créer une destination de flux de données en utilisant le composant Script.  
  
![Icône Integration Services (petite)](../media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Comparaison des solutions de script et des objets personnalisés](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Développement de types spécifiques de composants de flux de données](../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
