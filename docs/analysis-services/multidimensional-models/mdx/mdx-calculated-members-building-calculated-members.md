---
title: "Création de membres calculés dans MDX (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDX [Analysis Services], calculated members
- calculated members [MDX]
- Multidimensional Expressions [Analysis Services], calculated members
- queries [MDX], calculated members
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bc980db3ce9f468a98e7fbfb83d54981c4b6e6cd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-calculated-members---building-calculated-members"></a>MDX Calculated Members - création de membres calculés
  Dans MDX (Multidimensional Expressions), un membre calculé est un membre qui est résolu par le retour d'une valeur issue du calcul d'une expression MDX. Cette définition anodine couvre un vaste champ d'action. La possibilité de bâtir et d'utiliser des membres calculés dans une requête MDX est un élément fondamental de la manipulation des données multidimensionnelles.  
  
 Vous pouvez créer des membres calculés en n'importe quel point d'une hiérarchie. Vous pouvez également créer des membres calculés qui dépendent non seulement des membres existants d'un cube, mais aussi d'autres membres calculés définis dans la même expression MDX.  
  
 Vous pouvez définir pour un membre calculé l'un des contextes suivants :  
  
-   **Étendue de requête** Pour créer un membre calculé défini en tant que partie d’une requête MDX, et dont l’étendue est donc limitée à la requête, utilisez le mot clé WITH. Vous pouvez ensuite utiliser le membre calculé au sein d'une instruction MDX SELECT. Ainsi, vous pouvez modifier le membre calculé créé à l'aide du mot clé WITH sans porter atteinte à l'instruction SELECT.  
  
     Pour plus d’informations sur l’utilisation du mot clé WITH pour la création de membres calculés, consultez [Création de membres calculés d’étendue de requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md).  
  
-   **Étendue de session**  Pour créer un membre calculé dont l’étendue est plus vaste que le contexte de la requête, c’est-à-dire dont l’étendue soit la durée de la session MDX, utilisez l’instruction CREATE MEMBER. Un membre calculé défini à l'aide de l'instruction CREATE MEMBER est disponible pour toutes les requêtes MDX de cette session. L'instruction CREATE MEMBER est appropriée par exemple dans le cas d'une application cliente qui réutilise le même jeu dans différentes requêtes.  
  
     Pour plus d’informations sur l’utilisation de l’instruction CREATE MEMBER pour la création de membres calculés dans une session, consultez [Création de membres calculés au niveau de la session &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction CREATE MEMBER &#40;MDX&#41;](../../../mdx/mdx-data-definition-create-member.md)   
 [Informations de référence sur les fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)   
 [Instruction SELECT &#40; MDX &#41;](../../../mdx/mdx-data-manipulation-select.md)  
  
  

