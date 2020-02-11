---
title: Commentaire (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f0aa1455ffd9f52fd917f68d2bb0bb80e3f25a94
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68006274"
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
 Le serveur n’évalue pas le texte entre les caractères de commentaire,/ \** et/. Il est possible d'insérer des commentaires sur une ligne distincte ou à l'intérieur d'une instruction MDX. Les commentaires sur plusieurs lignes doivent être indiqués par\* / \*et/.  
  
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
 [Commentaire&#40;&#41; &#40;&#41;MDX](../mdx/comment-mdx-double-slash.md)   
 [--&#40;comment&#41; &#40;&#41;MDX](../mdx/comment-mdx-operator-reference.md)   
 [Référence des opérateurs MDX &#40;&#41;MDX](../mdx/mdx-operator-reference-mdx.md)  
  
  
