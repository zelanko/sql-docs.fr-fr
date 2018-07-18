---
title: Validation des modèles et à l’aide de modèles pour la prédiction (Data Mining Add-ins pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- mining models, charting
- validation [data mining]
- mining models, testing
ms.assetid: e245ac1f-1230-48e9-9091-e70b131aa2a8
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6cf4beef0255948a416b5a8e8867a3608d7db151
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250829"
---
# <a name="validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel"></a>Validation des modèles et utilisation des modèles pour la prédiction (compléments d'exploration de données pour Excel)
  Le test et la validation de votre modèle est une étape importante du processus d'exploration de données. Vous devez savoir dans quelle mesure vos modèles d'exploration de données sont efficaces sur des données réelles avant de les déployer dans un environnement de production.  
  
 Les compléments d'exploration de données incluent des outils qui permettent de tester les modèles que vous avez créés, et de créer des prédictions et des recommandations à l'aide des modèles.  
  
## <a name="accuracy-chart"></a>Graphique de précision  
 Le **graphique de précision** Assistant vous aide à créer une requête de prédiction et évaluer les performances d’un modèle d’exploration de données en créant un graphique de courbes d’élévation ou un graphique à nuages de points. Le graphique de courbes d'élévation permet de différencier les modèles dans les structures où ils sont presque identiques et de déterminer quels sont ceux permettant d'obtenir les prédictions les plus précises.  
  
 [Graphique de précision &#40;compléments d’exploration de données SQL Server&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
## <a name="classification-matrix"></a>Matrice de classification  
 Le **matrice de Classification** Assistant vous permet de créer une requête de prédiction pour évaluer les performances d’un modèle de classification. Il en résulte un graphique qui synthétise à la fois les prédictions précises et les prédictions imprécises effectuées par le modèle. La matrice est un outil très utile étant donné qu'elle montre non seulement combien de fois le modèle a correctement prédit une valeur, mais aussi les valeurs que le modèle a le plus fréquemment prédites de façon incorrecte.  
  
 [Matrice de classification &#40;compléments d’exploration de données SQL Server&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
  
## <a name="profit-chart"></a>Graphique des bénéfices  
 Le **graphique des bénéfices** Assistant vous aide à évaluer les avantages de l’utilisation d’un modèle d’exploration de données et d’évaluer le coût des faux positifs et faux négatifs  
  
 Ce type de graphique mesure la précision de prédiction du modèle et incorpore l'unité et le coût global spécifiés.  
  
 [Graphique des bénéfices &#40;compléments d’exploration de données SQL Server&#41;](profit-chart-sql-server-data-mining-add-ins.md).  
  
## <a name="cross-validation"></a>Validation croisée  
 La validation croisée est une technique établie dans la communauté d'exploration de données pour évaluer la validité d'un jeu de données et la précision d'un modèle d'exploration de données sur ce jeu de données. Elle divise un ensemble de données en sous-ensembles, puis crée, forme et test de manière itérative les modèles sur chaque sous-ensemble.  
  
 Le **la Validation croisée** Assistant vous permet de spécifier le nombre de REPLIS pour la division des données et fournit un rapport de validation croisée qui statistiquement décrit les différences entre ces sections croisées. Déterminez ensuite si le modèle est efficace sur toutes les données d'apprentissage, ou peut être dévié vers un sous-ensemble particulier.  
  
 [La Validation croisée &#40;compléments d’exploration de données SQL Server&#41;](cross-validation-sql-server-data-mining-add-ins.md)  
  
## <a name="query-wizard"></a>Assistant Requête  
 Le **requête** Assistant est un outil interactif qui vous permet de générer une requête de prédiction. Les requêtes indiquent comment sont générées les recommandations, les prévisions, etc.  
  
 Dans le **requête** Assistant, vous choisissez un modèle, puis fournissez les données d’entrée, en tant que valeurs uniques ou à partir d’une table ou une plage et l’Assistant vous permet de sélectionner les colonnes de sortie. Ajoutez également des fonctions à votre requête pour générer des scores de probabilité et d'autres statistiques utiles.  
  
 [Requête &#40;compléments d’exploration de données SQL Server&#41;](query-sql-server-data-mining-add-ins.md)  
  
## <a name="advanced-query-editor"></a>Éditeur de requête avancé  
 Le **éditeur de requêtes avancé** est un ensemble interactif de boîtes de dialogue qui vous permet de créer tous les types d’instructions DMX, allant de l’exécution des requêtes personnalisées à la création et apprentissage de nouveaux modèles, la suppression de modèles, ou créer de nouvelles données définit.  
  
 [Éditeur de requêtes d’exploration de données avancée](advanced-data-mining-query-editor.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration et nettoyage des données](exploring-and-cleaning-data.md)   
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)   
 [Déploiement et mise à l’échelle des modèles d’exploration de données &#40;les données des compléments d’exploration de données pour Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
