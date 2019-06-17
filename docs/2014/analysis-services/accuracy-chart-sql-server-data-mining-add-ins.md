---
title: Graphique de précision (SQL Server Data Mining Add-ins) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- mining models, validating
- mining models, charting
- lift chart
- mining models, testing
- lift [data mining]
ms.assetid: 303973b4-71c0-4cfc-b7bc-92218b52509d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ebe159aed7b27bf00ef47a110de1c7ec5ee70adb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66062990"
---
# <a name="accuracy-chart-sql-server-data-mining-add-ins"></a>Graphique de précision (Compléments d'exploration de données SQL Server)
  ![Bouton graphique de précision dans le ruban Exploration de données](media/dmc-accchart.gif "bouton graphique de précision dans le ruban Exploration de données")  
  
 Un graphique de précision permet d'appliquer un modèle à un nouveau jeu de données, puis d'évaluer les performances du modèle. Le graphique de précision créé par cet Assistant est un *graphique de courbes d’élévation*, qui est un type de graphique qui est fréquemment utilisée pour mesurer la précision d’un modèle d’exploration de données. Ce type de graphique de précision fournit une représentation graphique de l'amélioration obtenue grâce à l'utilisation du modèle d'exploration de données spécifié, par rapport à des prédictions aléatoires et par rapport au cas idéal dans lequel 100 % des prédictions sont exactes. Vous pouvez comparer plusieurs modèles dans un graphique unique.  
  
## <a name="example"></a>Exemple  
 Prenons le cas du service Marketing d'Adventure Works Cycles qui souhaite créer une campagne de publipostage ciblée. Les campagnes précédentes permettent de prévoir un taux de réponse de 10 %. L'entreprise possède une liste de 10 000 clients potentiels stockés dans une table de la base de données. D'après le taux de réponse habituel, l'entreprise peut s'attendre à ce que 1 000 clients répondent.  
  
 Toutefois, étant donné que le budget affecté ne permet d'envoyer la publicité qu'à 5 000 clients, le service Marketing utilise un modèle d'exploration de données pour cibler les 5 000 clients qui sont le plus susceptibles de répondre.  
  
 Si l'entreprise sélectionne au hasard 5 000 clients, elle peut s'attendre à recevoir seulement 500 réponses positives, car seuls 10 pour cent des clients contactés répondent habituellement. Ce scénario est représenté par la ligne aléatoire dans le graphique de courbes d'évaluation.  
  
 Par contre, si le service Marketing utilisait un modèle d'exploration de données pour cibler le publipostage et que ce modèle était parfait, la société pourrait s'attendre à recevoir les 1 000 réponses en envoyant un publipostage aux 1 000 clients potentiels recommandés par le modèle. Ce scénario est représenté par la ligne idéale dans le graphique de courbes d'élévation.  
  
## <a name="using-the-accuracy-chart-wizard"></a>Utilisation de l'Assistant Graphique de précision  
 Pour créer un graphique de précision, vous devez référencer une structure d'exploration de données existante. Vous pouvez mesurer l'exactitude de plusieurs modèles basés sur cette structure, tant qu'ils prédisent la même chose.  
  
 Si vous n'êtes pas sûr de connaître les structures qui sont disponibles, vous pouvez parcourir le serveur. Pour plus d’informations, consultez [exploration des modèles dans Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).  
  
#### <a name="to-create-an-accuracy-chart"></a>Pour créer un graphique de précision  
  
1.  Cliquez sur le **Client d’exploration de données** ruban.  
  
2.  Dans le **précision et Validation** de groupe, cliquez sur **graphique de précision**.  
  
3.  Dans le **sélectionner une Structure ou modèle** boîte de dialogue, sélectionnez le modèle que vous souhaitez évaluer. Cliquer sur **Suivant**.  
  
    > [!NOTE]  
    >  Vous devez choisir un modèle qui correspond le mieux possible aux données que vous avez l'intention de tester.  
  
4.  Dans le **spécifier colonne à prédire et valeur à prédire** boîte de dialogue, sélectionnez la colonne que vous souhaitez prédire et une valeur cible, le cas échéant. Cliquer sur **Suivant**.  
  
     Par exemple, dans l'exemple ci-dessus, vous pouvez choisir la colonne qui modélise la réponse des clients et spécifier « Achat probable » comme valeur cible.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas prédire une valeur continue. Toutefois, vous pouvez discrétiser la colonne en séparant les valeurs en plages discrètes. Vous devez effectuer cette opération avant de créer le modèle d'exploration de données.  
  
5.  Dans le **sélectionner les données Source** boîte de dialogue, spécifiez la source de données que vous allez transmettre via le modèle pour créer une prédiction.  
  
6.  Si vous utilisez une source externe de données et non les données de test qui sont stockées avec le modèle, dans le **spécifier la relation** boîte de dialogue, mappez les colonnes dans les nouvelles données de source aux colonnes utilisées dans le modèle d’exploration de données.  
  
     Si les noms de colonne sont similaires, l'Assistant les mappe automatiquement. Bien que certaines colonnes de vos données d'entrée puissent être ignorées car n'ayant aucune utilité pour l'analyse, d'autres sont requises pour que le modèle d'exploration de données puisse traiter l'entrée. Ces colonnes peuvent inclure un ID de transaction, la valeur cible ou des colonnes utilisées à des fins de prédiction. Si vous ne pouvez pas mapper une colonne requise, l'Assistant affichera un message d'avertissement.  
  
7.  Cliquez sur **Terminer**.  
  
     L'Assistant crée un rapport comprenant le graphique de courbes d'élévation et les données sous-jacentes.  
  
### <a name="requirements"></a>Configuration requise  
 Dans le cas de la prédiction d'une valeur discrète, vous devez sélectionner la valeur cible à prédire. Par exemple, si vos données sont classées avec une réponse « Oui : Acheter » en tant que 1 et la réponse « No : Ne pas acheter » en tant que 2, vous devez spécifier 1 ou 2 comme valeurs de prédiction. Par contre, si vous voulez prédire une plage de valeurs, vous ne pouvez comparer que deux valeurs à la fois. Par exemple, si vous voulez prédire un score supérieur à 5, il peut être nécessaire de réétiqueter vos données sources et de créer un nouveau modèle qui sépare les résultats en deux groupes : d'un côté, les valeurs supérieures à 5, de l'autre, les valeurs inférieures à 5. Vous pouvez ensuite comparer la précision de ces deux groupes.  
  
## <a name="understanding-accuracy"></a>À propos de la précision  
 Vous pouvez créer deux types de graphiques, l'un permettant de spécifier un état de la colonne prévisible, et l'autre ne permettant pas de spécifier l'état.  
  
 Si vous spécifiez l'état de la colonne prévisible, l'axe des abscisses (x) du graphique représente le pourcentage du jeu de données de test utilisé pour comparer les prédictions. L'axe des ordonnées (y) du graphique représente le pourcentage des valeurs prévues comme l'état spécifié.  
  
 Si vous ne spécifiez pas l'état de la colonne prévisible, le graphique indique la précision du modèle pour toutes les prédictions possibles.  
  
 Pour plus d'informations sur le fonctionnement d'un graphique de courbes d'élévation et sur la manière dont la précision est calculée en fonction des lignes de prédictions aléatoires et idéales, consultez la rubrique « Graphique de courbes d'élévation » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Validation des modèles et à l’aide de modèles pour la prédiction &#40;les données des compléments d’exploration de données pour Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
