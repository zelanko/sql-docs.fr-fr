---
title: IF, instruction (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 41bd34fbd3d296f4aa38877e6d26e25eba9ae726
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138691"
---
# <a name="mdx-scripting---if"></a>Écriture de scripts MDX - IF


  Exécute une instruction si la condition est vérifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IF expression THEN assignment END IF  
```  
  
## <a name="arguments"></a>Arguments  
 *formule*  
 Expression MDX (Multidimensional Expressions) dont l'évaluation aboutit à une valeur booléenne retournant la valeur True ou False.  
  
 *assigné*  
 Expression MDX assignant une valeur à un sous-cube ou à une propriété calculée.  
  
## <a name="remarks"></a>Notes  
 Utilisez l’instruction IF pour le contrôle Flow, contrairement à la fonction [IIf &#40;&#41;MDX](../mdx/iif-mdx.md) et l' [instruction CASE &#40;la&#41;MDX](../mdx/case-statement-mdx.md) qui ne peut être utilisée que pour retourner des valeurs ou des objets.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, la portée est limitée au niveau Pays de la hiérarchie Customers Geography dans la dimension Customers. Si la mesure actuelle est Montant des ventes sur Internet, ce montant est défini sur 10 :  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
