---
title: Membres (String) (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Members
dev_langs: kbMDX
helpviewer_keywords: Members function
ms.assetid: 21fca354-448b-4b05-93f4-111bde1568f1
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: bed8ef7372528320ff18be737c15218d80983690
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="members-string-mdx"></a>Members (String) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne un membre spécifié par une expression de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Members(Member_Name)   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Name*  
 Expression de chaîne valide qui spécifie un nom de membre.  
  
## <a name="remarks"></a>Notes  
 Le **membres (String)** fonction retourne un seul membre dont le nom est spécifié. En général, vous utilisez la **membres (String)** fonction avec des fonctions externes, en fournissant à la **membres (String)** fonction d’une chaîne qui identifie un membre, et le **membres (String)** fonction retourne la valeur de ce membre spécifié.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le **membres (String)** de fonction pour convertir la chaîne spécifiée à un membre valide, puis retourne la mesure par défaut pour le membre spécifié dans la chaîne. La chaîne spécifiée est entre guillemets simples. La mesure par défaut correspond à la mesure Reseller Sales Amount.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
