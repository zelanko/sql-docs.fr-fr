---
title: DROP SET, instruction (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f4e31a687597e454b9afe38d6c6dd1c15af486d0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68893727"
---
# <a name="mdx-data-definition---drop-set"></a>Définition de données MDX - DROP SET


  Supprime un jeu nommé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP [SESSION] SET   
   <Cube_Reference>.Set_Name   
               [,<Cube_Reference>.Set_Name ...n]  
  
<Cube_Reference> ::= {CURRENTCUBE | Cube_Name}  
  
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Expression de chaîne valide qui précise le nom du cube.  
  
 *Set_Name*  
 Expression de chaîne valide qui précise le nom du jeu nommé à supprimer.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les jeux nommés, consultez [Création de jeux nommés à l’aide d’expressions MDX &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets).  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données MDX &#40;&#41;MDX](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
