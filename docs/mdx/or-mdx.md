---
title: OU (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 45063e9f2aca6a924289d4d52434535d16c9a08e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68055712"
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
 Valeur booléenne qui retourne **true** si l’un ou l’autre ou les deux arguments ont la valeur **true**; Sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 L’opérateur **ou** traite les deux arguments comme des valeurs booléennes (zéro, 0, **false**; sinon, **true**) avant que l’opérateur effectue la disjonction logique. Le tableau suivant illustre la façon dont l’opérateur **ou** effectue la disjonction logique.  
  
|*Expression1*|*Expression2*|Valeur de retour|  
|-------------------|-------------------|------------------|  
|**:**|**:**|**:**|  
|**:**|**fausses**|**:**|  
|**fausses**|**:**|**:**|  
|**fausses**|**fausses**|**fausses**|  
  
## <a name="example"></a>Exemple  
 La requête suivante contient une mesure calculée qui retourne la chaîne « marié ou mâle » si le membre actuel dans la hiérarchie de sexe de la dimension Customer est mâle ou si le membre actuel dans la hiérarchie d’état matrimoniale de la dimension Customer est marié ; Sinon, elle retourne la chaîne « célibataire ou féminin ».  
  
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
 [Référence des opérateurs MDX &#40;&#41;MDX](../mdx/mdx-operator-reference-mdx.md)  
  
  
