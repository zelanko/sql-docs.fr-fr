---
title: --(Commentaire) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c848277505dde5fabb10247641ee6b7f955d84e0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68006283"
---
# <a name="comment---mdx-operator-reference"></a>Commentaire-référence des opérateurs MDX


  Signale un texte de commentaire inséré par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Paramètres  
 *Comment_Text*  
 Chaîne contenant le texte du commentaire.  
  
## <a name="remarks"></a>Notes  
 Il est possible d'insérer des commentaires sur une ligne distincte, à la fin d'une ligne de script MDX (Multidimensional Expressions), ou à l'intérieur d'une instruction MDX. Le serveur n'évalue pas ces commentaires.  
  
 Utilisez cet opérateur pour un commentaire d'une seule ligne ou imbriqué. Les commentaires insérés à l'aide de -- sont délimités par le caractère de fin de paragraphe.  
  
 Il n'y a pas de longueur maximale pour les commentaires.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
-- This member returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM -- Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commentaire &#40;&#41;MDX](../mdx/comment-mdx.md)   
 [Commentaire&#40;&#41; &#40;&#41;MDX](../mdx/comment-mdx-double-slash.md)   
 [Référence des opérateurs MDX &#40;&#41;MDX](../mdx/mdx-operator-reference-mdx.md)  
  
  
