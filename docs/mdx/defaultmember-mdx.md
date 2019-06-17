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
manager: kfile
ms.openlocfilehash: 3a0c11acadcbdcadfd9398baff09db9292c87eb2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248131"
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
  
  
