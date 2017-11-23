---
title: CovarianceN (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COVARIANCEN
dev_langs: kbMDX
helpviewer_keywords: Covariancen function
ms.assetid: 1cc621cd-ffa0-40aa-91f0-bc5cb57f692b
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 1dddff289640ae140f1e4e083487ced339fbd96c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="covariancen-mdx"></a>CovarianceN (MDX)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne l'exemple de covariance de paires x-y pour les valeurs évaluées sur un jeu à l'aide de la formule de remplissage non biaisée (par division du nombre de paires x-y).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CovarianceN(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Numeric_Expression_y*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des ordonnées.  
  
 *Numeric_Expression_x*  
 Expression numérique valide qui correspond généralement à une expression MDX (Multidimensional Expressions) des coordonnées des cellules qui retournent un nombre représentant les valeurs de l'axe des abscisses.  
  
## <a name="remarks"></a>Notes  
 Le **CovarianceN** évalue le jeu spécifié par rapport à la première expression numérique pour extraire les valeurs de l’axe des ordonnées. Elle évalue ensuite le jeu spécifié par rapport à la deuxième expression numérique (si cette dernière est précisée) pour extraire l'ensemble des valeurs de l'axe des abscisses. Si la deuxième expression numérique n’est pas spécifiée, la fonction utilise le contexte actuel des cellules dans le jeu spécifié en tant que valeurs de l’axe des abscisses.  
  
 Le **CovarianceN** fonction utilise la formule de remplissage non biaisée. Ceci est le contraire de la [Covariance](../mdx/covariance-mdx.md) fonction qui utilise la formule de remplissage biaisée (division par le nombre de paires x-y).  
  
> [!NOTE]  
>  Le **CovarianceN** fonction ignore les cellules vides ou les cellules qui contiennent du texte ou des valeurs logiques. Cependant, elle tient compte des cellules dont la valeur est zéro.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
