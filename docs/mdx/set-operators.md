---
title: "Opérateurs de jeu | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: set operators [MDX]
ms.assetid: 83500d2e-44b3-49eb-a221-3ce5a58277a5
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d28688a172a3bf28241c2b69f6aee7a8debca380
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="set-operators"></a>Opérateurs de jeu
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Dans la syntaxe MDX (Multidimensional Expressions), les opérateurs de jeu exécutent des opérations sur des membres ou des jeux et retournent un jeu. Ils sont généralement utilisés comme alternative à plusieurs fonctions de jeu dans les expressions MDX.  
  
 MDX prend en charge les opérateurs de jeu répertoriés dans le tableau suivant.  
  
|Opérateur| Description|  
|--------------|-----------------|  
|[- (Sauf)](../mdx/except-mdx-operator.md)|Retourne les différences entre deux jeux, en supprimant les membres en double.<br /><br /> Cet opérateur est fonctionnellement équivalent à la [sauf](../mdx/except-mdx-function.md) (fonction).|  
|[* (Jointure croisée)](../mdx/crossjoin-mdx-operator-reference.md)|Renvoie le produit croisé de deux jeux de données<br /><br /> Cet opérateur est fonctionnellement équivalent à la [Crossjoin](../mdx/crossjoin-mdx.md) (fonction).|  
|[: (Plage)](../mdx/range-mdx.md)|Retourne un jeu naturellement ordonné, dont les extrémités sont représentées par les deux membres spécifiés, entre lesquels figurent les autres membres du jeu.|  
|[+ (Union)](../mdx/union-mdx-operator-reference.md)|Retourne l'union de deux jeux, en excluant les membres en double.<br /><br /> Cet opérateur est fonctionnellement équivalent à la [Union &#40; MDX &#41; ](../mdx/union-mdx.md) (fonction).|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Opérateurs &#40; La syntaxe MDX &#41;](../mdx/operators-mdx-syntax.md)  
  
  
