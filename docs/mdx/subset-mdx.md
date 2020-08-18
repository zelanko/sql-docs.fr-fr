---
description: Subset (MDX)
title: Sous-ensemble (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d0b7e79ebf0415011665ae63e7b9699200e374b1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386725"
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
  
 *Count*  
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
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
