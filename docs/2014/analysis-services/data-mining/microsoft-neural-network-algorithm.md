---
title: Algorithme de réseau neuronal Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- training neural networks
- output neurons [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- neurons [Analysis Services]
- classification algorithms [Analysis Services]
- neural networks
- multilayer perceptron network of neurons [Analysis Services]
- hidden neurons
- Back-Propagated Delta Rule network
- input neurons [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 61eb4861-8a6a-4214-a4b8-1dd278ad7a68
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a7330fab8b4c0ecdff296e0daa5e529442fd8b94
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66083872"
---
# <a name="microsoft-neural-network-algorithm"></a>Microsoft Neural Network Algorithm
  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], l' [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithme de réseau neuronal associe chaque état possible de l’attribut d’entrée à chaque état possible de l’attribut prévisible et utilise les données d’apprentissage pour calculer les probabilités. Vous pouvez utiliser ces probabilités ultérieurement pour procéder à une classification ou à une régression ainsi que pour prédire le résultat de l'attribut prédit en fonction des attributs d'entrée.  
  
 Un modèle d'exploration de données généré avec l'algorithme MNN ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network) peut contenir plusieurs réseaux, en fonction du nombre de colonnes utilisées soit pour l'entrée et la prédiction, soit uniquement pour la prédiction. Le nombre de réseaux d'un modèle d'exploration de données dépend du nombre d'états figurant dans les colonnes d'entrée et dans les colonnes prédictibles utilisées par ce modèle d'exploration de données.  
  
## <a name="example"></a>Exemple  
 L'algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network) permet d'analyser des données d'entrée complexes, telles que les données d'un processus commercial ou de fabrication, ou des problèmes d'entreprise pour lesquels une quantité significative de données d'apprentissage est disponible, mais pour lesquels des règles ne peuvent pas être facilement dérivées en utilisant d'autres algorithmes.  
  
 Voici quelques suggestions de scénarios d'utilisation de l'algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network) :  
  
-   analyse de marketing et de promotion des ventes, par exemple pour mesurer le succès d'une campagne de publicité directe ou radiophonique ;  
  
-   prédiction des mouvements des stocks, des fluctuations monétaires ou d'autres informations financières extrêmement inconstantes à partir des données d'historique ;  
  
-   analyse de processus de fabrication et de processus industriels.  
  
-   Exploration de texte.  
  
-   Tout modèle de prédiction qui analyse des relations complexes entre de nombreuses entrées et des sorties beaucoup moins nombreuses.  
  
## <a name="how-the-algorithm-works"></a>Fonctionnement de l'algorithme  
 L’algorithme MNN ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network) crée un réseau composé de trois couches de neurones maximum. une couche d'entrée, une couche masquée facultative et une couche de sortie.  
  
 **Couche d’entrée :** Les neurones d’entrée définissent toutes les valeurs d’attribut d’entrée pour le modèle d’exploration de données, ainsi que leurs probabilités.  
  
 **Couche masquée :** Les neurones cachés reçoivent des entrées des neurones d’entrée et fournissent des sorties aux neurones de sortie. La couche masquée correspond à la couche où des poids sont affectés aux diverses probabilités des entrées. Un poids décrit la pertinence ou l’importance d'une entrée donnée par rapport au neurone masqué. Plus le poids assigné à une entrée est élevé, plus la valeur de cette entrée sera importante. Les poids peuvent être négatifs, ce qui implique que l'entrée peut désactiver un résultat spécifique au lieu de l'activer.  
  
 **Couche de sortie :** Les neurones de sortie représentent des valeurs d’attribut prévisibles pour le modèle d’exploration de données.  
  
 Pour en savoir plus sur la construction et le notation des couches d’entrée, des couches masquées et des couches de sortie, consultez [Informations techniques de référence sur l’algorithme MNN (Microsoft Neural Network)](microsoft-neural-network-algorithm-technical-reference.md).  
  
## <a name="data-required-for-neural-network-models"></a>Données requises pour les modèles Neural Network  
 Un modèle de réseau neuronal doit contenir une colonne clé, une ou plusieurs colonnes d'entrée et une ou plusieurs colonnes prédictibles.  
  
 Les modèles d’exploration de données qui utilisent l’algorithme MNN ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network) sont fortement influencés par les valeurs que vous spécifiez pour les paramètres accessibles à l’algorithme. Les paramètres définissent comment les données sont échantillonnées, comment elles sont distribuées ou comment leur distribution est prévue dans chaque colonne, ainsi que le moment où la sélection de fonctionnalité est invoquée pour limiter les valeurs utilisées dans le modèle final.  
  
 Pour plus d’informations sur la définition des paramètres permettant de personnaliser le comportement d’un modèle, consultez [Informations techniques de référence sur l’algorithme MNN (Microsoft Neural Network)](microsoft-neural-network-algorithm-technical-reference.md).  
  
## <a name="viewing-a-neural-network-model"></a>Affichage d’un modèle Neural Network  
 Pour utiliser les données et voir comment le modèle met en corrélation les entrées et les sorties, vous pouvez utiliser la **Visionneuse de l’algorithme MNN (Microsoft Neural Network)**. Cette visionneuse personnalisée vous permet de définir des filtres sur les attributs d’entrée et leurs valeurs et présentent des graphiques qui illustrent leur impact sur les sorties. Les info-bulles de la visionneuse montrent la probabilité et l'élévation associées à chaque paire de valeurs d'entrée et de sortie. Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’algorithme MNN (Microsoft Neural Network)](browse-a-model-using-the-microsoft-neural-network-viewer.md).  
  
 Le moyen le plus simple d’explorer la structure du modèle est d’utiliser la **Visionneuse de l’arborescence de contenu générique Microsoft**. Vous pouvez consulter les entrées, les sorties et les réseaux créés par le modèle et cliquer sur n’importe quel nœud pour le développer et consulter les statistiques liées aux nœuds des couches d’entrée, de sortie ou masquée. Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’arborescence de contenu générique Microsoft](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).  
  
## <a name="creating-predictions"></a>Création de prédictions  
 Une fois le modèle traité, vous pouvez utiliser le réseau et les poids stockés au sein de chaque nœud pour faire des prédictions. Un modèle de réseau neuronal prend en charge la régression, l’association et l’analyse de classification. Par conséquent, la signification de chaque prédiction peut être différente. Vous pouvez également interroger le modèle lui-même pour examiner les corrélations qui ont été trouvées et extraire les statistiques connexes. Pour obtenir des exemples de création de requêtes sur un modèle de réseau neuronal, consultez [Exemples de requêtes de modèle de réseau neuronal](neural-network-model-query-examples.md).  
  
 Pour obtenir des informations générales sur la création d’une requête sur un modèle d’exploration de données, consultez [Requêtes d’exploration de données](data-mining-queries.md).  
  
## <a name="remarks"></a>Notes  
  
-   Ne prend pas en charge l’extraction ou les dimensions d’exploration de données. Cela est dû au fait que la structure des nœuds du modèle d'exploration de données ne correspond pas nécessairement directement aux données sous-jacentes.  
  
-   Ne prend pas en charge la création de modèles au format de langage PMML (Predictive Model Markup Language).  
  
-   Prend en charge l'utilisation de modèles d'exploration de données OLAP.  
  
-   Ne prend pas en charge la création de dimensions d’exploration de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations techniques de référence sur l’algorithme Microsoft neuronal Network](microsoft-neural-network-algorithm-technical-reference.md)   
 [Contenu du modèle d’exploration de données pour les modèles de réseau neuronal &#40;Analysis Services d’exploration de données&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [Exemples de requêtes de modèle de réseau neuronal](neural-network-model-query-examples.md)   
 [Algorithme MLR (Microsoft Logistic Regression)](microsoft-logistic-regression-algorithm.md)  
  
  
