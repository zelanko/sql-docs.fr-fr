---
title: Sous-ensemble (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: subset
dev_langs: kbMDX
helpviewer_keywords: Subset function
ms.assetid: 49a7cd28-cd6f-4ae7-8c91-94a8652a97a5
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 86014760cec4a433b43c93e8e2186b8018cf49da
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="subset-mdx"></a>Subset (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne un sous-ensemble de tuples d'un jeu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Subset(Set_Expression, Start [ ,Count ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Démarrer*  
 Expression numérique valide qui précise la position du premier tuple à retourner.  
  
 *Nombre*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
## <a name="remarks"></a>Notes  
 Dans le jeu spécifié, le **sous-ensemble** fonction retourne un sous-ensemble qui contient le nombre spécifié de tuples, en commençant à la position de début spécifiée. La position de départ est fondée sur un index de base zéro : zéro (0) correspond au premier tuple dans le jeu spécifié, 1 correspond au deuxième, et ainsi de suite.  
  
 Si *nombre* n’est pas spécifié, la fonction retourne tous les tuples à partir de *Démarrer* à la fin de l’ensemble.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la mesure Reseller Sales pour les cinq premières sous-catégories de vente de produits, quelle que soit la hiérarchie et conformément à la mesure Reseller Gross Profit (marge brute du revendeur). Le **sous-ensemble** fonction est utilisée pour retourner uniquement les cinq premiers jeux dans le résultat, une fois que le résultat est trié à l’aide de la **ordre** (fonction).  
  
```  
SELECT Subset  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BDESC  
      )  
   ,0  
   ,5  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
