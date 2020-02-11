---
title: Sous-ensemble (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b1f9a79c0e0ba6d578b82d7b1d072f3543888a1c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036704"
---
# <a name="subset-mdx"></a>Subset (MDX)


  Retourne un sous-ensemble de tuples d'un jeu spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Subset(Set_Expression, Start [ ,Count ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Start*  
 Expression numérique valide qui précise la position du premier tuple à retourner.  
  
 *Saut*  
 Expression numérique valide qui précise le nombre de tuples à retourner.  
  
## <a name="remarks"></a>Notes  
 À partir du jeu spécifié, la fonction de **sous-ensemble** retourne un sous-ensemble qui contient le nombre spécifié de tuples, en commençant à la position de début spécifiée. La position de départ est fondée sur un index de base zéro : zéro (0) correspond au premier tuple dans le jeu spécifié, 1 correspond au deuxième, et ainsi de suite.  
  
 Si *Count* n’est pas spécifié, la fonction retourne tous les tuples de *début* à la fin de l’ensemble.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne la mesure Reseller Sales pour les cinq premières sous-catégories de vente de produits, quelle que soit la hiérarchie et conformément à la mesure Reseller Gross Profit (marge brute du revendeur). La fonction de **sous-ensemble** est utilisée pour retourner uniquement les cinq premiers jeux dans le résultat une fois que le résultat est ordonné à l’aide de la fonction **Order** .  
  
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
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
