---
title: Covariance (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COVARIANCE
dev_langs: kbMDX
helpviewer_keywords: Covariance function
ms.assetid: 5faf6742-62db-4c5c-8797-096bf1cab273
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3a00d12c88df72dda0d7c0d929c8e3b99ff77f6e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="covariance-mdx"></a>Covariance (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 Le **Covariance** évalue le jeu spécifié par rapport à la première expression numérique pour extraire les valeurs de l’axe des ordonnées. Elle évalue ensuite le jeu spécifié par rapport à la deuxième expression numérique (si cette dernière est précisée) pour extraire l'ensemble des valeurs de l'axe des abscisses. Si le deuxième expressionis numérique pas spécifié, la fonction utilise le contexte actuel des cellules dans le jeu spécifié en tant que valeurs de l’axe des abscisses.  
  
 Le **Covariance** fonction utilise la formule de remplissage biaisée. Ceci est le contraire de la [CovarianceN](../mdx/covariancen-mdx.md) fonction qui utilise la formule de remplissage non biaisée (en divisant le nombre de paires x-y, puis en soustrayant 1).  
  
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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
