---
title: Restriction de la requête avec les Axes de requête et segment (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b2a7d69055d3d60f8805a7cf7e8b9f1a98b9c01e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048181"
---
# <a name="restricting-the-query-with-query-and-slicer-axes-mdx"></a>Restriction de la requête avec des axes de requête et de secteur (MDX)
  Lors de la formulation d'une instruction SELECT MDX (Multidimensional Expressions), une application examine généralement un cube et divise le jeu de hiérarchies en deux sous-ensembles :  
  
-   Les **axes de requête** — jeu de hiérarchies dont des données sont extraites pour plusieurs membres. Pour plus d’informations sur les axes de requête, consultez [Spécification du contenu d’un axe de requête &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
-   **L’axe de secteur** — jeu de hiérarchies dont des données sont extraites pour un seul membre. Pour plus d’informations sur l’axe de secteur, consultez [Spécification du contenu d’un axe de secteur &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).  
  
 Dans la mesure où les axes de requête et de secteur peuvent être construits à partir de plusieurs hiérarchies du cube à interroger, ces termes permettent de différencier les hiérarchies utilisées par le cube devant faire l'objet d'une interrogation par rapport aux hiérarchies créées dans le cube retourné par une requête MDX.  
  
 Pour obtenir un exemple d’utilisation des axes de requête et de secteur, consultez [Utilisation d’axes de requête et de secteur dans un exemple simple&#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de membres, Tuples et jeux &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)   
 [Principes de base de requête MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
