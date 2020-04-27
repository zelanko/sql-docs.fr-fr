---
title: LinRegPoint (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3719071beca4dbd8cc991befbb7b2b74f8982c89
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905575"
---
# <a name="linregpoint-mdx"></a>LinRegPoint (MDX)


  Calcule la régression linéaire d’un jeu et retourne la valeur de l' *intersection y* dans la droite de régression, y = ax + b pour une valeur particulière de x.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LinRegPoint(Slice_Expression_x, Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Slice_Expression_x*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe de secteur.  
  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression_y*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des ordonnées.  
  
 *Numeric_Expression_x*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des abscisses.  
  
## <a name="remarks"></a>Notes  
 La régression linéaire qui utilise la méthode des moindres carrés calcule l'équation d'une droite de régression (c'est-à-dire de la meilleure ligne pour une série de points). La ligne de régression présente l’équation suivante, où a est la pente et b est l’intersection :  
  
 y = ax+b  
  
 La fonction **LinRegPoint** évalue le jeu spécifié par rapport à la deuxième expression numérique pour obtenir les valeurs de l’axe y. Elle évalue ensuite le jeu spécifié par rapport à la troisième expression numérique (si cette dernière est précisée) pour extraire les valeurs de l'axe des abscisses. Si la troisième expression numérique n'est pas spécifiée, la fonction utilise le contexte actuel des cellules dans le jeu spécifié en tant que valeurs de l'axe des abscisses. Il est fréquent de ne pas spécifier l'argument de l'axe des abscisses avec la dimension Time.  
  
 Une fois la régression linéaire calculée, la valeur de l'équation est calculée pour la première expression numérique, puis retournée.  
  
> [!NOTE]  
>  La fonction **LinRegPoint** ignore les cellules vides ou les cellules qui contiennent du texte. Cependant, elle tient compte des cellules dont la valeur est zéro.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la valeur prévue de Unit Sales (ventes à l'unité) sur les dix périodes écoulées en se basant sur la relation statistique entre les mesures Unit Sales (ventes par unité) et Store Sales (ventes par magasin).  
  
```  
LinRegPoint([Measures].[Unit Sales],LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
