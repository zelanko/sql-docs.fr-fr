---
title: '* Multiplier (MDX) | Microsoft Docs'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 396dded86adfe8faa6b6ad58b5eb8174d4323726
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088426"
---
# <a name="-multiply-mdx"></a>* (Multiply) (MDX)


  Exécute une opération arithmétique qui multiplie deux nombres.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Numeric_Expression * Numeric_Expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Numeric_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur dont le type de données du paramètre possède la priorité la plus élevée.  
  
## <a name="remarks"></a>Notes  
 Les deux expressions doivent être de même type de données, ou l'une des expressions doit pouvoir être implicitement convertie dans le type de données de l'autre expression. Si une expression donne comme résultat une valeur NULL, l'opérateur retourne une valeur NULL.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;&#41;MDX](../mdx/mdx-operator-reference-mdx.md)  
  
  
