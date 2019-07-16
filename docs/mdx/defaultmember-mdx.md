---
title: DefaultMember (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c5843ec42cf4ba712a2e55c9cc96dd6f482c0760
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68047094"
---
# <a name="defaultmember-mdx"></a>DefaultMember (MDX)


  Retourne le membre par défaut d'une hiérarchie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Hierarchy_Expression.DefaultMember  
```  
  
## <a name="arguments"></a>Arguments  
 *Hierarchy_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne une hiérarchie.  
  
## <a name="remarks"></a>Notes  
 Le membre par défaut d'un attribut sert à évaluer des expressions lorsqu'un attribut n'est pas inclus dans une requête.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le **DefaultMember** fonction, conjointement avec le **nom** pour retourner le membre par défaut pour la dimension de devise de Destination dans le cube Adventure Works. L’exemple retourne **Dollar américain**. Le **nom** fonction est utilisée pour retourner le nom de la mesure plutôt que la propriété par défaut de la mesure, qui est **valeur**.  
  
```  
WITH MEMBER Measures.x AS   
   [Destination Currency].[Destination Currency].DefaultMember.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Définir un membre par défaut](../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
