---
title: IF instruction (MDX Multidimensional) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4975c455b942f053287b344a956a0083c8ca4e1a
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741658"
---
# <a name="mdx-scripting---if"></a>Écriture de scripts MDX - IF


  Exécute une instruction si la condition est vérifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IF expression THEN assignment END IF  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Expression MDX (Multidimensional Expressions) dont l'évaluation aboutit à une valeur booléenne retournant la valeur True ou False.  
  
 *Affectation*  
 Expression MDX assignant une valeur à un sous-cube ou à une propriété calculée.  
  
## <a name="remarks"></a>Notes  
 Utilisez l’instruction IF pour les flux de contrôle, contrairement à la [IIf &#40;MDX&#41; ](../mdx/iif-mdx.md) (fonction) et le [instruction CASE &#40;MDX&#41; ](../mdx/case-statement-mdx.md) qui peut uniquement être utilisé pour retourner des valeurs ou des objets.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, la portée est limitée au niveau Pays de la hiérarchie Customers Geography dans la dimension Customers. Si la mesure actuelle est Montant des ventes sur Internet, ce montant est défini sur 10 :  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
