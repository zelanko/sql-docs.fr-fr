---
description: IF, instruction (MDX)
title: IF, instruction (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 62b5a2e7d2ae04b7cd11bb08a3a65ddad903b6cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429731"
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
  
 *assigné*  
 Expression MDX assignant une valeur à un sous-cube ou à une propriété calculée.  
  
## <a name="remarks"></a>Notes  
 Utilisez l’instruction IF pour le contrôle Flow, contrairement à la fonction [IIf &#40;&#41;MDX ](../mdx/iif-mdx.md) et l' [instruction CASE &#40;la&#41;MDX ](../mdx/case-statement-mdx.md) qui ne peut être utilisée que pour retourner des valeurs ou des objets.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, la portée est limitée au niveau Pays de la hiérarchie Customers Geography dans la dimension Customers. Si la mesure actuelle est Montant des ventes sur Internet, ce montant est défini sur 10 :  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
