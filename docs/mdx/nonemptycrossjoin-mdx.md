---
description: NonEmptyCrossjoin (MDX)
title: NonEmptyCrossjoin (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6fafaad2f6fa0f46d826bf94b26ceb6fdbe9df55
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471801"
---
# <a name="nonemptycrossjoin-mdx"></a>NonEmptyCrossjoin (MDX)


  Retourne un dataset contenant le produit du croisement d'un ou plusieurs jeux dont sont exclus les tuples vides et les tuples qui ne sont associés à aucune table de faits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
NonEmptyCrossjoin(Set_Expression1 [ ,Set_Expression2,...] [,Count ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Count*  
 Expression numérique valide qui précise le nombre de jeux à retourner.  
  
## <a name="remarks"></a>Notes  
 La fonction **NonEmptyCrossjoin** retourne le produit croisé de deux jeux ou plus sous la forme d’un jeu, en excluant les tuples vides ou les tuples sans données fournies par les tables de faits sous-jacentes. En raison du fonctionnement de la fonction **NonEmptyCrossjoin** , tous les membres calculés sont automatiquement exclus.  
  
 Si *Count* n’est pas spécifié, la fonction joint tous les jeux spécifiés et exclut les membres vides du jeu résultant. Si un nombre de jeux est défini, la fonction joint les nombres des jeux spécifiés entre eux en commençant par le premier jeu spécifié. La fonction **NonEmptyCrossjoin** utilise tous les jeux restants qui sont spécifiés dans les jeux spécifiés suivants, mais qui n’ont pas été joints entre eux pour déterminer quels membres sont considérés comme non vides dans le jeu de jointures croisées résultant. La fonction **NonEmptyCrossjoin** respecte le paramètre **NON_EMPTY_BEHAVIOR** des mesures calculées.  
  
> [!IMPORTANT]  
>  Cette fonction est déconseillée et vous ne devez pas l'utiliser ; elle est conservée uniquement pour maintenir la compatibilité descendante. Au lieu de cela, vous devez utiliser la fonction [Exists (MDX)](../mdx/exists-mdx.md) avec l’argument Nom du groupe de mesures ou la fonction non [vide (MDX)](../mdx/nonempty-mdx.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
