---
title: Outils d’analyse de table pour Excel | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- getting started
ms.assetid: 6d9d1481-18e4-4108-9efa-68152b0940c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 596bc66152f36c25169e4a089644042d25f8c13b
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52391897"
---
# <a name="table-analysis-tools-for-excel"></a>Outils d'analyse de table pour Excel
  Les outils d’exploration de données dans le **analyser** barre d’outils sont le moyen le plus simple pour bien démarrer avec l’exploration de données. Chaque outil analyse automatiquement la distribution et le type des données, et définit les paramètres pour garantir que les résultats sont valides. Vous n'avez pas à sélectionner un algorithme ou à configurer des paramètres complexes.  
  
 ![DM](media/dm-tabletoolsanalyze.gif "DM")  
  
 Le **analyser** ruban comprend les outils suivants :  
  
 [Analyser les facteurs d’influence clés &#40;outils d’analyse de Table pour Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 Vous choisissez une colonne ou une valeur de sortie d'intérêt, puis l'algorithme analyse les données d'entrée pour identifier les facteurs qui ont le plus d'influence sur la cible. Éventuellement, créez un rapport qui compare deux valeurs quelconques, afin que vous puissiez voir comment les facteurs d'influence changent.  
  
 Le **analyser les facteurs d’influence clés** outil utilise l’algorithme Microsoft Naïve Bayes.  
  
 [Détecter les catégories &#40;outils d’analyse de Table pour Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
 Cet outil vous permet d'ajouter n'importe quel jeu de données et d'appliquer le clustering pour rechercher des regroupements de données. Il est utile pour rechercher des similitudes et pour créer des groupes à analyser.  
  
 Le **détecter les catégories** outil utilise l’algorithme Microsoft Clustering.  
  
 [Remplir à partir de l’exemple &#40;outils d’analyse de Table pour Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)  
 Cet outil vous aide à imputer les valeurs manquantes. Vous fournissez des exemples de valeurs manquantes, et l'outil crée des modèles basés sur toutes les données de la table, puis recommande de nouvelles valeurs en fonction des séquences dans les données.  
  
 Le **remplir à partir de l’exemple** outil utilise l’algorithme Microsoft Logistic Regression.  
  
 [Prévision &#40;outils d’analyse de Table pour Excel&#41;](forecast-table-analysis-tools-for-excel.md)  
 Cet outil prend des données qui changent au fil du temps, puis prédit des valeurs futures.  
  
 Le **prévision** outil utilise l’algorithme Microsoft Time Series.  
  
 [Mettez en surbrillance les Exceptions &#40;outils d’analyse de Table pour Excel&#41;](highlight-exceptions-table-analysis-tools-for-excel.md)  
 Cet outil analyse les séquences dans une table de données et recherche les lignes et les valeurs qui ne correspondent pas au modèle. Vous pouvez les examiner et les corriger, puis réexécuter le modèle, ou marquer les valeurs avec un indicateur pour une action ultérieure.  
  
 Le **mettre en surbrillance les Exceptions** outil utilise l’algorithme Microsoft Clustering.  
  
 [Scénario valeur cible &#40;outils d’analyse de Table pour Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)  
 Dans le **valeur cible** outil, vous spécifiez une valeur cible et l’outil identifie les facteurs sous-jacents qui doivent changer pour atteindre cette cible. Par exemple, si vous savez que vous devez augmenter la satisfaction des appels de 20 %, demandez au modèle de prédire les facteurs qui doivent changer pour obtenir cet objectif.  
  
 Le **valeur cible** outil utilise l’algorithme Microsoft Logistic Regression.  
  
 [Scénario de simulation &#40;outils d’analyse de Table pour Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)  
 Le **analyse de scénarios** outil complète la **valeur cible** outil. Avec cet outil, vous entrez la valeur que vous souhaitez modifier, puis le modèle prédit si cette modification est suffisante pour obtenir les résultats souhaités. Par exemple, demandez au modèle de déterminer si l'ajout d'un opérateur augmenterait la satisfaction des clients d'un point.  
  
 Le **What If** outil utilise l’algorithme Microsoft Logistic Regression.  
  
 [Calcul de prédiction &#40;outils d’analyse de Table pour Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 Cet outil crée un modèle d'analyse des facteurs qui mènent aux résultats, puis prédit un résultat pour toute nouvelle entrée, en fonction de règles de score dérivées des données. Il génère également une feuille de calcul interactive pour la prise de décision qui vous permet d'établir le score de nouvelles entrées. Vous pouvez également créer une version imprimée de la feuille de calcul que vous pouvez utiliser hors connexion pour l'établissement du score.  
  
 Le **calcul de prédiction** outil utilise l’algorithme Microsoft Logistic Regression.  
  
 [Analyse de panier d’achat &#40;outils d’analyse de Table pour Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)  
 Cet outil identifie les modèles qui peuvent être utilisés dans la vente croisée ou la vente incitative. Il identifie les groupes de produits qui sont souvent achetés ensemble, et il génère également des rapports basés sur le prix et le coût de paquets de produits connexes, pour aider à la prise de décision.  
  
 Il n'est pas limité à l'analyse du panier d'achat ; appliquez-le à tout problème qui se prête à l'analyse d'association. Par exemple, recherchez les événements qui se produisent fréquemment ensemble, les facteurs conduisant à un diagnostic, ou tout autre ensemble de causes et résultats potentiels.  
  
 Le **analyse de panier d’achat** outil utilise l’algorithme Microsoft Association.  
  
## <a name="requirements-for-the-table-analysis-tools-for-excel"></a>Conditions requises pour les outils d'analyse de table pour Excel  
 Pour utiliser les outils d'analyse de table pour Excel, vous devez commencer par créer une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Cette connexion vous donne accès aux algorithmes d'exploration de données Microsoft qui sont utilisés pour analyser vos données. Si vous n'avez pas accès à une instance, nous vous recommandons de demander à votre administrateur d'installer une instance à utiliser pour tester l'exploration de données. Pour plus d’informations, consultez [se connecter à la Source de données &#40;Client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Pour utiliser des données à l'aide des outils d'analyse de table, vous devez convertir la plage de données que vous souhaitez utiliser dans des tables Excel.  
  
 Si vous ne voyez pas le **analyser** du ruban, cliquez tout d’abord à l’intérieur d’une table de données. Le menu n'est pas activé tant qu'une table de données n'est pas sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Client d’exploration de données pour Excel &#40;compléments d’exploration de données SQL Server&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)   
 [Dépannage des diagrammes d’exploration de données Visio &#40;compléments d’exploration de données SQL Server&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)   
 [Éléments inclus dans les compléments d’exploration de données pour Office](what-s-included-in-the-data-mining-add-ins-for-office.md)  
  
  
