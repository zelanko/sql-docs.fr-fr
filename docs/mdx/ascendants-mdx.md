---
title: Ascendants (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ASCENDANTS
dev_langs:
- kbMDX
helpviewer_keywords:
- Ascendants function
ms.assetid: a2baf4a2-7d66-4766-b708-739a3c21b09e
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 7eb0bff443065cff7a279320d85d848ae303f5dd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
