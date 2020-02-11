---
title: CovarianceN (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 796dc37127eba984477aef628e4ae9161db4637e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68047181"
---
# <a name="covariancen-mdx"></a>CovarianceN (MDX)


  Retourne l'exemple de covariance de paires x-y pour les valeurs évaluées sur un jeu à l'aide de la formule de remplissage non biaisée (par division du nombre de paires x-y).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CovarianceN(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression_y*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des ordonnées.  
  
 *Numeric_Expression_x*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des abscisses.  
  
## <a name="remarks"></a>Notes  
 La fonction **CovarianceN** évalue le jeu spécifié par rapport à la première expression numérique, pour obtenir les valeurs de l’axe y. Elle évalue ensuite le jeu spécifié par rapport à la deuxième expression numérique (si cette dernière est précisée) pour extraire l'ensemble des valeurs de l'axe des abscisses. Si la deuxième expression numérique n’est pas spécifiée, la fonction utilise le contexte actuel des cellules dans le jeu spécifié comme valeurs pour l’axe des x.  
  
 La fonction **CovarianceN** utilise la formule de remplissage non biaisée. Cela diffère de la fonction de [covariance](../mdx/covariance-mdx.md) qui utilise la formule de remplissage biaisée (en divisant le nombre de paires x-y).  
  
> [!NOTE]  
>  La fonction **CovarianceN** ignore les cellules vides ou les cellules qui contiennent du texte ou des valeurs logiques. Cependant, elle tient compte des cellules dont la valeur est zéro.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
