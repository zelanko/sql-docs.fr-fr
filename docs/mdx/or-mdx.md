---
title: OR (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ae6b6602d7968bb444dcf4838537bb000b97dd53
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63278257"
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
 Une valeur booléenne qui retourne **true** si les deux arguments donnent comme résultat **true**; sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 Le **ou** opérateur traite les deux arguments comme valeurs booléennes (zéro, 0, comme **false**; sinon, **true**) avant que l’opérateur effectue la disjonction logique. Le tableau suivant illustre comment la **ou** opérateur effectue la disjonction logique.  
  
|*Expression1*|*Expression2*|Valeur de retour|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="example"></a>Exemple  
 La requête suivante contient une mesure calculée qui retourne la chaîne « MARRIED OR MALE » si le membre actuel sur la hiérarchie Gender de la dimension Customer est Male ou le membre actuel sur la hiérarchie Marital Status de la dimension Customer est Married ; Sinon, elle retourne la chaîne « UNMARRIED ou FEMALE ».  
  
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
  
  
