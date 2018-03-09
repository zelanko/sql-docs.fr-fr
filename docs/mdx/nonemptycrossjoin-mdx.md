---
title: NonEmptyCrossjoin (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: NONEMPTYCROSSJOIN
dev_langs: kbMDX
helpviewer_keywords: NonEmptyCrossjoin function
ms.assetid: 3dc9522d-9126-4f7a-b587-216fa7a06c62
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ffa983a749245022d0815906fe8e17850f9aabdf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="nonemptycrossjoin-mdx"></a>NonEmptyCrossjoin (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
 *Nombre*  
 Expression numérique valide qui précise le nombre de jeux à retourner.  
  
## <a name="remarks"></a>Notes   
 Le **NonEmptyCrossjoin** fonction retourne le produit croisé de deux ou plusieurs jeux sous la forme d’un jeu, en excluant les tuples vides ou des tuples sans les données fournies par les tables de faits sous-jacentes. En raison de la façon dont le **NonEmptyCrossjoin** fonction, tous les calculés membres sont automatiquement exclus.  
  
 Si *nombre* n’est pas spécifié, la fonction cross joint tous les jeux spécifiés et exclut les membres vides du jeu obtenu. Si un nombre de jeux est défini, la fonction joint les nombres des jeux spécifiés entre eux en commençant par le premier jeu spécifié. Le **NonEmptyCrossjoin** fonction utilise tous les jeux restants qui sont spécifiées dans les jeux spécifiés suivants, mais qui n’ont pas été croisé joint pour déterminer quels membres sont considérés comme non vides dans la boîte entre le jeu joint. Le **NonEmptyCrossjoin** fonction respecte la **NON_EMPTY_BEHAVIOR** définition des mesures calculées.  
  
> [!IMPORTANT]  
>  Cette fonction est déconseillée et vous ne devez pas l'utiliser ; elle est conservée uniquement pour maintenir la compatibilité descendante. Au lieu de cela, vous devez utiliser le [Exists (MDX)](../mdx/exists-mdx.md) fonction avec l’argument de nom de groupe de mesures ou la [NonEmpty (MDX)](../mdx/nonempty-mdx.md) (fonction).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
