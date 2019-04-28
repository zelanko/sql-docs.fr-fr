---
title: DrilldownMemberTop (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3dd1128bfafb052936e742f7ce56529b1222333a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62690847"
---
# <a name="drilldownmembertop-mdx"></a>DrilldownMemberTop (MDX)


  Extrait vers le bas les membres dans un jeu spécifié qui sont présents dans un second jeu spécifié, ce qui limite l'ensemble de résultats à un nombre spécifique de membres. Vous pouvez également, cette fonction extrait vers le bas sur un jeu de tuples à l’aide de la première hiérarchie de tuple ou de la hiérarchie éventuellement spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DrillDownMemberTop(<Set_Expression1>, <Set_Expression2>, <Count> [,[<Numeric_Expression>] [,[<Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Compter*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
 *Hierarchy*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
 *Récursive*  
 Mot clé qui indique une comparaison récursive de jeux.  
  
 *Include_Calc_Members*  
 Mot clé permettant d'activer les membres calculés à inclure dans les résultats de l'extraction vers le bas.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, le **DrilldownMemberTop** fonction trie, par ordre décroissant, les enfants de chaque membre dans le premier jeu selon la valeur de l’expression numérique, telle qu’évaluée sur le jeu d’enfant membres. Si aucune expression numérique n'est spécifiée, cette fonction trie, par ordre décroissant, les enfants de chaque membre dans le premier jeu selon les valeurs des cellules représentées par le jeu des membres enfants, comme le détermine le contexte de la requête. Ce comportement est semblable aux fonctions TopCount et Head (MDX) qui retournent un jeu de membres dans l'ordre naturel, sans tri.  
  
 Après le tri, le **DrilldownMemberTop** fonction retourne un jeu qui contient les membres parents et le nombre de membres enfants spécifiés dans *Count,* avec la valeur la plus élevée et qui sont contenues dans les deux ensembles .  
  
 Si **récursive** est spécifié, la fonction trie le premier jeu comme décrit précédemment, puis compare de manière récursive les membres du premier jeu, organisées dans une hiérarchie, par rapport au deuxième jeu *.* La fonction récupère le premier nombre d’enfants pour chaque membre dans le premier jeu est également présent dans le deuxième jeu.  
  
 Le premier jeu peut contenir des tuples au lieu de membres. Descente de tuple est une extension de OLE DB et retourne un jeu de tuples au lieu de membres.  
  
 Le **DrilldownMemberTop** fonction est similaire à la [DrilldownMember](../mdx/drilldownmember-mdx.md) de fonctionner, mais au lieu d’inclure tous les enfants de chaque membre dans le premier jeu est également présent dans le deuxième jeu, le **DrilldownMemberTop** fonction retourne le premier nombre de membres enfants pour chaque membre.  
  
 Interrogez la propriété XMLA MdpropMdxDrillFunctions vous permet de vérifier le niveau de prise en charge fournis par le serveur pour les fonctions d’extraction ; consultez [propriétés XMLA prises en charge &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) pour plus d’informations.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant effectue une extraction vers le bas dans la catégorie d'habillement pour retourner les trois sous-catégories de vêtements enregistrant le plus grand nombre de commandes expédiées.  
  
```  
SELECT DrilldownMemberTop   ({[Product].[Product Categories].[All Products],        
[Product].[Product Categories].[Category].Bikes,        
[Product].[Product Categories].[Category].Clothing},     
{[Product].[Product Categories].[Category].Clothing},     
3,     
[Measures].[Reseller Order Quantity])     
ON 0     
FROM [Adventure Works]     
WHERE [Measures].[Reseller Order Quantity]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
