---
title: Génération de jeux nommés dans MDX (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], named sets
- named sets [MDX]
- sets [MDX]
- MDX [Analysis Services], named sets
- queries [MDX], named sets
- set expressions [MDX]
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 98d363ab09e75905b13503687fe425a981c790e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074145"
---
# <a name="building-named-sets-in-mdx-mdx"></a>Création de jeux nommés à l'aide d'expressions MDX (MDX)
  Une expression d'ensemble peut être une déclaration assez longue, complexe et donc difficile à assimiler. Ou bien, il est possible que vous l'utilisiez si souvent qu'il devient pénible de la redéfinir à chaque fois. Pour faciliter l’utilisation d’une expression longue, complexe ou fréquemment utilisée, MDX (Multidimensional Expressions) vous permet de traiter une telle expression sous forme de *jeu nommé*.  
  
 Un jeu nommé est essentiellement une expression d'ensemble à laquelle un alias a été attribué. Il peut comprendre les membres ou les fonctions pouvant être normalement intégrées dans un jeu. MDX traitant l'alias du jeu nommé comme une expression d'ensemble, vous pouvez utiliser cet alias où une telle expression est acceptée.  
  
 Vous pouvez définir pour un jeu nommé l'un des contextes suivants :  
  
-   **Étendue de requête** Pour créer un jeu nommé défini dans le cadre d’une requête MDX et dont l’étendue est donc limitée à la requête, utilisez le mot clé WITH. Vous pouvez ensuite utiliser le jeu nommé au sein d'une instruction MDX SELECT. De la sorte, vous pouvez modifier le jeu nommé créé à l'aide du mot clé WITH sans porter atteinte à l'instruction SELECT.  
  
     Pour plus d’informations sur l’utilisation du mot clé WITH pour la création de jeux nommés, consultez [Création de jeux nommés d’étendue de requête &#40;MDX&#41;](mdx-named-sets-creating-query-scoped-named-sets.md).  
  
-   **Étendue de session** Pour créer un jeu nommé dont l’étendue est plus vaste que le contexte de la requête, c’est-à-dire dont l’étendue est la durée de vie de la session MDX, vous utilisez l’instruction CREATe SET. Un jeu nommé défini à l'aide de l'instruction CREATE SET est disponible pour toutes les requêtes MDX de cette session. L'instruction CREATE SET est appropriée par exemple dans le cas d'une application cliente qui réutilise le même jeu dans différentes requêtes.  
  
     Pour plus d’informations sur l’utilisation de l’instruction CREATE SET pour la création de jeux nommés dans une session, consultez [Création de jeux nommés dans l’étendue de session &#40;MDX&#41;](mdx-named-sets-creating-session-scoped-named-sets.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction SELECT &#40;&#41;MDX](/sql/mdx/mdx-data-manipulation-select)   
 [Instruction CREATe SET &#40;&#41;MDX](/sql/mdx/mdx-data-definition-create-set)   
 [Notions de base des requêtes MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
