---
description: LinRegR2 (MDX)
title: LinRegR2 (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 748b332d7925313c5b5d8c1d3dfe868e3eb3e9cd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429821"
---
# <a name="linregr2-mdx"></a>LinRegR2 (MDX)


  Calcule la régression linéaire d’un jeu et retourne le coefficient de détermination, R<sup>2</sup>.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LinRegR2(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression_y*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des ordonnées.  
  
 *Numeric_Expression_x*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des abscisses.  
  
## <a name="remarks"></a>Notes  
 La régression linéaire qui utilise la méthode des moindres carrés calcule l'équation d'une droite de régression (c'est-à-dire de la meilleure ligne pour une série de points). La ligne de régression présente l’équation suivante, où a est la pente et b est l’intersection :  
  
 y = ax+b  
  
 La fonction **LinRegR2** évalue le setagainst spécifié la première expressionto numérique obtient les valeurs de l’axe y. La fonction évalue ensuite le jeu spécifié par rapport à la deuxième expression numérique, si spécifiée, pour extraire les valeurs de l'axe des abscisses. Si la deuxième expression numérique n’est pas spécifiée, la fonction utilise le contexte actuel des cellules dans le jeu spécifié comme valeurs de l’axe des abscisses. Il est fréquent de ne pas spécifier l'argument de l'axe des abscisses avec la dimension Time.  
  
 Une fois l’ensemble de points obtenu, la fonction **LinRegR2** retourne le R<sup>2</sup> statistique qui décrit l’adéquation entre l’équation linéaire et les points.  
  
> [!NOTE]  
>  La fonction **LinRegR2** ignore les cellules vides ou les cellules qui contiennent du texte ou des valeurs logiques. Cependant, elle tient compte des cellules dont la valeur est zéro.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne le R<sup>2</sup> statistique qui décrit l’adéquation entre l’équation de régression linéaire et les points pour les mesures Sales unitaire et sales Store.  
  
```  
LinRegR2(LastPeriods(10), [Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
