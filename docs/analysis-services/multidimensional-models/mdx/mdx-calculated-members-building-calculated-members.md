---
title: "Création de membres calculés dans MDX (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDX [Analysis Services], calculated members
- calculated members [MDX]
- Multidimensional Expressions [Analysis Services], calculated members
- queries [MDX], calculated members
ms.assetid: 9322e8b8-43e1-4e02-a7d1-e41a586a5bb8
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: cbfe97ab13483ccaf31134bfa45ab5b583f797d7
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="mdx-calculated-members---building-calculated-members"></a>MDX Calculated Members - création de membres calculés
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Dans MDX (Multidimensional Expressions), un membre calculé est un membre qui est résolu par le retour d'une valeur issue du calcul d'une expression MDX. Cette définition anodine couvre un vaste champ d'action. La possibilité de bâtir et d'utiliser des membres calculés dans une requête MDX est un élément fondamental de la manipulation des données multidimensionnelles.  
  
 Vous pouvez créer des membres calculés en n'importe quel point d'une hiérarchie. Vous pouvez également créer des membres calculés qui dépendent non seulement des membres existants d'un cube, mais aussi d'autres membres calculés définis dans la même expression MDX.  
  
 Vous pouvez définir pour un membre calculé l'un des contextes suivants :  
  
-   **Étendue de requête** Pour créer un membre calculé défini en tant que partie d’une requête MDX, et dont l’étendue est donc limitée à la requête, utilisez le mot clé WITH. Vous pouvez ensuite utiliser le membre calculé au sein d'une instruction MDX SELECT. Ainsi, vous pouvez modifier le membre calculé créé à l'aide du mot clé WITH sans porter atteinte à l'instruction SELECT.  
  
     Pour plus d’informations sur l’utilisation du mot clé WITH pour la création de membres calculés, consultez [Création de membres calculés d’étendue de requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md).  
  
-   **Étendue de session**  Pour créer un membre calculé dont l’étendue est plus vaste que le contexte de la requête, c’est-à-dire dont l’étendue soit la durée de la session MDX, utilisez l’instruction CREATE MEMBER. Un membre calculé défini à l'aide de l'instruction CREATE MEMBER est disponible pour toutes les requêtes MDX de cette session. L'instruction CREATE MEMBER est appropriée par exemple dans le cas d'une application cliente qui réutilise le même jeu dans différentes requêtes.  
  
     Pour plus d’informations sur l’utilisation de l’instruction CREATE MEMBER pour la création de membres calculés dans une session, consultez [Création de membres calculés au niveau de la session &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une instruction MEMBER &#40; MDX &#41;](../../../mdx/mdx-data-definition-create-member.md)   
 [Référence des fonctions MDX &#40; MDX &#41;](../../../mdx/mdx-function-reference-mdx.md)   
 [Instruction SELECT &#40; MDX &#41;](../../../mdx/mdx-data-manipulation-select.md)  
  
  
