---
title: Item (Tuple) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5740095752b482430cd718d0e2bff813449d92ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68105223"
---
# <a name="item-tuple-mdx"></a>Item (Tuple) (MDX)


  Retourne un tuple d'un jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Index syntax  
Set_Expression.Item(Index)  
  
String expression syntax  
Set_Expression.Item(String_Expression1 [ ,String_Expression2,...n])  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *String_Expression1*  
 Expression de chaîne valide qui correspond généralement à un tuple exprimé dans une chaîne.  
  
 *String_Expression2*  
 Expression de chaîne valide qui correspond généralement à un tuple exprimé dans une chaîne.  
  
 *Évaluer*  
 Expression numérique valide qui précise le tuple spécifique par position dans le jeu à retourner.  
  
## <a name="remarks"></a>Notes  
 La fonction **Item** retourne un tuple à partir du jeu spécifié. Il existe trois façons d’appeler la fonction **Item** :  
  
-   Si une expression de chaîne unique est spécifiée, la fonction **Item** retourne le tuple spécifié. Par exemple, « ([2005].Q3, [Store05]) ».  
  
-   Si plusieurs expressions de chaîne sont spécifiées, la fonction **Item** retourne le tuple défini par les coordonnées spécifiées. Le nombre de chaînes doit correspondre au nombre d'axes, et chaque chaîne doit identifier une hiérarchie unique. Par exemple, « [2005].Q3 », « [Store05] ».  
  
-   Si un entier est spécifié, la fonction **Item** retourne le tuple qui est dans la position de base zéro spécifiée par *index*.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous retourne ([1996],Sales) :  
  
 `{([1996],Sales), ([1997],Sales), ([1998],Sales)}.Item(0)`  
  
 L'exemple suivant utilise une expression de niveau et retourne la mesure Internet Sales Amount (volume de vente Internet) pour chaque State-Province (état-Province) en Australie ; il dévoile également le pourcentage de volume de vente Internet total pour l'Australie. Cet exemple utilise la fonction Item pour extraire le premier (et seul tuple) du jeu retourné par la fonction **ancêtres** .  
  
```  
WITH MEMBER Measures.x AS [Measures].[Internet Sales Amount] /   
   ( [Measures].[Internet Sales Amount],    
      Ancestors   
      ( [Customer].[Customer Geography].CurrentMember,  
        [Customer].[Customer Geography].[Country]  
      ).Item (0)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{ Descendants   
   ( [Customer].[Customer Geography].[Country].&[Australia],  
     [Customer].[Customer Geography].[State-Province], SELF   
   )   
} ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
