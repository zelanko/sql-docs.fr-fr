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
ms.openlocfilehash: 16c6f812d1d7cae5a81a8e64fb425f4d33f4cb5c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68017059"
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
 La fonction **ascenders** retourne tous les ancêtres d’un membre du membre lui-même jusqu’au sommet de la hiérarchie du membre ; plus spécifiquement, il effectue une traversée postérieure de l’ordre de la hiérarchie pour le membre spécifié, puis retourne tous les membres ascendants associés au membre, y compris lui-même, dans un ensemble. Cela diffère de la fonction [Ancestor](../mdx/ancestor-mdx.md) , qui retourne un membre ascendants spécifique, ou ancêtre, à un niveau spécifique.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne le nombre de commandes du revendeur pour le `[Sales Territory].[Northwest]` membre et tous les ascendants de ce membre à partir du cube **Adventure Works** . La fonction **ascenders** construit le jeu qui comprend le `[Sales Territory].[Northwest]` membre et ses ascendants pour l’axe Rows.  
  
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
  
  
