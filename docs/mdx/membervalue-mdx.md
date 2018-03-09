---
title: MemberValue (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: MEMBERVALUE
dev_langs: kbMDX
helpviewer_keywords: MemberValue function
ms.assetid: f9b2af16-2b81-48e4-ae81-99f64e4bbc98
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 615b49f12079b8cf47045e3c56635e17fcdae691
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="membervalue-mdx"></a>MemberValue (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne la valeur d'un membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.MemberValue  
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui prend la valeur d'un membre.  
  
## <a name="return-value"></a>Valeur retournée  
 La valeur de membre retournée contient les informations suivantes, répertoriées ci-dessous selon leur ordre d'apparition dans cette valeur :  
  
-   La liaison de la valeur, si elle a été définie.  
  
-   La clé avec le type de données d'origine, s'il n'y a aucune liaison de nom ou si la clé et la légende sont liées à la même colonne.  
  
-   La légende du membre.  
  
## <a name="example"></a> Exemple  
 L'exemple ci-après retourne la liaison de la valeur, la clé de membre et la légende de la première date dans la dimension Date du cube Adventure Works.  
  
```  
WITH MEMBER Measures.ValueColumn as [Date].[Calendar].[July 1, 2001].MemberValue  
MEMBER Measures.KeyColumn as [Date].[Calendar].[July 1, 2001].Member_Key  
MEMBER Measures.NameColumn as [Date].[Calendar].[July 1, 2001].Member_Name  
  
SELECT {Measures.ValueColumn, Measures.KeyColumn, Measures.NameColumn}  ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
