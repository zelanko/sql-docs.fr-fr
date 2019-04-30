---
title: Covariance (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1bb24e4dcb536af144214f96dd5b904cc8530cd4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63249608"
---
# <a name="covariance-mdx"></a>Covariance (MDX)


  Retourne la covariance de remplissage de paires x-y pour les valeurs évaluées sur un jeu à l'aide de la formule de remplissage biaisée (par division du nombre de paires x-y).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Covariance(Set_Expression,Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression_y*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des ordonnées.  
  
 *Numeric_Expression_x*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des abscisses.  
  
## <a name="remarks"></a>Notes  
 Le **Covariance** fonction évalue le jeu spécifié par rapport à la première expression numérique, pour obtenir les valeurs de l’axe y. Elle évalue ensuite le jeu spécifié par rapport à la deuxième expression numérique (si cette dernière est précisée) pour extraire l'ensemble des valeurs de l'axe des abscisses. Si le deuxième expressionis numérique pas spécifié, la fonction utilise le contexte actuel des cellules dans le jeu spécifié en tant que valeurs pour l’axe des abscisses.  
  
 Le **Covariance** fonction utilise la formule de remplissage biaisée. Il s’agit Contrairement à la [CovarianceN](../mdx/covariancen-mdx.md) fonction qui utilise la formule de remplissage non biaisée (en divisant le nombre de paires x-y, puis en soustrayant 1).  
  
> [!NOTE]  
>  Le **Covariance** fonction ignore les cellules vides ou les cellules qui contiennent du texte ou les valeurs logiques sont ignorés. Cependant, elle tient compte des cellules dont la valeur est zéro.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser la fonction Covariance dans :  
  
```  
WITH   
MEMBER [Measures].[CovarianceDemo] AS  
COVARIANCE([Date].[Date].[Date].Members, [Measures].[Internet Sales Amount], [Measures].[Internet Order Count])   
SELECT {[Measures].[CovarianceDemo]} ON 0   
FROM  
[Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
