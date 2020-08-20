---
description: DrilldownLevelTop (MDX)
title: DrilldownLevelTop (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d0bb64acad5e29ff6eed5570e8764fd6a76a7547
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500512"
---
# <a name="drilldownleveltop-mdx"></a>DrilldownLevelTop (MDX)


  Extrait vers le bas les membres les plus hauts d'un jeu, d'un niveau à partir du niveau spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DrilldownLevelTop(<Set_Expression>, <Count> [,[<Level_Expression>] [,[<Numeric_Expression>][,INCLUDE_CALC_MEMBERS]]])  
  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Count*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
 *Level_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un niveau.  
  
 *Numeric_Expression*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre.  
  
 *Include_Calc_Members*  
 Mot clé pour ajouter les membres calculés aux résultats de l'extraction vers le bas.  
  
## <a name="remarks"></a>Notes  
 Si une expression numérique est spécifiée, la fonction **DrilldownLevelTop** trie, dans l’ordre décroissant, les enfants de chaque membre dans le jeu spécifié en fonction de la valeur de l’expression numérique, telle qu’évaluée sur le jeu de membres enfants. Si une expression numérique n'est pas spécifiée, cette fonction trie, par ordre décroissant, les enfants de chaque membre dans le jeu spécifié selon les valeurs des cellules représentées par le jeu des membres enfants, comme le détermine le contexte de la requête.  
  
 Après le tri, la fonction **DrilldownLevelTop** retourne un jeu qui contient les membres parents et le nombre de membres enfants, spécifiés dans *Count,* avec la valeur la plus élevée.  
  
 La fonction **DrilldownLevelTop** est similaire à la fonction [DrilldownLevel](../mdx/drilldownlevel-mdx.md) , mais au lieu d’inclure tous les enfants de chaque membre au niveau spécifié, la fonction **DrilldownLevelTop** retourne le plus grand nombre de membres enfants.  
  
 L’interrogation de la propriété XMLA MdpropMdxDrillFunctions vous permet de vérifier le niveau de prise en charge fourni par le serveur pour les fonctions de perçage. Pour plus d’informations, consultez [Propriétés XMLA prises en charge &#40;&#41;XMLA ](https://docs.microsoft.com/analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) .  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne les trois enfants supérieurs du niveau Product Category en fonction de la mesure par défaut. Dans l'exemple de cube Adventure Works, les trois premiers enfants pour Accessories sont Bike Racks, Bike Stands et Bottles and Cages. Dans Management Studio, dans la fenêtre de requête MDX, vous pouvez accéder à Products | Product Categories | Members | All Products | Accessories pour afficher la liste complète. Vous pouvez augmenter l'argument Count pour retourner davantage de membres.  
  
```  
SELECT DrilldownLevelTop   
   ([Product].[Product Categories].children,  
   3,  
   [Product].[Product Categories].[Category])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 L’exemple suivant illustre l’utilisation de l’indicateur **INCLUDE_CALC_MEMBERS** , utilisé pour inclure des membres calculés dans le niveau d’exploration. La mesure [Reseller Order Count] est incluse dans l’instruction **DrilldownLevelTop** pour garantir que les valeurs de retour sont triées par cette mesure.  
  
```  
WITH MEMBER   
[Product].[Product Categories].[Category].&[3].[Premium Clothes] AS  
[Product].[Product Categories].[Subcategory].&[18] +  
[Product].[Product Categories].[Subcategory].&[21]  
SELECT [Measures].[Reseller Order Count] ON 0,  
DRILLDOWNLEVELTOP(  
  [Product].[Product Categories].children ,  
  2,  
  [Product].[Product Categories].[Category] ,  
  [Measures].[Reseller Order Count],  
  INCLUDE_CALC_MEMBERS ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DrilldownLevel&#41;MDX &#40;](../mdx/drilldownlevel-mdx.md)   
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
