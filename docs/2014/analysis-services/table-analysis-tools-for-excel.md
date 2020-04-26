---
title: Outils d’analyse de table pour Excel | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- getting started
ms.assetid: 6d9d1481-18e4-4108-9efa-68152b0940c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af4c8ae7c2ba827e6110602bd21432fec4f74393
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "66067971"
---
# <a name="table-analysis-tools-for-excel"></a>Outils d'analyse de table pour Excel
  Les outils d’exploration de données de la barre d’outils **analyse** constituent le moyen le plus simple pour commencer à utiliser l’exploration de données. Chaque outil analyse automatiquement la distribution et le type des données, et définit les paramètres pour garantir que les résultats sont valides. Vous n'avez pas à sélectionner un algorithme ou à configurer des paramètres complexes.  
  
 ![DM](media/dm-tabletoolsanalyze.gif "DM")  
  
 Le ruban **analyser** comprend les outils suivants :  
  
 [Analyser les influenceurs clés &#40;les outils d’analyse de table pour Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 Vous choisissez une colonne ou une valeur de sortie d'intérêt, puis l'algorithme analyse les données d'entrée pour identifier les facteurs qui ont le plus d'influence sur la cible. Éventuellement, créez un rapport qui compare deux valeurs quelconques, afin que vous puissiez voir comment les facteurs d'influence changent.  
  
 L’outil **analyser les influences clés** utilise l’algorithme Microsoft Naïve Bayes.  
  
 [Détecter les catégories &#40;les outils d’analyse de table pour Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
 Cet outil vous permet d'ajouter n'importe quel jeu de données et d'appliquer le clustering pour rechercher des regroupements de données. Il est utile pour rechercher des similarités et pour créer des groupes à analyser plus en détail.  
  
 L’outil **détecter les catégories** utilise l’algorithme de clustering Microsoft.  
  
 [Remplir à partir de l’exemple &#40;les outils d’analyse de table pour Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)  
 Cet outil vous aide à imputer les valeurs manquantes. Vous fournissez des exemples de valeurs manquantes, et l'outil crée des modèles basés sur toutes les données de la table, puis recommande de nouvelles valeurs en fonction des séquences dans les données.  
  
 L’outil **remplir à partir de l’exemple** utilise l’algorithme de régression logistique de Microsoft.  
  
 [Outils d’analyse de table &#40;de prévision pour Excel&#41;](forecast-table-analysis-tools-for-excel.md)  
 Cet outil prend des données qui changent au fil du temps, puis prédit des valeurs futures.  
  
 L’outil **prévision** utilise l’algorithme MTS (Microsoft Time Series).  
  
 [Mettre en surbrillance les exceptions &#40;les outils d’analyse de table pour Excel&#41;](highlight-exceptions-table-analysis-tools-for-excel.md)  
 Cet outil analyse les séquences dans une table de données et recherche les lignes et les valeurs qui ne correspondent pas au modèle. Vous pouvez les examiner et les corriger, puis réexécuter le modèle, ou marquer les valeurs avec un indicateur pour une action ultérieure.  
  
 L’outil **mettre en surbrillance les exceptions** utilise l’algorithme de clustering Microsoft.  
  
 [Scénario de la recherche de l’objectif &#40;outils d’analyse de table pour Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)  
 Dans l’outil **recherche objectif** , vous spécifiez une valeur cible et l’outil identifie les facteurs sous-jacents qui doivent changer pour répondre à cette cible. Par exemple, si vous savez que vous devez augmenter la satisfaction des appels de 20 %, demandez au modèle de prédire les facteurs qui doivent changer pour obtenir cet objectif.  
  
 L’outil de **recherche d’objectif** utilise l’algorithme de régression logistique de Microsoft.  
  
 [Scénario de simulation &#40;les outils d’analyse de table pour Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)  
 L’outil d' **analyse de scénarios** complète l’outil de **recherche d’objectif** . Avec cet outil, vous entrez la valeur que vous souhaitez modifier, puis le modèle prédit si cette modification est suffisante pour obtenir les résultats souhaités. Par exemple, demandez au modèle de déterminer si l'ajout d'un opérateur augmenterait la satisfaction des clients d'un point.  
  
 L’outil **simulation** utilise l’algorithme de régression logistique de Microsoft.  
  
 [Calcul de prédiction &#40;les outils d’analyse de table pour Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 Cet outil crée un modèle d'analyse des facteurs qui mènent aux résultats, puis prédit un résultat pour toute nouvelle entrée, en fonction de règles de score dérivées des données. Il génère également une feuille de calcul interactive pour la prise de décision qui vous permet d'établir le score de nouvelles entrées. Vous pouvez également créer une version imprimée de la feuille de calcul que vous pouvez utiliser hors connexion pour l'établissement du score.  
  
 L’outil **calcul de prédiction** utilise l’algorithme de régression logistique de Microsoft.  
  
 [Analyse du panier d’achat &#40;table outils pour Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)  
 Cet outil identifie les modèles qui peuvent être utilisés dans la vente croisée ou la vente incitative. Il identifie les groupes de produits qui sont souvent achetés ensemble, et il génère également des rapports basés sur le prix et le coût de paquets de produits connexes, pour aider à la prise de décision.  
  
 Il n'est pas limité à l'analyse du panier d'achat ; appliquez-le à tout problème qui se prête à l'analyse d'association. Par exemple, recherchez les événements qui se produisent fréquemment ensemble, les facteurs conduisant à un diagnostic, ou tout autre ensemble de causes et résultats potentiels.  
  
 L’outil d' **analyse du panier d’achat** utilise l’algorithme Microsoft Association.  
  
## <a name="requirements-for-the-table-analysis-tools-for-excel"></a>Conditions requises pour les outils d'analyse de table pour Excel  
 Pour utiliser les outils d'analyse de table pour Excel, vous devez commencer par créer une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Cette connexion vous donne accès aux algorithmes d'exploration de données Microsoft qui sont utilisés pour analyser vos données. Si vous n'avez pas accès à une instance, nous vous recommandons de demander à votre administrateur d'installer une instance à utiliser pour tester l'exploration de données. Pour plus d’informations, consultez [se connecter à des données sources &#40;client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Pour utiliser des données à l'aide des outils d'analyse de table, vous devez convertir la plage de données que vous souhaitez utiliser dans des tables Excel.  
  
 Si vous ne voyez pas le ruban **analyser** , essayez d’abord de cliquer à l’intérieur d’une table de données. Le menu n'est pas activé tant qu'une table de données n'est pas sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Client d’exploration de données pour Excel &#40;SQL Server des compléments d’exploration de données&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)   
 [Dépannage des diagrammes d’exploration de données Visio &#40;SQL Server des compléments d’exploration de données&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)   
 [Éléments inclus dans les compléments d'exploration de données pour Office](what-s-included-in-the-data-mining-add-ins-for-office.md)  
  
  
