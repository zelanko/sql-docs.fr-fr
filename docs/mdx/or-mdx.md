---
title: OU (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: OR
dev_langs: kbMDX
helpviewer_keywords: OR operator
ms.assetid: 7634c08a-5b70-44cd-9422-6555fed6ae05
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 7cddabea47afb791fd4ec9f111d81248edc4c2f8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="or-mdx"></a>OR (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Effectue une disjonction logique sur deux expressions numériques.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Expression1 OR Expression2   
```  
  
#### <a name="parameters"></a>Paramètres  
 Expression1  
 Expression MDX (Multidimensional Expressions) valide qui retourne une valeur numérique.  
  
 Expression2  
 Expression MDX valide qui retourne une valeur numérique.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur booléenne qui retourne **true** si les deux arguments donnent comme résultat **true**; sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 Le **ou** opérateur traite les deux arguments comme des valeurs booléennes (zéro, 0, comme **false**; sinon, **true**) avant que l’opérateur effectue la disjonction logique. Le tableau suivant illustre comment la **ou** opérateur effectue la disjonction logique.  
  
|*Expression1*|*Expression2*|Valeur retournée|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="example"></a>Exemple  
 La requête suivante contient une mesure calculée qui retourne la chaîne « MARRIED OR MALE » si le membre actuel sur la hiérarchie Gender de la dimension Client est Male ou le membre actuel sur la hiérarchie Marital Status de la dimension Client est Married ; sinon, elle retourne la chaîne « UNMARRIED OR FEMALE ».  
  
```  
WITH  
MEMBER MEASURES.ORDEMO AS  
IIF(  
([Customer].[Gender].CURRENTMEMBER IS [Customer].[Gender].&[M])  
OR  
([Customer].[Marital Status].CURRENTMEMBER IS [Customer].[Marital Status].&[M]),  
"MARRIED OR MALE",  
"UNMARRIED OR FEMALE")  
SELECT [Customer].[Gender].[Gender].MEMBERS ON 0,  
[Customer].[Marital Status].[Marital Status].MEMBERS ON 1  
FROM [Adventure Works]  
WHERE(MEASURES.ORDEMO)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
