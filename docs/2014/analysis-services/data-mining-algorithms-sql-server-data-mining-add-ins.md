---
title: Algorithmes d’exploration de données (SQL Server Data Mining Add-ins) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation
- data mining algorithms
- clustering [data mining]
- linear regression
- association [data mining]
- neural networks
- logistic regression
- regression
- sequence analysis
- decision tree [data mining]
- Naive Bayes
- time series [data mining]
ms.assetid: 3a1a62e4-9fb5-4cdb-a6c6-1b8b30d417ef
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6e0bf6c0c1126dff29107636e0956d92d4b314a7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66086512"
---
# <a name="data-mining-algorithms-sql-server-data-mining-add-ins"></a>Algorithmes d'exploration de données (Compléments d'exploration de données SQL Server)
  Les Compléments d'exploration de données pour Office prennent en charge la création de modèles analytiques utilisant les algorithmes d'exploration de données suivants. Tous les algorithmes reposent sur des méthodes d'apprentissage automatique connues et ont été implémentés par Microsoft Research.  
  
## <a name="algorithms"></a>Algorithmes  
  
|Méthode d'apprentissage automatique|Fonctionnement|  
|-----------------------------|------------------|  
|Algorithme MAR (Microsoft Association Rules)|Découvrez les produits achetés ensemble ou les événements qui se produisent simultanément, et utilisez le modèle pour créer des recommandations.<br /><br /> [https://msdn.microsoft.com/library/ms174916.aspx](https://msdn.microsoft.com/library/ms174916.aspx)|  
|Algorithme de gestion de clusters Microsoft|Définissez des segments de marché, regroupez automatiquement les clients liés, ou recherchez des relations dans les données à utiliser dans une exploration des données plus détaillée.<br /><br /> [https://msdn.microsoft.com/library/ms174879.aspx](https://msdn.microsoft.com/library/ms174879.aspx)|  
|Algorithme MDT (Microsoft Decision Trees)|Identifiez les relations précédemment inconnues entre chaque élément de vos données afin de mieux éclairer vos décisions, ou recherchez les facteurs qui ont généré des résultats spécifiques.<br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
|Algorithme MLR (Microsoft Linear Regression)|Recherchez une formule mathématique décrivant les facteurs qui contribuent à un résultat numérique.<br /><br /> [https://msdn.microsoft.com/library/ms174824.aspx](https://msdn.microsoft.com/library/ms174824.aspx)|  
|Algorithme MLR (Microsoft Logistic Regression)|Identifiez les facteurs qui contribuent à des résultats binaires et apprenez comment les utiliser pour affecter les résultats.<br /><br /> [https://msdn.microsoft.com/library/ms174828.aspx](https://msdn.microsoft.com/library/ms174828.aspx)|  
|Algorithme MNB (Microsoft Naive Bayes)|Explorez les relations dans vos données et recherchez celles qui sont le plus étroitement corrélées avec un résultat.<br /><br /> [https://msdn.microsoft.com/library/ms174806.aspx](https://msdn.microsoft.com/library/ms174806.aspx)|  
|Algorithme MNN (Microsoft Neural Networks)|Recherchez des relations masquées entre plusieurs entrées et même entre plusieurs sorties. Utilisation pour l'exploration ou pour une prédiction.<br /><br /> [https://msdn.microsoft.com/library/ms174941.aspx](https://msdn.microsoft.com/library/ms174941.aspx)|  
|Algorithme MTS (Microsoft Time Series)|Utilisez des données d'historique pour prédire des valeurs futures.<br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
  
## <a name="advanced-options"></a>Options avancées  
 Lorsque vous utilisez le Client d'exploration de données pour Excel, vous pouvez soit créer vos propres structures et modèles d'exploration de données, soit optimiser les paramètres des algorithmes.  
  
 [Paramètres d’algorithme &#40;compléments d’exploration de données SQL Server&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md)  
  
 Il existe deux façons de personnaliser vos modèles à l'aide de ces options avancées :  
  
-   Utilisez le **requête d’exploration de données** Assistant pour créer votre modèle.  
  
-   Dans le **Client d’exploration de données**, une fois que vous démarrez l’Assistant, cliquez sur **paramètres**.  
  
## <a name="see-also"></a>Voir aussi  
 [Requête &#40;compléments d’exploration de données SQL Server&#41;](query-sql-server-data-mining-add-ins.md)   
 [Avancées de modélisation &#40;les données des compléments d’exploration de données pour Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)  
  
  
