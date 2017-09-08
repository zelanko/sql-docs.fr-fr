---
title: "Cubes dans les modèles multidimensionnels | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1a555a25c41b4860aa16d5a2cfd43749a0ccd65d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="cubes-in-multidimensional-models"></a>Cubes dans les modèles multidimensionnels
  Un cube est une structure multidimensionnelle qui contient des informations à des fins analytiques ; les constituants principaux d'un cube sont des dimensions et des mesures. Les dimensions définissent la structure du cube que vous utilisez pour la découpe, et les mesures fournissent des valeurs numériques agrégées qui intéressent l'utilisateur final. Comme structure logique, un cube permet à une application cliente de récupérer des valeurs, de mesures, comme si elles étaient contenues dans des cellules du cube ; les cellules sont définies pour chaque valeur résumée possible. Une cellule, dans le cube, est définie par l'intersection des membres de dimension et contient les valeurs agrégées des mesures à cette intersection spécifique.  
  
## <a name="benefits-of-using-cubes"></a>Avantages de l'utilisation des cubes  
 Un cube fournit un seul emplacement où toutes les données associées, pour l'analyse, sont stockées.  
  
## <a name="components-of-cubes"></a>Composants des cubes  
 Un cube est composé de :  
  
|Élément|Description|  
|-------------|-----------------|  
|Dimensions|[Dimensions dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)|  
|Mesures et groupes de mesures|[Création de mesures et de groupes de mesures dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|  
|Partitions|[Partitions dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/partitions-in-multidimensional-models.md)|  
|Perspectives|[Perspectives dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|  
|Hierarchies|[Créer des hiérarchies définies par l'utilisateur](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)|  
|Actions|[Actions dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|  
|Indicateurs de performance clés (KPI)|[Indicateurs de performance clés &#40;KPI&#41; dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)|  
|calculs|[Calculs dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|  
|Translations|[Traductions dans les modèles multidimensionnels &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Créer un cube à l'aide de l'Assistant Cube](../../analysis-services/multidimensional-models/create-a-cube-using-the-cube-wizard.md)|Décrit comment utiliser l'Assistant Cube pour définir un cube, des dimensions, des attributs de dimension et des hiérarchies définies par l'utilisateur.|  
|[Création de mesures et de groupes de mesures dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)|Décrit comment définir des groupes de mesures.|  
|[Calculs dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)|Décrit comment définir et configurer un calcul dans un script MDX.|  
|[Actions dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/actions-in-multidimensional-models.md)|Décrit comment définir et configurer une action.|  
|[Perspectives dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/perspectives-in-multidimensional-models.md)|Décrit comment définir et configurer une perspective.|  
|[Définition de procédures stockées](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|Décrit comment utiliser les procédures stockées.|  
  
  
