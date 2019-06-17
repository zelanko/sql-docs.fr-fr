---
title: Ascendants (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3122b3aa2f53da69f88e6ffad508f12c8e10da1c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63249820"
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)


  Retourne le jeu des ascendants du membre spécifié, notamment le membre lui-même.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Le **Ascendants** fonction retourne tous les ancêtres d’un membre à partir du membre lui-même jusqu’en haut de la hiérarchie du membre ; plus précisément, il effectue un balayage post-ordre de la hiérarchie du membre spécifié, puis retourne que tous les membres ascendants associés au membre, y compris lui-même, dans un jeu. Il s’agit Contrairement à la [ancêtre](../mdx/ancestor-mdx.md) (fonction), qui retourne un membre ascendant spécifique, ou ancêtre, à un niveau spécifique.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne le nombre de commandes des revendeurs le `[Sales Territory].[Northwest]` membre et tous les ascendants de ce membre dans le **Adventure Works** cube. Le **Ascendants** fonction construit le jeu qui inclut le `[Sales Territory].[Northwest]` membre et ses ascendants pour l’axe des lignes.  
  
```  
SELECT  
   Measures.[Reseller Order Count] ON COLUMNS,  
   Order(  
      Ascendants(  
         [Sales Territory].[Northwest]  
      ),  
      DESC  
   ) ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
