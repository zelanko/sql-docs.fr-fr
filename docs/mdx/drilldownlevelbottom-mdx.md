---
title: DrilldownLevelBottom (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 83dc56056e6000a789c8944b38326c23d7632bb7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68049286"
---
# <a name="drilldownlevelbottom-mdx"></a>DrilldownLevelBottom (MDX)


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
 facultatif. Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
 *Include_Calc_Members*  
 facultatif. Un mot clé qui ajoute des membres calculés aux résultats de l’exploration vers le bas.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, le **DrilldownLevelBottom** fonction trie, par ordre croissant, les enfants de chaque membre dans le jeu spécifié, en fonction de la valeur spécifiée, telle qu’évaluée sur le jeu de membres enfants. Si une expression numérique n'est pas spécifiée, la fonction trie, dans l'ordre croissant, les enfants de chaque membre dans le jeu spécifié, d'après les valeurs des cellules représentées par le jeu de membres enfants, comme déterminé par le contexte de requête ; ce comportement est semblable aux fonctions BottomCount et Tail (MDX) qui retournent un jeu de membres dans l'ordre naturel, sans tri.  
  
 Après le tri, le **DrilldownLevelBottom** fonction retourne un jeu qui contient les membres parents et le nombre de membres enfants spécifiés dans *nombre*, avec la valeur la plus basse.  
  
 Le **DrilldownLevelBottom** fonction est similaire à la [DrilldownLevel](../mdx/drilldownlevel-mdx.md) (fonction), mais au lieu d’inclure tous les enfants de chaque membre au niveau spécifié, le  **DrilldownLevelBottom** fonction retourne le nombre le plus bas des membres enfants.  
  
 Interrogez la propriété XMLA MdpropMdxDrillFunctions vous permet de vérifier le niveau de prise en charge fournis par le serveur pour les fonctions d’extraction ; consultez [propriétés XMLA prises en charge &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) pour plus d’informations.  
  
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
  
 L’exemple suivant illustre l’utilisation de la **include_calc_members** indicateur, utilisé pour inclure des membres calculés dans le niveau de zoom. La mesure [Reseller Order Count] est ajoutée à la **DrilldownLevelBottom** instruction pour vous assurer que les résultats sont triés par cette mesure. Pour voir le membre calculé, il est nécessaire d'augmenter Count à au moins 9.  
  
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
 [DrilldownLevel &#40;MDX&#41;](../mdx/drilldownlevel-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
