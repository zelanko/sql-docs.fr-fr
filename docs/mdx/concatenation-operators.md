---
title: Opérateurs de concaténation | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- concatenation operators [MDX]
ms.assetid: 9e4c181a-b71e-41ec-98a1-ec8b5b5103b1
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 576d134e935189fa83f60d3a3200d13cad47e9d5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="concatenation-operators"></a>Opérateurs de concaténation
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  L'opérateur de concaténation est le signe plus (+). Vous pouvez combiner, ou concaténer, deux ou plusieurs chaînes de caractères en une seule. Vous pouvez également concaténer des chaînes binaires.  
  
 Le code suivant est un exemple d'opérateur de concaténation combinant le nom du produit et son nom unique :  
  
```  
WITH MEMBER Measures.ProductName AS   
   Product.Product.CurrentMember.Name + " (" + Product.Product.CurrentMember.UniqueName + ")"  
SELECT   
   {Measures.ProductName} ON COLUMNS,  
   Product.Product.Members ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="language-considerations"></a>Observations relatives au langage  
 Lorsque les chaînes utilisées dans une concaténation possèdent toutes deux le même classement, la chaîne concaténée obtenue possède un classement identique aux entrées. Lorsque les chaînes utilisées dans une concaténation possèdent des classements différents, les règles de priorité de classement déterminent celui de la chaîne concaténée obtenue. Pour plus d’informations, consultez [Langues et classements &#40;Analysis Services&#41;](../analysis-services/languages-and-collations-analysis-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Opérateurs &#40;syntaxe MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
