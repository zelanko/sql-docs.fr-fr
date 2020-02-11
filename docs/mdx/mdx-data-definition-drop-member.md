---
title: DROP, instruction (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4e8e38a3ff3f40f44c911a277f99ab9b629c7c87
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038195"
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
 [Instructions de définition de données MDX &#40;&#41;MDX](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
