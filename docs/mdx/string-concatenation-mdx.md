---
title: "+ (Concaténation de chaînes) (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +
dev_langs: kbMDX
helpviewer_keywords:
- string concatenation operators
- + (string concatenation)
ms.assetid: d77636b1-2973-4587-af35-54aba5700d9a
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 026618d4a71e2e3c85df12c1994c4c0b6ffd30f7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="-string-concatenation-mdx"></a>+ (Concaténation de chaînes) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Exécute une opération de chaîne qui concatène deux ou plusieurs chaînes de caractères, tuples, ou une combinaison de chaînes et de tuples.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
String_Expression + String_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *String_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une valeur de chaîne.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur dont le type de données du paramètre possède la priorité la plus élevée.  
  
## <a name="remarks"></a>Notes  
 Les deux expressions doivent être de même type de données, ou l'une des expressions doit pouvoir être implicitement convertie dans le type de données de l'autre expression. Si une expression s'évalue à NULL, l'opérateur retourne le résultat de l'autre expression.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
