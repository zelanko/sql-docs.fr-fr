---
description: Opérateurs de jeu
title: Opérateurs de jeu | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eb4434c9fe1991e1398baaa9c7bfd9602995652d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341235"
---
# <a name="set-operators"></a>Opérateurs de jeu


  Dans la syntaxe MDX (Multidimensional Expressions), les opérateurs de jeu exécutent des opérations sur des membres ou des jeux et retournent un jeu. Ils sont généralement utilisés comme alternative à plusieurs fonctions de jeu dans les expressions MDX.  
  
 MDX prend en charge les opérateurs de jeu répertoriés dans le tableau suivant.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[- (Sauf)](../mdx/except-mdx-operator.md)|Retourne les différences entre deux jeux, en supprimant les membres en double.<br /><br /> Cet opérateur est fonctionnellement équivalent à la fonction [except](../mdx/except-mdx-function.md) .|  
|[* (Jointure croisée)](../mdx/crossjoin-mdx-operator-reference.md)|Renvoie le produit croisé de deux jeux de données<br /><br /> Cet opérateur est fonctionnellement équivalent à la fonction [CrossJoin](../mdx/crossjoin-mdx.md) .|  
|[: (Plage)](../mdx/range-mdx.md)|Retourne un jeu naturellement ordonné, dont les extrémités sont représentées par les deux membres spécifiés, entre lesquels figurent les autres membres du jeu.|  
|[+ (Union)](../mdx/union-mdx-operator-reference.md)|Retourne l'union de deux jeux, en excluant les membres en double.<br /><br /> Cet opérateur est fonctionnellement équivalent à la fonction d' [&#41;MDX &#40;](../mdx/union-mdx.md) .|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX ](../mdx/mdx-function-reference-mdx.md)   
 [Référence des opérateurs MDX &#40;&#41;MDX ](../mdx/mdx-operator-reference-mdx.md)   
 [Opérateurs &#40;syntaxe MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
