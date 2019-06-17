---
title: Comment (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6469921572b8a1809e228fff0d25061475399ae7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181572"
---
# <a name="comment-mdx"></a>Commentaire (MDX)


  Signale un texte de commentaire inséré par l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
/* Comment_Text */      
```  
  
#### <a name="parameters"></a>Paramètres  
 *Comment_Text*  
 Chaîne contenant le texte du commentaire.  
  
## <a name="remarks"></a>Notes  
 Le serveur n’évalue pas le texte entre les caractères de commentaire / * et \*/. Il est possible d'insérer des commentaires sur une ligne distincte ou à l'intérieur d'une instruction MDX. Commentaires de plusieurs lignes doivent être signalés par /\* et \*/.  
  
 Il n'y a pas de longueur maximale pour les commentaires. Les commentaires peuvent être imbriqués ; par exemple, `/* Test /*Comment*/ Text*/` est un commentaire imbriqué.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous illustre l'utilisation de cet opérateur.  
  
```  
/* This member returns the gross profit margin for product types  
  and reseller types crossjoined by year. */  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM /* Select from the Adventure Works cube. */  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [&#40;Comment&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md)   
 [-- &#40;Comment&#41; &#40;MDX&#41;](../mdx/comment-mdx-operator-reference.md)   
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
