---
description: Correlation (MDX)
title: Corrélation (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ae050b681830b81ffa63ae82c714d69d54b03c91
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387645"
---
# <a name="correlation-mdx"></a>Correlation (MDX)


  Retourne le coefficient de corrélation des paires x-y des valeurs évaluées sur un jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Correlation( Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression_y*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des ordonnées.  
  
 *Numeric_Expression_x*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des abscisses.  
  
## <a name="remarks"></a>Notes  
 La fonction de **corrélation** calcule le coefficient de corrélation de deux paires de valeurs en évaluant tout d’abord le jeu spécifié par rapport à la première expression numérique pour obtenir les valeurs de l’axe y. Elle évalue ensuite le jeu spécifié par rapport à la deuxième expression numérique (si cette dernière est présente) pour extraire l'ensemble des valeurs de l'axe des abscisses. Si la deuxième expression numérique n'est pas spécifiée, la fonction utilise le contexte actuel des cellules dans le jeu spécifié en tant que valeurs de l'axe des abscisses.  
  
> [!NOTE]  
>  La fonction de **corrélation** ignore les cellules vides ou les cellules qui contiennent du texte ou des valeurs logiques. Cependant, elle tient compte des cellules dont la valeur est zéro.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
