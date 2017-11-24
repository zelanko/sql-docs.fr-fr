---
title: "Création de sous-cubes dans MDX (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [MDX], subcubes
- subcubes [MDX]
- filtered views [MDX]
- MDX [Analysis Services], subcubes
- Multidimensional Expressions [Analysis Services], subcubes
- CREATE SUBCUBE statement
ms.assetid: 5403a62b-99ac-4d83-b02a-89bf78bf0f46
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d56fe149317939cfb0b184dcd20b1411514f2ca9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="building-subcubes-in-mdx-mdx"></a>Création de sous-cubes à l'aide de la syntaxe MDX (MDX)
  Un sous-cube est un sous-jeu d'un cube représentant une vue filtrée des données sous-jacentes. En limitant le cube à un sous-cube, vous pouvez améliorer les performances des requêtes.  
  
 Pour définir un sous-cube, vous devez utiliser l’instruction [CREATE SUBCUBE](../../../mdx/mdx-data-definition-create-subcube.md) , comme décrit dans cette rubrique.  
  
## <a name="create-subcube-syntax"></a>Syntaxe CREATE SUBCUBE  
 Utilisez la syntaxe suivante pour créer un sous-cube :  
  
```  
CREATE SUBCUBE Subcube_Identifier AS Subcube_Expression  
```  
  
 La syntaxe CREATE SUBCUBE est relativement simple. Le paramètre *Subcube_Identifier* identifie le cube sur lequel doit se baser le sous-cube. Le paramètre *Subcube_Expression* sélectionne la partie du cube qui deviendra le sous-cube.  
  
 Une fois le sous-cube créé, il devient le contexte de toutes les requêtes MDX jusqu’à la fermeture de la session ou l’exécution de l’instruction [DROP SUBCUBE](../../../mdx/mdx-data-definition-drop-subcube.md) .  
  
### <a name="what-a-subcube-contains"></a>Éléments contenus dans un sous-cube  
 Même si l'instruction CREATE SUBCUBE est relativement simple à utiliser, l'instruction proprement dite n'indique pas explicitement tous les membres qui font partie d'un sous-cube. Lors de la définition d'un sous-cube, les règles suivantes s'appliquent :  
  
-   Si vous incluez le membre **(All)** d’une hiérarchie, vous incluez tous les membres qu’elle contient.  
  
-   Si vous incluez un membre, vous incluez également ses ascendants et ses descendants.  
  
-   Si vous incluez tous les membres d'un niveau, vous incluez tous les membres de la hiérarchie. Les membres des autres hiérarchies seront exclus s'ils ne possèdent pas de membre de ce niveau (par exemple, une hiérarchie déséquilibrée telle qu'une ville qui ne contient aucun client).  
  
-   Un sous-cube contient toujours tous les membres **(All)** du cube.  
  
 En outre, les valeurs d'agrégation contenues dans le sous-cube sont totalisées visuellement. Par exemple, un sous-cube contient `USA`, `WA`et `OR`. La valeur d'agrégation de `USA` sera la somme de `{WA,OR}` , car `WA` et `OR` sont les seuls États définis par le sous-cube. Tous les autres États seront ignorés.  
  
 Par ailleurs, les références explicites à des cellules situées en dehors du sous-cube retournent des valeurs évaluées dans le contexte de l'intégralité du cube. Supposons que vous créez un sous-cube limité à l'année en cours. Ensuite, vous utilisez la fonction [ParallelPeriod](../../../mdx/parallelperiod-mdx.md) pour comparer l’année en cours à l’année précédente. La différence entre les valeurs est retournée, même si la valeur de l'année précédente est située à l'extérieur du sous-cube.  
  
 Pour terminer, si le contexte original n'est pas remplacé, les fonctions de jeu évaluées dans une sous-sélection sont évaluées dans le contexte de celle-ci. Si ce contexte est remplacé, les fonctions de jeu sont évaluées dans le contexte de l'intégralité du cube.  
  
## <a name="create-subcube-example"></a>Exemple de syntaxe CREATE SUBCUBE  
 L'exemple suivant crée un sous-cube qui limite le cube Budget aux comptes 4200 et 4300 uniquement :  
  
 `CREATE SUBCUBE Budget AS SELECT {[Account].[Account].&[4200], [Account].[Account].&[4300] } ON 0 FROM Budget`  
  
 Lorsque vous avez créé un sous-cube pour la session, toutes les requêtes suivantes sont exécutées sur celui-ci plutôt que sur l'intégralité du cube. Vous pouvez par exemple exécuter la requête suivante. Elle ne retourne que les membres des comptes 4200 et 4300.  
  
 `SELECT [Account].[Account].Members ON 0, Measures.Members ON 1 FROM Budget`  
  
## <a name="see-also"></a>Voir aussi  
 [Définition d’un contexte de cube dans une requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)   
 [Principes de base des requêtes MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
