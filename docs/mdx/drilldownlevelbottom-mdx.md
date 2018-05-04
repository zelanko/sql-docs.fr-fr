---
title: DrilldownLevelBottom (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DRILLDOWNLEVELBOTTOM
dev_langs:
- kbMDX
helpviewer_keywords:
- DrilldownLevelBottom function
ms.assetid: c00a6a02-e618-4713-805a-870e042f2d51
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 2628ef6a691772a4fc085130e1d1482b2bd4cb2e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="drilldownlevelbottom-mdx"></a>DrilldownLevelBottom (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Extrait vers le bas les membres les plus bas d'un jeu, d'un niveau à partir d'un niveau spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DrilldownLevelBottom(Set_Expression, Count [,[<Level_Expression>] [,[<Numeric_Expression>][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Compter*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
 *Numeric_expression*  
 Ce paramètre est facultatif. Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
 *Include_Calc_Members*  
 Ce paramètre est facultatif. Un mot clé qui ajoute des membres calculés aux résultats de l’exploration vers le bas.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, la **DrilldownLevelBottom** fonction trie, par ordre croissant, les enfants de chaque membre dans le jeu spécifié, en fonction de la valeur spécifiée, telle qu’évaluée sur le jeu de membres enfants. Si une expression numérique n'est pas spécifiée, la fonction trie, dans l'ordre croissant, les enfants de chaque membre dans le jeu spécifié, d'après les valeurs des cellules représentées par le jeu de membres enfants, comme déterminé par le contexte de requête ; ce comportement est semblable aux fonctions BottomCount et Tail (MDX) qui retournent un jeu de membres dans l'ordre naturel, sans tri.  
  
 Après le tri, le **DrilldownLevelBottom** fonction retourne un jeu qui contient les membres parents et le nombre de membres enfants spécifiés dans *nombre*, avec la valeur la plus faible.  
  
 Le **DrilldownLevelBottom** fonction est similaire à la [DrilldownLevel](../mdx/drilldownlevel-mdx.md) (fonction), mais au lieu d’inclure tous les enfants de chaque membre au niveau spécifié, le **DrilldownLevelBottom** fonction retourne le nombre le plus bas des membres enfants.  
  
 Interrogez la propriété XMLA MdpropMdxDrillFunctions vous permet de vérifier le niveau de prise en charge par le serveur pour les fonctions d’extraction ; consultez [pris en charge les propriétés XMLA &#40;XMLA&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) pour plus d’informations.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne les trois enfants inférieurs du niveau Product Category en fonction de la mesure par défaut. Dans l'exemple de cube Adventure Works, les trois derniers enfants pour Accessories sont Tires and Tubes, Pumps et Panniers. Dans Management Studio, dans la fenêtre de requête MDX, vous pouvez accéder à Products | Product Categories | Members | All Products | Accessories pour afficher la liste complète. Vous pouvez augmenter l'argument Count pour retourner davantage de membres.  
  
```  
SELECT DrilldownLevelBottom   
   ([Product].[Product Categories].children,  
   3,  
   [Product].[Product Categories].[Category])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 L’exemple suivant illustre l’utilisation de la **include_calc_members** indicateur, utilisé pour inclure les membres calculés dans le niveau de zoom. La mesure [Reseller Order Count] est ajoutée à la **DrilldownLevelBottom** instruction pour vous assurer que les résultats sont triés par cette mesure. Pour voir le membre calculé, il est nécessaire d'augmenter Count à au moins 9.  
  
```  
WITH MEMBER   
[Product].[Product Categories].[Category].&[3].[Premium Clothes] AS  
[Product].[Product Categories].[Subcategory].&[18] +  
[Product].[Product Categories].[Subcategory].&[21]  
SELECT [Measures].[Reseller Order Count] ON 0,  
DRILLDOWNLEVELBOTTOM(  
  [Product].[Product Categories].children ,  
  9,  
  [Product].[Product Categories].[Category] ,  
  [Measures].[Reseller Order Count],  
  INCLUDE_CALC_MEMBERS ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DrilldownLevel & #40 ; MDX & #41 ;](../mdx/drilldownlevel-mdx.md)   
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
