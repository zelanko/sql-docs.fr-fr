---
description: Members (String) (MDX)
title: Membres (chaîne) (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 95e90f488f4b9182fc237045b570bc9da02f47e6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483822"
---
# <a name="members-string-mdx"></a>Members (String) (MDX)


  Retourne un membre spécifié par une expression de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Members(Member_Name)   
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Name*  
 Expression de chaîne valide qui spécifie un nom de membre.  
  
## <a name="remarks"></a>Notes  
 La fonction **Members (String)** retourne un membre unique dont le nom est spécifié. En général, vous utilisez la fonction **Members (String)** avec des fonctions externes, en fournissant à la fonction **Members (String)** une chaîne qui identifie un membre, et la fonction **Members (String)** retourne la valeur pour ce membre spécifié.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la fonction **Members (String)** pour convertir la chaîne spécifiée en membre valide, puis retourne la mesure par défaut pour le membre spécifié dans la chaîne. La chaîne spécifiée est entre guillemets simples. La mesure par défaut correspond à la mesure Reseller Sales Amount.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
