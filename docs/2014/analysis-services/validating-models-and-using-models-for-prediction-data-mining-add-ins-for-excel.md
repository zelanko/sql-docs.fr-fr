---
title: Validation des modèles et utilisation des modèles pour la prédiction (compléments d’exploration de données pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- mining models, charting
- validation [data mining]
- mining models, testing
ms.assetid: e245ac1f-1230-48e9-9091-e70b131aa2a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 00048ea3c5f344a90e93799a92b4d48c07325482
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938160"
---
# <a name="validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel"></a>Validation des modèles et utilisation des modèles pour la prédiction (compléments d'exploration de données pour Excel)
  Le test et la validation de votre modèle est une étape importante du processus d'exploration de données. Vous devez savoir dans quelle mesure vos modèles d'exploration de données sont efficaces sur des données réelles avant de les déployer dans un environnement de production.  
  
 Les compléments d'exploration de données incluent des outils qui permettent de tester les modèles que vous avez créés, et de créer des prédictions et des recommandations à l'aide des modèles.  
  
## <a name="accuracy-chart"></a>Graphique de précision  
 L’Assistant **graphique de précision** vous aide à créer une requête de prédiction et à évaluer les performances d’un modèle d’exploration de données en créant un graphique de courbes d’élévation ou un graphique à nuages de points. Le graphique de courbes d'élévation permet de différencier les modèles dans les structures où ils sont presque identiques et de déterminer quels sont ceux permettant d'obtenir les prédictions les plus précises.  
  
 [Graphique d’analyse de précision &#40;SQL Server les compléments d’exploration de données&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
## <a name="classification-matrix"></a>Matrice de classification  
 L’Assistant **matrice de classification** vous aide à créer une requête de prédiction pour évaluer les performances d’un modèle de classification. Il en résulte un graphique qui synthétise à la fois les prédictions précises et les prédictions imprécises effectuées par le modèle. La matrice est un outil très utile étant donné qu'elle montre non seulement combien de fois le modèle a correctement prédit une valeur, mais aussi les valeurs que le modèle a le plus fréquemment prédites de façon incorrecte.  
  
 [&#40;de matrices de classification SQL Server des compléments d’exploration de données&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
  
## <a name="profit-chart"></a>Graphique des bénéfices  
 L’Assistant **graphique des bénéfices** vous aide à évaluer les avantages de l’utilisation d’un modèle d’exploration de données et à évaluer les coûts des faux positifs et des faux négatifs  
  
 Ce type de graphique mesure la précision de prédiction du modèle et incorpore l'unité et le coût global spécifiés.  
  
 [Graphique des bénéfices &#40;SQL Server&#41;des compléments d’exploration de données ](profit-chart-sql-server-data-mining-add-ins.md).  
  
## <a name="cross-validation"></a>Validation croisée  
 La validation croisée est une technique établie dans la communauté d'exploration de données pour évaluer la validité d'un jeu de données et la précision d'un modèle d'exploration de données sur ce jeu de données. Elle divise un ensemble de données en sous-ensembles, puis crée, forme et test de manière itérative les modèles sur chaque sous-ensemble.  
  
 L’Assistant **validation croisée** vous permet de spécifier le nombre de replis pour la Division de vos données, puis fournit un rapport de validation croisée qui décrit de façon statistique les différences entre ces sections croisées. Déterminez ensuite si le modèle est efficace sur toutes les données d'apprentissage, ou peut être dévié vers un sous-ensemble particulier.  
  
 [Validation croisée &#40;SQL Server des compléments d’exploration de données&#41;](cross-validation-sql-server-data-mining-add-ins.md)  
  
## <a name="query-wizard"></a>Assistant Requête  
 L’Assistant **requête** est un outil interactif qui vous aide à créer une requête de prédiction. Les requêtes indiquent comment sont générées les recommandations, les prévisions, etc.  
  
 Dans l’Assistant **requête** , vous choisissez un modèle, puis vous fournissez des données d’entrée, soit comme valeurs uniques, soit à partir d’une table ou d’une plage, et l’Assistant vous aide à sélectionner les colonnes à générer. Ajoutez également des fonctions à votre requête pour générer des scores de probabilité et d'autres statistiques utiles.  
  
 [&#40;de requêtes SQL Server des compléments d’exploration de données&#41;](query-sql-server-data-mining-add-ins.md)  
  
## <a name="advanced-query-editor"></a>Éditeur de requête avancé  
 L' **éditeur de requêtes avancé** est un ensemble interactif de boîtes de dialogue qui vous aide à créer tous les types d’instructions DMX, de l’exécution de requêtes personnalisées à la création et à l’apprentissage de nouveaux modèles, à la suppression de modèles ou à la création de nouveaux jeux de données.  
  
 [Éditeur de requêtes d’exploration de données avancée](advanced-data-mining-query-editor.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exploration et nettoyage des données](exploring-and-cleaning-data.md)   
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)   
 [Déploiement et mise à l’échelle des modèles d’exploration de données &#40;les compléments d’exploration de données pour Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
