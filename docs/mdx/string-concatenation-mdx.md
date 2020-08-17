---
description: + (Concaténation de chaînes) MDX
title: + (Concaténation de chaînes) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e92751cb709a93d3d5d8d05ac76361c22bee5fa7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88386865"
---
# <a name="-string-concatenation-mdx"></a>+ (Concaténation de chaînes) (MDX)


  Exécute une opération de chaîne qui concatène deux ou plusieurs chaînes de caractères, tuples, ou une combinaison de chaînes et de tuples.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
String_Expression + String_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *String_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une valeur de chaîne.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur dont le type de données du paramètre possède la priorité la plus élevée.  
  
## <a name="remarks"></a>Notes  
 Les deux expressions doivent être de même type de données, ou l'une des expressions doit pouvoir être implicitement convertie dans le type de données de l'autre expression. Si une expression s'évalue à NULL, l'opérateur retourne le résultat de l'autre expression.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;&#41;MDX ](../mdx/mdx-operator-reference-mdx.md)  
  
  
