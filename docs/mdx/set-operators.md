---
title: Opérateurs de jeu | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: df58b5c7f6da05700f00b4ec5fd46b81926dd3bb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63150171"
---
# <a name="set-operators"></a>Opérateurs de jeu


  Dans la syntaxe MDX (Multidimensional Expressions), les opérateurs de jeu exécutent des opérations sur des membres ou des jeux et retournent un jeu. Ils sont généralement utilisés comme alternative à plusieurs fonctions de jeu dans les expressions MDX.  
  
 MDX prend en charge les opérateurs de jeu répertoriés dans le tableau suivant.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[- (Sauf)](../mdx/except-mdx-operator.md)|Retourne les différences entre deux jeux, en supprimant les membres en double.<br /><br /> Cet opérateur est fonctionnellement équivalent à la [sauf](../mdx/except-mdx-function.md) (fonction).|  
|[* (Jointure croisée)](../mdx/crossjoin-mdx-operator-reference.md)|Renvoie le produit croisé de deux jeux de données<br /><br /> Cet opérateur est fonctionnellement équivalent à la [Crossjoin](../mdx/crossjoin-mdx.md) (fonction).|  
|[: (Plage)](../mdx/range-mdx.md)|Retourne un jeu naturellement ordonné, dont les extrémités sont représentées par les deux membres spécifiés, entre lesquels figurent les autres membres du jeu.|  
|[+ (Union)](../mdx/union-mdx-operator-reference.md)|Retourne l'union de deux jeux, en excluant les membres en double.<br /><br /> Cet opérateur est fonctionnellement équivalent à la [Union &#40;MDX&#41; ](../mdx/union-mdx.md) (fonction).|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Opérateurs &#40;syntaxe MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
