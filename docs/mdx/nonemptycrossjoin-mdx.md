---
title: NonEmptyCrossjoin (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7da56ac658f57d6eb664762f9dd94351df39fe0f
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63456569"
---
# <a name="nonemptycrossjoin-mdx"></a>NonEmptyCrossjoin (MDX)


  Retourne un dataset contenant le produit du croisement d'un ou plusieurs jeux dont sont exclus les tuples vides et les tuples qui ne sont associés à aucune table de faits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
NonEmptyCrossjoin(Set_Expression1 [ ,Set_Expression2,...] [,Count ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Set_Expression1*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Set_Expression2*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Compter*  
 Expression numérique valide qui précise le nombre de jeux à retourner.  
  
## <a name="remarks"></a>Notes  
 Le **NonEmptyCrossjoin** fonction retourne le produit croisé de deux ou plusieurs jeux sous la forme d’un jeu, en excluant les tuples vides ou les tuples dépourvus de données fournies par les tables de faits sous-jacentes. En raison de la façon dont le **NonEmptyCrossjoin** fonction fonctionne, tous les calculés membres sont automatiquement exclus.  
  
 Si *nombre* n’est pas spécifié, la fonction entre tous les jeux spécifiés des jointures et exclut les membres vides du jeu résultant. Si un nombre de jeux est défini, la fonction joint les nombres des jeux spécifiés entre eux en commençant par le premier jeu spécifié. Le **NonEmptyCrossjoin** fonction utilise tous les jeux restants qui sont spécifiées dans les jeux spécifiés suivants mais qui n’ont pas été croisé joint pour déterminer quels membres sont considérés comme non vides dans cross jeu joint obtenu. Le **NonEmptyCrossjoin** fonction respecte la **NON_EMPTY_BEHAVIOR** définition des mesures calculées.  
  
> [!IMPORTANT]  
>  Cette fonction est déconseillée et vous ne devez pas l'utiliser ; elle est conservée uniquement pour maintenir la compatibilité descendante. Au lieu de cela, vous devez utiliser le [Exists (MDX)](../mdx/exists-mdx.md) fonction avec l’argument de nom de groupe de mesures ou la [NonEmpty (MDX)](../mdx/nonempty-mdx.md) (fonction).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
