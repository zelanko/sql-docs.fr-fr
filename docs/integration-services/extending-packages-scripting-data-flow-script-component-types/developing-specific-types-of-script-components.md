---
title: "Développement de Types spécifiques de composants de Script | Documents Microsoft"
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
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 458ba4be689ed976a5948380d35f38020f7dd4dd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="developing-specific-types-of-script-components"></a>Développement de types spécifiques de composants Script
  Le composant Script est un outil configurable que vous pouvez utiliser dans le flux de données d'un package pour remplir presque toutes les conditions qui ne sont pas satisfaites par les sources, les transformations et les destinations incluses dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Cette section contient des exemples de code du composant Script qui illustrent les quatre options de configuration du composant Script :  
  
-   en tant que source ;  
  
-   en tant que transformation à sorties synchrones ;  
  
-   en tant que transformation à sorties asynchrones ;  
  
-   en tant que destination.  
  
 Pour obtenir des exemples supplémentaires de composant de Script, consultez [des exemples supplémentaires de composant de Script](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Création d’une source à l’aide du composant Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)  
 Explique et montre comment créer une source de flux de données en utilisant le composant Script.  
  
 [Création d’une transformation synchrone à l’aide du composant Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
 Explique et montre comment créer une transformation de flux de données à sorties synchrones en utilisant le composant Script. Ce type de transformation modifie des lignes de données en place lorsqu'elles franchissent le composant.  
  
 [Création d’une transformation asynchrone à l’aide du composant Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 Explique et montre comment créer une transformation de flux de données à sorties asynchrones en utilisant le composant Script. Ce type de transformation doit lire toutes les lignes de données avant de pouvoir ajouter d'autres informations, telles que des agrégats calculés, aux données qui franchissent le composant.  
  
 [Création d’une destination à l’aide du composant Script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 Explique et montre comment créer une destination de flux de données en utilisant le composant Script.  
  
## <a name="see-also"></a>Voir aussi  
 [Comparaison des Solutions de script et des objets personnalisés](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Composants de flux de développement de Types spécifiques de données](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
