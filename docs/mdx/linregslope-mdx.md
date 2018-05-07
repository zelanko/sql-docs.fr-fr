---
title: LinRegSlope (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LINREGSLOPE
dev_langs:
- kbMDX
helpviewer_keywords:
- LinRegSlope function
ms.assetid: dc61f941-b25d-4eef-9b25-75e03a1dd6de
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f561a1589a59a28ffabe541d67366b08c0c215db
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="linregslope-mdx"></a>LinRegSlope (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Calcule la régression linéaire d’un jeu et retourne la valeur de la pente dans la ligne de régression y = ax + b.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LinRegSlope(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression_y*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des ordonnées.  
  
 *Numeric_Expression_x*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des abscisses.  
  
## <a name="remarks"></a>Notes  
 La régression linéaire qui utilise la méthode des moindres carrés calcule l'équation d'une droite de régression (c'est-à-dire de la meilleure ligne pour une série de points). La ligne de régression a l’équation suivante, où un est de la pente et b l’ordonnée à l’origine :  
  
 y = ax+b  
  
 Le **LinRegSlope** évalue le jeu spécifié par rapport à la première expression numérique pour obtenir les valeurs de l’axe des ordonnées. Elle évalue ensuite l'expression de jeu spécifié par rapport à la deuxième expression numérique (si cette dernière est précisée) pour extraire les valeurs de l'axe des abscisses. Si la deuxième expression numérique n'est pas spécifiée, la fonction utilise le contexte actuel des cellules dans le jeu spécifié en tant que valeurs de l'axe des abscisses. Il est fréquent de ne pas spécifier l'argument de l'axe des abscisses avec la dimension Time.  
  
 Après avoir obtenu l’ensemble de points, le **LinRegSlope** fonction retourne la pente de la ligne de régression (un dans l’équation ci-dessus).  
  
> [!NOTE]  
>  Le **LinRegSlope** fonction ignore les cellules vides ou les cellules qui contiennent du texte ou des valeurs logiques. Cependant, elle tient compte des cellules dont la valeur est zéro.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la pente d'une droite de régression pour les mesures des ventes par unité et par magasin.  
  
```  
LinRegSlope(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
