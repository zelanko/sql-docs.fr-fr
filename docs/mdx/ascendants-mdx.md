---
title: Ascendants (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ASCENDANTS
dev_langs: kbMDX
helpviewer_keywords: Ascendants function
ms.assetid: a2baf4a2-7d66-4766-b708-739a3c21b09e
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2b81f8dffc10d5fa62c264814d3f1215c7f44c5a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
