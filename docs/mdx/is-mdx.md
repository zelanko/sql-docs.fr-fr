---
title: EST (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS
dev_langs:
- kbMDX
helpviewer_keywords:
- IS operator
ms.assetid: dc8c0b91-3bb1-49e5-8d70-57545baaa8e0
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 97183b67350b6d3db613bb8bc8e957642bf5bb76
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="is-mdx"></a>IS (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Effectue une comparaison logique sur deux expressions d'objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Expression1 IS ( Expression2 | NULL )  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Expression1*  
 Expression MDX (Multidimensional Expressions) valide retournant une référence à un objet MDX.  
  
 *Expression2*  
 Expression MDX valide retournant une référence à un objet MDX.  
  
## <a name="return-value"></a>Valeur retournée  
 Valeur booléenne qui retourne **true** si les deux arguments font référence au même objet ; sinon, **false**. Si le **NULL** mot clé est spécifié, l’opérateur retourne **true** si *Expression1* est **null**; sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 Le **IS** opérateur est souvent utilisée pour déterminer si tuples et membres sont idempotents, ce qui signifie qu’ils sont tout à fait équivalents.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre comment utiliser le **IS** opérateur afin de vérifier si le membre actuel sur un axe est un membre spécifique :  
  
 `With`  
  
 `//Returns TRUE if the currentmember is Bikes`  
  
 `Member [Measures].[IsBikes?] AS`  
  
 `[Product].[Category].CurrentMember IS [Product].[Category].&[1]`  
  
 `SELECT`  
  
 `{[Measures].[IsBikes?]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des opérateurs MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  

