---
title: Ascendants (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ef9cccb488cebb08c1b9721c40cb8037ea8687a
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739618"
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)


  Retourne le jeu des ascendants du membre spécifié, notamment le membre lui-même.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Le **Ascendants** fonction retourne tous les ancêtres d’un membre du membre lui-même jusqu’au haut de la hiérarchie du membre ; plus spécifiquement, il effectue une traversée post-ordre de la hiérarchie du membre spécifié, et puis retourne tous les membres ascendants associés au membre, notamment lui-même, dans un jeu. Ceci est le contraire de la [ancêtre](../mdx/ancestor-mdx.md) fonction, qui retourne un membre ascendant spécifique, ou ancêtre, à un niveau spécifique.  
  
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
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
