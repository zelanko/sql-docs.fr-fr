---
title: '* (Multiplication) (MDX) | Documents Microsoft'
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '*'
dev_langs: kbMDX
helpviewer_keywords:
- '* (multiply operator)'
- multiply operator (*)
ms.assetid: 073fd098-65bd-4a30-81dd-d233d007490d
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b72207a9574b83c234d9f70a76b168be49bee66f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="-multiply-mdx"></a>* (Multiply) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Exécute une opération arithmétique qui multiplie deux nombres.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Numeric_Expression * Numeric_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Numeric_expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur dont le type de données du paramètre possède la priorité la plus élevée.  
  
## <a name="remarks"></a>Notes  
 Les deux expressions doivent être de même type de données, ou l'une des expressions doit pouvoir être implicitement convertie dans le type de données de l'autre expression. Si une expression donne comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
