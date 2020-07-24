---
title: Fonctions de prédiction générales (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cde2fe9da61ca9d877f0c905609d8baf832ea509
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971668"
---
# <a name="general-prediction-functions-dmx"></a>Fonctions de prédiction générales (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Vous pouvez utiliser l’instruction **Select** dans les extensions DMX (Data Mining Extensions) pour créer différents types de requêtes. Une requête peut être utilisée pour retourner des informations sur le modèle d'exploration de données lui-même, afin de faire de nouvelles prédictions ou encore modifier le modèle en effectuant un apprentissage avec de nouvelles données. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]fournit diverses fonctions spécialisées qui contrôlent le type d’informations retournées dans une requête. En ajoutant ces fonctions à une requête DMX, vous pouvez récupérer des statistiques ou des colonnes de données supplémentaires. Toutefois, pour chaque type de requête et chaque type de modèle, seules certaines fonctions sont prises en charge.  
  
## <a name="common-functions"></a>Fonctions communes  
 Vous pouvez utiliser des fonctions pour étendre les résultats retournés par un modèle d'exploration de données. Vous pouvez utiliser les fonctions suivantes pour toute instruction **Select** qui retourne une expression de table :  
  
|||  
|-|-|  
|[BottomCount &#40;DMX&#41;](../dmx/bottomcount-dmx.md)|[RangeMin&#41;DMX &#40;](../dmx/rangemin-dmx.md)|  
|[BottomPercent&#41;DMX &#40;](../dmx/bottompercent-dmx.md)|[&#40;DMX&#41;](../dmx/topcount-dmx.md)|  
|[Predict &#40;DMX&#41;](../dmx/predict-dmx.md)|[&#41;DMX &#40;](../dmx/toppercent-dmx.md)|  
|[RangeMax&#41;DMX &#40;](../dmx/rangemax-dmx.md)|[&#41;DMX &#40;DMX](../dmx/topsum-dmx.md)|  
|[RangeMid&#41;DMX &#40;](../dmx/rangemid-dmx.md)||  
  
 De plus, les fonctions suivantes sont prises en charge pour la plupart des types de modèles :  
  
-   [Existe &#40;DMX&#41;](../dmx/exists-dmx.md)  
  
-   [IsDescendant &#40;DMX&#41;](../dmx/isdescendant-dmx.md)  
  
-   [IsTestCase&#41;DMX &#40;](../dmx/istestcase-dmx.md)  
  
-   [IsTrainingCase&#41;DMX &#40;](../dmx/istrainingcase-dmx.md)  
  
-   [Predict &#40;DMX&#41;](../dmx/predict-dmx.md)  
  
-   [RangeMax&#41;DMX &#40;](../dmx/rangemax-dmx.md)  
  
-   [RangeMid&#41;DMX &#40;](../dmx/rangemid-dmx.md)  
  
-   [RangeMin&#41;DMX &#40;](../dmx/rangemin-dmx.md)  
  
-   [StructureColumn&#41;DMX &#40;](../dmx/structurecolumn-dmx.md)  
  
 Les algorithmes individuels peuvent prendre en charge des fonctions supplémentaires. Pour obtenir la liste des fonctions prises en charge par chaque type de modèle, consultez [requêtes d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/data-mining-queries).  
  
## <a name="functions-specific-to-select-syntax"></a>Fonctions spécifiques à la syntaxe SELECT  
 Le tableau suivant répertorie les fonctions que vous pouvez utiliser pour chaque type d’instruction **Select** .  
  
 Pour obtenir des informations générales sur les fonctions dans DMX, consultez [Data Mining Extensions &#40;dmx&#41; Function Reference](../dmx/data-mining-extensions-dmx-function-reference.md).  
  
|Type de requête|Fonctions prises en charge|Notes|  
|----------------|-------------------------|-------------|  
|[SELECT DISTINCT FROM \<model>](../dmx/select-distinct-from-model-dmx.md)|[RangeMin&#41;DMX &#40;](../dmx/rangemin-dmx.md)<br /><br /> [RangeMid&#41;DMX &#40;](../dmx/rangemid-dmx.md)<br /><br /> [RangeMax&#41;DMX &#40;](../dmx/rangemax-dmx.md)|Ces fonctions peuvent être utilisées pour fournir des valeurs maximales, des valeurs minimales et des moyennes pour toute colonne contenant un type de données numérique, que la colonne soit continue ou ait été discrétisée.|  
|[SELECT FROM \<model>.CONTENT](../dmx/select-from-model-content-dmx.md)<br /><br /> ou<br /><br /> [SELECT FROM \<model>.DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md)|[IsDescendant &#40;DMX&#41;](../dmx/isdescendant-dmx.md)|Cette fonction récupère les nœuds enfants pour le nœud spécifié dans le modèle. Elle peut être utilisée, par exemple, pour parcourir les nœuds dans le contenu du modèle d'exploration de données. La disposition des nœuds dans le contenu du modèle d'exploration de données dépend du type de modèle. Pour plus d’informations sur la structure de chaque type de modèle d’exploration de données, consultez [Mining Model Content &#40;Analysis Services-data mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-analysis-services-data-mining).<br /><br /> Si vous avez enregistré le contenu du modèle d'exploration de données sous forme d'une dimension, vous pouvez aussi utiliser d'autres fonctions MDX (Multidimensional Expressions) disponibles pour interroger une hiérarchie d'attribut.|  
|[SELECT FROM \<model>.CASES](../dmx/select-from-model-cases-dmx.md)|[IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md)<br /><br /> [Classe ClientSettingsGeneralFlag](../relational-databases/wmi-provider-configuration-classes/clientsettingsgeneralflag-class/clientsettingsgeneralflag-class.md)<br /><br /> [IsTrainingCase&#41;DMX &#40;](../dmx/istrainingcase-dmx.md)<br /><br /> [IsTestCase&#41;DMX &#40;](../dmx/istestcase-dmx.md)|La fonction lag est prise en charge uniquement pour les modèles de série chronologique.<br /><br /> La fonction IsTestCase est prise en charge dans les modèles basés sur une structure créée à l’aide de l’option exclusion pour créer un jeu de données de test. Si le modèle n'est pas basé sur une structure avec le jeu de test d'exclusion, tous les cas sont traités comme des cas d'apprentissage.|  
|[SELECT FROM \<model>.SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md)|[IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md)|Dans ce contexte, la fonction IsInNode retourne un cas qui appartient à un ensemble de cas d’exemple idéaux.|  
|Sélectionnez à partir de \<model> . PMML|Non applicable. Utilisez plutôt des fonctions de requête XML.|Les représentations PMML ne sont prises en charge que pour les types de modèles suivants :<br /><br /> [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees<br /><br /> [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering|  
|[SELECT FROM \<model> PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md)|Fonctions de prédiction spécifiques à l'algorithme que vous utilisez pour générer le modèle.|Pour obtenir la liste des fonctions de prédiction pour chaque type de modèle, consultez [requêtes d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/data-mining-queries).|  
|[SÉLECTIONNER DANS\<model>](../dmx/select-from-model-dmx.md)|Fonctions de prédiction spécifiques à l'algorithme que vous utilisez pour générer le modèle.|Pour obtenir la liste des fonctions de prédiction pour chaque type de modèle, consultez [requêtes d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/data-mining-queries).|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-reference.md)   
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
