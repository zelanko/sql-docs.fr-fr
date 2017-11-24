---
title: "(Syntaxe MDX) de mots clés réservés | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- reserved words [MDX]
- Multidimensional Expressions [Analysis Services], reserved words
- MDX [Analysis Services], reserved words
ms.assetid: 0baab5fb-bd04-4ab3-b99a-9f91f3470fbb
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 986213edcc0e95c593e4bd9954b36cfbefca8be3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="reserved-keywords-mdx-syntax"></a>Mots clés réservés (syntaxe MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] réserve certains mots clés pour son usage exclusif. Pour obtenir la liste des mots clés réservés, consultez [les mots réservés MDX](../mdx/mdx-reserved-words.md).  
  
 Les mots clés respectent les principes suivants :  
  
-   Vous ne pouvez inclure des mots clés réservés dans une instruction MDX (Multidimensional Expressions) qu'à l'emplacement défini par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   Aucun objet de la base de données ne peut recevoir un nom qui correspond à un mot clé réservé. Si le cas se présente, il faut toujours faire référence à l'objet en délimitant les identificateurs. Même si cette méthode n'autorise pas les noms d'objets en tant que mots réservés, l'utilisation de mots clés pour nommer des objets doit être évitée.  
  
-   Utilisez une convention d'attribution de noms qui permet d'éviter l'utilisation de mots clés réservés. Les consonnes ou les voyelles peuvent être supprimées si un nom d’objet doit ressembler à un mot clé réservé.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments de syntaxe MDX &#40; MDX &#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
