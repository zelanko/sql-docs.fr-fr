---
title: "Corrélation (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CORRELATION
dev_langs:
- kbMDX
helpviewer_keywords:
- Correlation function
ms.assetid: 9b3662c9-95a1-4644-b952-9460fe0cf160
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 00f2e3380c1706805e111edbc24423ae49e3ab97
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="correlation-mdx"></a>Correlation (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le coefficient de corrélation des paires x-y des valeurs évaluées sur un jeu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Correlation( Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression_y*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des ordonnées.  
  
 *Numeric_Expression_x*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des abscisses.  
  
## <a name="remarks"></a>Notes  
 Le **corrélation** fonction calcule le coefficient de corrélation de deux paires de valeurs en évaluant d’abord le jeu spécifié par rapport à la première expression numérique pour obtenir les valeurs de l’axe des ordonnées. Elle évalue ensuite le jeu spécifié par rapport à la deuxième expression numérique (si cette dernière est présente) pour extraire l'ensemble des valeurs de l'axe des abscisses. Si la deuxième expression numérique n'est pas spécifiée, la fonction utilise le contexte actuel des cellules dans le jeu spécifié en tant que valeurs de l'axe des abscisses.  
  
> [!NOTE]  
>  Le **corrélation** fonction ignore les cellules vides ou les cellules qui contiennent du texte ou des valeurs logiques. Cependant, elle tient compte des cellules dont la valeur est zéro.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

