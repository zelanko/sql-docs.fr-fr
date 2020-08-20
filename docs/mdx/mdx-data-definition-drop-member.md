---
description: Définition de données MDX - DROP MEMBER
title: DROP, instruction (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f71232997c24a1bdca9a1294a804e8b30660d704
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483852"
---
# <a name="mdx-data-definition---drop-member"></a>Définition de données MDX - DROP MEMBER


  Supprime un membre calculé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP MEMBER   
   CURRENTCUBE | Cube_Name  
      .Member_Name   
               [,CURRENTCUBE | Cube_Name.Member_Name ...n]  
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Expression de chaîne valide qui précise le nom d'un cube.  
  
 *Member_Identifier*  
 Expression de chaîne valide qui fournit un nom de membre ou une clé de membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction CREATe MEMBER &#40;MDX&#41;](../mdx/mdx-data-definition-create-member.md)   
 [Instructions de définition de données MDX &#40;&#41;MDX ](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
