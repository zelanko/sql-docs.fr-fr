---
title: Scénario de scénarios (outils d’analyse de table pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- what if scenario
- scenario analysis
ms.assetid: 4df5a5c5-1983-4009-a7c5-cd340649fd2f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ed1fe8447064bf224ea3f0e0a576d4e73fb07203
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938110"
---
# <a name="what-if-scenario-table-analysis-tools-for-excel"></a>Scénario (Outils d'analyse de table pour Excel)
  ![Bouton Scénarios des Outils d'analyse de table](media/tat-whatif.gif "Bouton Scénarios des Outils d'analyse de table")

 L' **outil scénario analyse** les séquences dans les données existantes, puis vous permet d’évaluer l’effet que les modifications apportées à une colonne ont sur la valeur d’une autre colonne.

 Vous pouvez, par exemple, examiner l'effet qu'une augmentation de prix d'un article aurait sur le total de ses ventes.

 L'outil est flexible quant au nombre de prédictions que vous pouvez créer. Après l'analyse initiale, vous pouvez choisir de prédire les modifications pour toutes les données de la table ou bien d'entrer les valeurs de test une par une.

## <a name="using-the-what-if-scenario-tool"></a>Utilisation de l'outil Scénario

1.  Ouvrez une table de données Excel.

2.  Cliquez sur **scénarios**, puis sélectionnez **quoi-faire**.

3.  Dans la zone **scénario** , sélectionnez la colonne qui contient la valeur que vous allez modifier, puis spécifiez la modification en tant que valeur spécifique ou en pourcentage de modification (augmentée ou diminuée) sur les valeurs actuelles.

4.  Dans la zone **qu’est-ce qui se passe** , spécifiez la colonne pour laquelle vous souhaitez évaluer l’effet.

5.  Si vous le souhaitez, cliquez sur **choisir les colonnes à utiliser pour l’analyse** pour sélectionner les colonnes qui sont susceptibles d’être utiles pour effectuer la prédiction. Vous pouvez également désélectionner les colonnes qui risquent de n'avoir aucune ou peu d'utilité pour la détection des séquences de données remarquables, telles que les ID et noms de lignes.

6.  Dans la zone **spécifier la ligne ou la table** , indiquez si vous souhaitez que l’impact soit évalué pour la ligne actuellement sélectionnée uniquement ou pour l’ensemble complet de données de la table.

7.  Si vous sélectionnez **sur cette ligne**, l’outil affiche le résultat dans la boîte de dialogue. Tant que la boîte de dialogue est ouverte, vous pouvez modifier vos choix pour tester d'autres scénarios.

8.  Si vous sélectionnez la **table entière**, l’outil affiche un message d’État dans la boîte de dialogue et ajoute deux nouvelles colonnes à la table de données d’origine. Cliquez sur **Fermer** pour afficher toutes les résultats dans la feuille de calcul.

### <a name="requirements"></a>Configuration requise
 Cet outil utilise l'algorithme MLR (Microsoft Logistic Regression), qui prend en charge la prédiction de valeurs numériques ou discrètes. Cependant, nous suggérons les meilleures pratiques suivantes pour maximiser les résultats :

-   Sélectionnez les colonnes contenant des informations utiles à l'analyse.

-   Si vous ne sélectionnez pas assez de colonnes, il peut être difficile de parvenir à un résultat.

-   Si vous utilisez l’option **to value** , vous devez taper une valeur dans la zone ou sélectionner une valeur dans la liste.

-   Si vous utilisez l’option **pourcentage** , définissez la modification comme une augmentation ou une diminution de pourcentage. La valeur par défaut est de 120 %, ce qui correspond à une augmentation de 20 % par rapport à la valeur actuelle.

> [!NOTE]
>  Si vous ne définissez pas de valeur, vous risquez de recevoir un message d'erreur.

## <a name="understanding-the-results-of-what-if-analysis"></a>Explication des résultats de l'analyse de scénarios
 Lorsque vous créez un scénario de **simulation** , l’outil effectue trois opérations :

-   il crée une structure d'exploration de données qui stocke des faits clés à propos des données de votre table ;

-   il crée un modèle d'exploration de données de régression logistique basé sur vos données ;

-   il crée une requête de prédiction pour chacune des valeurs que vous spécifiez.

 Vous pouvez générer toutes les prédictions en une seule fois en spécifiant la **table entière**. L'outil crée ensuite deux nouvelles colonnes dans la table de données d'origine.

 Les colonnes ajoutées à la table contiennent deux types d'informations : la valeur prédite en fonction de la modification et son niveau de confiance. La confiance correspond à la probabilité que la prédiction est correcte.

 Vous pouvez également entrer une par une les valeurs à modifier dans la boîte de dialogue et afficher les prédictions de manière interactive. Cela revient à créer une requête de *prédiction Singleton*. Les résultats de la requête de prédiction s'affichent avec les informations suivantes : la réussite ou l'échec de la prédiction, la valeur prédite et le niveau de confiance. Le niveau de confiance apparaît sous la forme d'une barre contenant une ligne pointillée. Plus la ligne pointillée est longue, puis le niveau de confiance du résultat est élevé.

 Par exemple, si vous essayez de déterminer l’effet de l’augmentation de l’âge du client sur la volonté du client d’acheter et d’augmenter l’âge du client à 25, l’outil de **simulation** interroge le modèle d’exploration de données et renvoie le résultat suivant :

 **L'analyse de scénarios pour Achats vélo a trouvé une solution.**

 **'Achats vélo' = yes**

 **Confiance : Correcte**

 Ce résultat étant basé sur une ligne existante de la table de données, cela signifie qu'il y a un client spécifique qui, si tous les facteurs restaient les mêmes sauf son âge qui augmenterait à 25 ans, serait susceptible d'acheter un vélo.

 La sortie des prédictions dans la table de données d'origine peut vous permettre de déterminer plus facilement si ces prédictions sont utiles.

## <a name="related-tools"></a>Outils connexes
 Le client d'exploration de données pour Excel, un complément séparé qui fournit des fonctionnalités d'exploration de données plus avancées, comprend des Assistants pour créer des modèles d'exploration de données qui prédisent le comportement. Pour plus d’informations, consultez [création d’un modèle d’exploration de données](creating-a-data-mining-model.md).

 Pour plus d’informations sur l’algorithme utilisé par l’outil scénario de **simulation** , consultez la rubrique « algorithme de régression logistique Microsoft » dans documentation en ligne de SQL Server.

## <a name="see-also"></a>Voir aussi
 [Outils d'analyse de table pour Excel](table-analysis-tools-for-excel.md)


