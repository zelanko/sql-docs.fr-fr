---
title: Restriction de la requête avec la requête et de l’axe de secteur (MDX) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4ad9f1b3a60707a0a10c9b15865286e1ad53eb2c
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52508466"
---
# <a name="mdx-query-and-slicer-axes---restricting-the-query"></a>Axes de requête et de segment MDX - Restriction de la requête
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Lors de la formulation d'une instruction SELECT MDX (Multidimensional Expressions), une application examine généralement un cube et divise le jeu de hiérarchies en deux sous-ensembles :  
  
-   **Axes de requête**-l’ensemble des hiérarchies à partir de laquelle les données sont extraites pour plusieurs membres. Pour plus d’informations sur les axes de requête, consultez [Spécification du contenu d’un axe de requête &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
-   **Axe de secteur**-l’ensemble des hiérarchies à partir de laquelle les données sont extraites pour un seul membre. Pour plus d’informations sur l’axe de secteur, consultez [Spécification du contenu d’un axe de secteur &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).  
  
 Dans la mesure où les axes de requête et de secteur peuvent être construits à partir de plusieurs hiérarchies du cube à interroger, ces termes permettent de différencier les hiérarchies utilisées par le cube devant faire l'objet d'une interrogation par rapport aux hiérarchies créées dans le cube retourné par une requête MDX.  
  
 Pour obtenir un exemple d’utilisation des axes de requête et de secteur, consultez [Utilisation d’axes de requête et de secteur dans un exemple simple&#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de membres, de tuples et de jeux &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [Principes de base des requêtes MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
