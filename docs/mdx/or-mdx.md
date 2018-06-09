---
title: OU (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 668e8f1955290c31ee63ca5b81fc5e9c286d54c4
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742448"
---
# <a name="or-mdx"></a>OR (MDX)


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
  
## <a name="return-value"></a>Valeur de retour  
 Valeur booléenne qui retourne **true** si les deux arguments donnent comme résultat **true**; sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 Le **ou** opérateur traite les deux arguments comme des valeurs booléennes (zéro, 0, comme **false**; sinon, **true**) avant que l’opérateur effectue la disjonction logique. Le tableau suivant illustre comment la **ou** opérateur effectue la disjonction logique.  
  
|*Expression1*|*Expression2*|Valeur de retour|  
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
 [Référence des opérateurs MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
