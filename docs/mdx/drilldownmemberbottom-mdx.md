---
title: DrilldownMemberBottom (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: DRILLDOWNMEMBERBOTTOM
dev_langs: kbMDX
helpviewer_keywords: DrilldownMemberBottom function
ms.assetid: 603927ba-68f6-4e7a-b17f-44cad33bdfb0
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a0b8ce3ba24d95b276143629d11051f93c65f18c
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="drilldownmemberbottom-mdx"></a>DrilldownMemberBottom (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Extrait vers le bas les membres dans un jeu spécifié qui sont présents dans un second jeu spécifié, ce qui limite l'ensemble de résultats à un nombre spécifique de membres. Cette fonction extrait également vers le bas un jeu de tuples à l'aide de la première hiérarchie de tuple ou de la hiérarchie éventuellement spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DrillDownMemberBottom(<Set_Expression1>, <Set_Expression2>, <Count> [,[<Numeric_Expresion>] [,[<Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Nombre*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
 *Numeric_expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
 *Hierarchy*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
 *Récursive*  
 Mot clé qui indique une comparaison récursive de jeux.  
  
 *Include_Calc_Members*  
 Mot clé permettant d'activer les membres calculés à inclure dans les résultats de l'extraction vers le bas.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, la **DrilldownMemberBottom** fonction trie, par ordre croissant, les enfants de chaque membre dans le premier jeu, en fonction de la valeur de l’expression numérique, telle qu’évaluée sur le jeu de membres enfants. Si aucune expression numérique n'est spécifiée, cette fonction trie, par ordre croissant, les enfants de chaque membre dans le premier jeu selon les valeurs des cellules représentées par le jeu des membres enfants, comme le détermine le contexte de la requête. Ce comportement est semblable aux fonctions BottomCount et Tail (MDX) qui retournent un jeu de membres dans l'ordre naturel, sans tri.  
  
 Après le tri, le **DrilldownMemberBottom** fonction retourne un jeu qui contient les membres parents et le nombre de membres enfants spécifiés dans *Count,* avec la valeur la plus basse et contenues dans les deux ensembles.  
  
 Si **récursive** est spécifié, la fonction trie le premier jeu comme décrit précédemment, puis compare de manière récursive les membres du premier jeu, organisées dans une hiérarchie, par rapport au deuxième jeu. La fonction extrait le nombre le plus faible d'enfants pour chaque membre du premier jeu également présent dans le deuxième jeu.  
  
 Le premier jeu peut contenir des tuples au lieu de membres. Descente de tuple est une extension de OLE DB et retourne un jeu de tuples au lieu de membres.  
  
 Le **DrilldownMemberBottom** fonction est similaire à la [DrilldownMember](../mdx/drilldownmember-mdx.md) de fonctionner, mais au lieu d’inclure tous les enfants de chaque membre dans le premier jeu est également présent dans le deuxième jeu, le **DrilldownMemberBottom** fonction retourne le nombre le plus faible de membres enfants pour chaque membre.  
  
 Interrogez la propriété XMLA MdpropMdxDrillFunctions vous permet de vérifier le niveau de prise en charge par le serveur pour les fonctions d’extraction ; consultez [pris en charge les propriétés XMLA &#40; XMLA &#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
