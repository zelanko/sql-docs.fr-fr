---
title: Structure et utilisation des requêtes de prédiction DMX | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 99d8ef98ad4e86bce0e1beff819a8d140662aaf7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67938069"
---
# <a name="structure-and-usage-of-dmx-prediction-queries"></a>Structure et utilisation des requêtes de prédiction DMX
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], vous pouvez utiliser la requête de prédiction dans les extensions DMX (Data Mining Extensions) pour prédire les valeurs de colonnes inconnues dans un nouveau jeu de données, en fonction des résultats d’un modèle d’exploration de données.  
  
 Le type de requête utilisé dépend des informations que vous souhaitez obtenir d'un modèle. Si vous voulez créer des prédictions simples en temps réel, par exemple pour savoir si un éventuel client sur un site Web correspond au personnage de l'acheteur de bicyclette, vous utilisez une requête singleton. En revanche, si vous souhaitez créer un lot de prédictions à partir d'un ensemble de cas figurant dans une source de données, vous devez utiliser une requête de prédiction standard.  
  
## <a name="prediction-types"></a>Types de prédictions  
 Dans DMX, vous pouvez créer les types de prédictions suivants :  
  
 Jointure de prédiction  
 Ce type de prédiction permet de créer des prédictions sur des données d'entrée sur la base des schémas qui figurent dans le modèle d'exploration de données. Cette instruction de requête doit être suivie d’une clause on qui fournit les conditions **de** jointure entre les colonnes du modèle d’exploration de données et les colonnes d’entrée.  
  
 Jointure de prédiction naturelle  
 Ce type de prédiction permet de créer des prédictions basées sur les noms de colonnes du modèle d'exploration de données qui correspondent exactement aux noms de colonnes de la table sur laquelle vous effectuez la requête. Cette instruction de requête ne nécessite pas **de clause on** , car la condition de jointure est automatiquement générée en fonction des noms correspondants entre les colonnes du modèle d’exploration de données et les colonnes d’entrée.  
  
 Jointure de prédiction vide  
 Cette requête permet de découvrir la prédiction la plus probable, sans avoir à fournir de données d'entrée. Elle retourne une prédiction basée uniquement sur le contenu du modèle d'exploration de données.  
  
 Requête singleton  
 Ce type de prédiction permet de créer une prédiction en alimentant les données à la requête. Cette instruction est utile car elle permet de soumettre un seul cas à la requête et d'obtenir les résultats rapidement. Par exemple, vous pouvez utiliser la requête pour prévoir si une personne, du sexe féminin, âgée de 35 ans et mariée, serait susceptible d'acheter une bicyclette. Cette requête ne nécessite pas de source de données externe.  
  
## <a name="query-structure"></a>Structure de la requête  
 Pour construire une requête de prédiction en DMX, vous devez utiliser une combinaison des éléments suivants :  
  
-   **SELECT [APLATI]**  
  
-   **TOP**  
  
-   **À partir du***\<modèle>* **PREDICTION JOIN**      
  
-   **ACTIVÉ**  
  
-   **WHERE**  
  
-   **ORDER BY**  
  
 L’élément **Select** d’une requête de prédiction définit les colonnes et les expressions qui s’affichent dans le jeu de résultats, et peut inclure les données suivantes :  
  
-   **Prédiction** ou **PredictOnly** des colonnes du modèle d’exploration de données.  
  
-   Toute colonne des données d'entrée utilisée pour créer les prédictions.  
  
-   Des fonctions retournant une colonne de données.  
  
 L’élément **from** * \<Model>* **PREDICTION JOIN** définit les données sources à utiliser pour créer la prédiction. Pour une requête singleton, c'est une série de valeurs affectées aux colonnes. Pour une jointure de prédiction vide, l'élément est vide.  
  
 L’élément **on** mappe les colonnes définies dans le modèle d’exploration de données aux colonnes d’un DataSet externe. Il est inutile d'inclure cet élément si vous créez une requête de jointure de prédiction vide ou une jointure de prédiction naturelle.  
  
 Vous pouvez utiliser la clause **Where** pour filtrer les résultats d’une requête de prédiction. Vous pouvez utiliser une clause **Top** ou **order by** pour sélectionner les prédictions les plus probables. Pour plus d’informations sur l’utilisation de ces clauses, consultez [SELECT &#40;DMX&#41;](../dmx/select-dmx.md).  
  
 Pour plus d’informations sur la syntaxe d’une instruction de prédiction, consultez [Select from &#60;model&#62; PREDICTION JOIN &#40;dmx&#41;](../dmx/select-from-model-prediction-join-dmx.md) et [Select from &#60;model&#62; &#40;DMX&#41;](../dmx/select-from-model-dmx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-reference.md)   
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
