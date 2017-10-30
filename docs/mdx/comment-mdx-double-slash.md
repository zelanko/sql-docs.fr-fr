---
title: (Commentaire) (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- //
dev_langs:
- kbMDX
helpviewer_keywords:
- commenting characters
- // (comment)
ms.assetid: 9a3ee822-4689-41a8-9997-8b307850cd68
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ee635641e8d6ee4fb2542d106180d8107c79db28
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="comment-mdx-double-slash"></a>Barre oblique double de commentaire MDX
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Indique un texte défini par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
// Comment_Text   
```  
  
#### <a name="parameters"></a>Paramètres  
 *Comment_Text*  
 Chaîne contenant le texte du commentaire.  
  
## <a name="remarks"></a>Notes  
 Il est possible d'insérer des commentaires sur une ligne distincte, à la fin d'une ligne de script MDX (Multidimensional Expressions), ou à l'intérieur d'une instruction MDX. Le serveur n'évalue pas ces commentaires.  
  
 Utilisez // pour un commentaire d'une seule ligne uniquement. Les commentaires insérés à l'aide de // sont délimités par le caractère de fin de paragraphe.  
  
 Il n'y a pas de longueur maximale pour les commentaires.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
// This member returns the gross profit margin for product types  
// and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM // Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commentaire &#40; MDX &#41;](../mdx/comment-mdx.md)   
 [--&#40; Commentaire &#41; &#40; MDX &#41;](../mdx/comment-mdx-operator-reference.md)   
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  

