---
title: DefaultMember (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DefaultMember
dev_langs:
- kbMDX
helpviewer_keywords:
- DefaultMember function
ms.assetid: c1b53b3a-6e73-4c41-a4fe-9f5c96da5463
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 09fa9c7b92fcb6839efc2870b4dad5d6c4a39fa7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="defaultmember-mdx"></a>DefaultMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 L’exemple suivant utilise le **DefaultMember** fonction, conjointement avec la **nom** pour retourner le membre par défaut pour la dimension de devise de Destination dans le cube Adventure Works. L’exemple retourne **Dollar américain**. Le **nom** fonction est utilisée pour retourner le nom de la mesure plutôt que la propriété par défaut de la mesure, qui est **valeur**.  
  
```  
WITH MEMBER Measures.x AS   
   [Destination Currency].[Destination Currency].DefaultMember.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)   
 [Définir un membre par défaut](../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
