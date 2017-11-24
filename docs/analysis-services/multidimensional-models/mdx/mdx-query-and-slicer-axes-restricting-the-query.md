---
title: "Restriction de la requête avec la requête et l’axe de secteur (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: eae3ee8aa4ea2c47aafbf4f6a881395fa24a5484
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="mdx-query-and-slicer-axes---restricting-the-query"></a>Requête MDX et les Axes de segment - restriction de la requête
  Lors de la formulation d'une instruction SELECT MDX (Multidimensional Expressions), une application examine généralement un cube et divise le jeu de hiérarchies en deux sous-ensembles :  
  
-   Les **axes de requête** — jeu de hiérarchies dont des données sont extraites pour plusieurs membres. Pour plus d’informations sur les axes de requête, consultez [Spécification du contenu d’un axe de requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
-   **L’axe de secteur** — jeu de hiérarchies dont des données sont extraites pour un seul membre. Pour plus d’informations sur l’axe de secteur, consultez [Spécification du contenu d’un axe de secteur &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).  
  
 Dans la mesure où les axes de requête et de secteur peuvent être construits à partir de plusieurs hiérarchies du cube à interroger, ces termes permettent de différencier les hiérarchies utilisées par le cube devant faire l'objet d'une interrogation par rapport aux hiérarchies créées dans le cube retourné par une requête MDX.  
  
 Pour obtenir un exemple d’utilisation des axes de requête et de secteur, consultez [Utilisation d’axes de requête et de secteur dans un exemple simple&#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de membres, de tuples et de jeux &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [Principes de base des requêtes MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
