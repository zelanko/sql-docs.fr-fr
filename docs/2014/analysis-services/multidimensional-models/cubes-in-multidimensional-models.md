---
title: Cubes dans les modèles multidimensionnels | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c7ce00bc87ca17c97996023d7cb9a4745b9882f3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66076106"
---
# <a name="cubes-in-multidimensional-models"></a>Cubes dans les modèles multidimensionnels
  Un cube est une structure multidimensionnelle qui contient des informations à des fins analytiques ; les constituants principaux d'un cube sont des dimensions et des mesures. Les dimensions définissent la structure du cube que vous utilisez pour la découpe, et les mesures fournissent des valeurs numériques agrégées qui intéressent l'utilisateur final. Comme structure logique, un cube permet à une application cliente de récupérer des valeurs, de mesures, comme si elles étaient contenues dans des cellules du cube ; les cellules sont définies pour chaque valeur résumée possible. Une cellule, dans le cube, est définie par l'intersection des membres de dimension et contient les valeurs agrégées des mesures à cette intersection spécifique.  
  
## <a name="benefits-of-using-cubes"></a>Avantages de l'utilisation des cubes  
 Un cube fournit un seul emplacement où toutes les données associées, pour l'analyse, sont stockées.  
  
## <a name="components-of-cubes"></a>Composants des cubes  
 Un cube est composé de :  
  
|Élément|Description|  
|-------------|-----------------|  
|Dimensions|[Dimensions dans les modèles multidimensionnels](dimensions-in-multidimensional-models.md)|  
|Mesures et groupes de mesures|[Créer des mesures et des groupes de mesures dans les modèles multidimensionnels](create-measures-and-measure-groups-in-multidimensional-models.md)|  
|Partitions|[Partitions dans les modèles multidimensionnels](partitions-in-multidimensional-models.md)|  
|perspectives|[Perspectives dans les modèles multidimensionnels](perspectives-in-multidimensional-models.md)|  
|Hierarchies|[Créer des hiérarchies définies par l’utilisateur](user-defined-hierarchies-create.md)|  
|Actions|[Actions dans les modèles multidimensionnels](actions-in-multidimensional-models.md)|  
|Indicateurs de performance clés (KPI)|[Indicateurs de performance clés &#40;&#41; KPI dans les modèles multidimensionnels](key-performance-indicators-kpis-in-multidimensional-models.md)|  
|Calculs|[Calculs dans les modèles multidimensionnels](calculations-in-multidimensional-models.md)|  
|Translations|[Traductions dans les modèles multidimensionnels](translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a>Tâches associées  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Créer un cube à l'aide de l'Assistant Cube](create-a-cube-using-the-cube-wizard.md)|Décrit comment utiliser l'Assistant Cube pour définir un cube, des dimensions, des attributs de dimension et des hiérarchies définies par l'utilisateur.|  
|[Créer des mesures et des groupes de mesures dans les modèles multidimensionnels](create-measures-and-measure-groups-in-multidimensional-models.md)|Décrit comment définir des groupes de mesures.|  
|[Calculs dans les modèles multidimensionnels](calculations-in-multidimensional-models.md)|Décrit comment définir et configurer un calcul dans un script MDX.|  
|[Actions dans les modèles multidimensionnels](actions-in-multidimensional-models.md)|Décrit comment définir et configurer une action.|  
|[Perspectives dans les modèles multidimensionnels](perspectives-in-multidimensional-models.md)|Décrit comment définir et configurer une perspective.|  
|[Définition de procédures stockées](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|Décrit comment utiliser les procédures stockées.|  
  
  
