---
title: Création de prédictions sur un modèle Sequence Clustering (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 94a8d4f9-a76a-49c5-9785-917010359511
author: minewiskan
ms.author: owend
manager: kfilee
ms.openlocfilehash: 893067e234d868ae6dde2f93d93bfd50458bfeb2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63217741"
---
# <a name="creating-predictions-on-a-sequence-clustering-model-intermediate-data-mining-tutorial"></a>Création de prédictions sur un modèle Sequence Clustering (Didacticiel intermédiaire sur l'exploration de données)
  Une fois que vous comprenez mieux le modèle Sequence Clustering en le parcourant dans la visionneuse, vous pouvez créer des requêtes de prédiction à l’aide de Générateur de requêtes de prédiction sous l’onglet **prédiction de modèle d’exploration** de données du concepteur d’exploration de données. Pour créer une prédiction, commencez par sélectionner le modèle Sequence Clustering, puis sélectionnez les données d'entrée. Pour les entrées, vous pouvez utiliser une source de données externe, ou vous pouvez générer une requête singleton et fournir des valeurs dans une boîte de dialogue.  
  
 Cette leçon suppose que vous savez comment utiliser le générateur de requêtes de prédiction et souhaitez apprendre à générer des requêtes qui sont spécifiques à un modèle Sequence Clustering. Pour obtenir des informations générales sur l’utilisation des Générateur de requêtes de prédiction, consultez [interfaces de requête d’exploration de données](../../2014/analysis-services/data-mining/data-mining-query-tools.md) ou la section du didacticiel sur l’exploration de données de base, création de [prédictions &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md).  
  
## <a name="creating-predictions-on-the-regional-model"></a>Création de prédictions sur le modèle régional  
 Pour ce scénario, vous commencerez par créer des requêtes de prédiction singleton pour avoir une idée des différences entre les prédictions selon la région.  
  
#### <a name="to-create-a-singleton-query-on-a-sequence-clustering-model"></a>Pour créer une requête singleton sur un modèle Sequence Clustering  
  
1.  Cliquez sur l’onglet **prédiction de modèle d’exploration** de données du concepteur d’exploration de données.  
  
2.  Dans le menu colonne du **modèle d’exploration de données** , sélectionnez **requête singleton**.  
  
     Le volet **modèle d’exploration de données** et le volet entrée de **requête singleton** s’affichent.  
  
3.  Dans le volet **modèle d’exploration de données** , cliquez sur Sélectionner un **modèle**. (Vous pouvez ignorer cette étape si le mode Sequence Clustering est déjà sélectionné.)  
  
     La boîte de dialogue **Sélectionner le modèle d’exploration de données** s’ouvre.  
  
4.  Développez le nœud qui représente la structure **d’exploration de données Sequence Clustering avec Region**, puis sélectionnez la **séquence de modèles clustering avec Region**. Cliquez sur **OK**. Pour le moment, ignorez le volet d'entrée ; vous spécifierez les entrées après avoir configuré les fonctions de prédiction.  
  
5.  Dans la grille, cliquez sur la cellule vide sous **source** , puis sélectionnez **fonction de prédiction.** Dans la cellule sous **champ**, sélectionnez **PredictSequence**.  
  
    > [!NOTE]  
    >  Vous pouvez également utiliser la fonction **Predict** . Dans ce cas, veillez à choisir la version de la fonction **Predict** qui prend comme argument une colonne de table.  
  
6.  Dans le **volet modèle d’exploration de données** , sélectionnez la `v Assoc Seq Line Items`table imbriquée et faites-la glisser dans la grille vers la zone **critères/argument** de la fonction **PredictSequence** .  
  
     Le glisser-déplacer des noms de table et de colonne vous permet de générer des instructions complexes sans erreurs de syntaxe. Toutefois, elle remplace le contenu actuel de la cellule, qui inclut d’autres arguments facultatifs pour la fonction **PredictSequence** . Pour consulter les autres arguments, vous pouvez ajouter temporairement une deuxième instance de la fonction à la grille pour référence.  
  
7.  Cliquez sur le bouton **résultat** dans le coin supérieur de la générateur de requêtes de prédiction.  
  
 Les résultats attendus contiennent une seule colonne avec l' **expression**d’en-tête. La colonne **expression** contient une table imbriquée avec trois colonnes comme suit :  
  
|$SEQUENCE|Numéro de ligne|Modèle|  
|---------------|-----------------|-----------|  
|1||Mountain-200|  
  
 Que signifient ces résultats ? N'oubliez pas que vous n'avez pas spécifié d'entrées. Par conséquent, la prédiction est élaborée par rapport à la population globale de cas, et Analysis Services retourne la prédiction la plus probable en général.  
  
### <a name="adding-inputs-to-a-singleton-prediction-query"></a>Ajout d'entrées à une requête de prédiction singleton  
 Jusqu'à maintenant, vous n'avez pas spécifié d'entrées. Dans la tâche suivante, vous allez utiliser le volet **entrée de requête singleton** pour spécifier des entrées dans la requête. En premier lieu, vous utiliserez [Region] comme une entrée au modèle Sequence Clustering régional pour déterminer si les séquences prédites sont les mêmes pour toutes les régions. Vous apprendrez ensuite comment modifier la requête pour ajouter la probabilité pour chaque prédiction et aplatir les résultats pour faciliter leur affichage.  
  
##### <a name="to-generate-predictions-for-a-specific-customer-group"></a>Pour générer des prédictions pour un groupe de client spécifique  
  
1.  Cliquez sur le bouton **conception** dans l’angle supérieur gauche de la générateur de requêtes de prédiction pour revenir à la grille de création de la requête.  
  
2.  Dans la boîte de dialogue **entrée de requête singleton** , cliquez sur la `Region`zone **valeur** pour, puis sélectionnez **Europe**.  
  
3.  Cliquez sur le bouton **résultat** pour afficher les prédictions pour les clients en Europe.  
  
4.  Cliquez sur le bouton **conception** dans l’angle supérieur gauche de la générateur de requêtes de prédiction pour revenir à la grille de création de la requête.  
  
5.  Dans la boîte de dialogue **entrée de requête singleton** , cliquez sur la `Region`zone **valeur** pour, puis sélectionnez **Amérique du Nord**.  
  
6.  Cliquez sur le bouton **résultat** pour afficher les prédictions des clients dans Amérique du Nord.  
  
### <a name="adding-probabilities-by-using-a-custom-expression"></a>Ajout des probabilités à l'aide d'une expression personnalisée  
 Générer la probabilité pour chaque prédiction est légèrement plus compliqué, parce que la probabilité est un attribut de la prédiction et est générée comme une table imbriquée. Si vous connaissez les extensions DMX, vous pouvez modifier facilement la requête pour ajouter une instruction de sous-sélection sur la table imbriquée. Toutefois, vous pouvez créer également une instruction de sous-sélection dans le Générateur de requêtes de prédiction en ajoutant une expression personnalisée.  
  
##### <a name="to-output-probabilities-for-a-predicted-sequence-by-using-a-custom-expression"></a>Pour générer des probabilités pour une séquence prédite à l'aide d'une expression personnalisée  
  
1.  Cliquez sur le bouton **conception** dans l’angle supérieur gauche de la générateur de requêtes de prédiction pour revenir à la grille de création de la requête.  
  
2.  Dans la grille, sous **source**, cliquez sur une nouvelle ligne, puis sélectionnez **expression personnalisée**.  
  
3.  Laissez la zone sous **champ** vide.  
  
4.  Pour **alias**, tapez `t`.  
  
5.  Dans la zone **critères/argument** , tapez l’instruction sub-select complète comme indiqué dans l’exemple de code suivant. Veillez à inclure les parenthèses de début et de fin.  
  
    ```  
    (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))  
    ```  
  
6.  Cliquez sur le bouton **résultat** pour afficher les prédictions pour les clients en Europe.  
  
 Les résultats contiennent maintenant deux tables imbriquées, une avec la prédiction, et une avec la probabilité pour la prédiction. Si la requête ne fonctionne pas, vous pouvez basculer en mode affichage de conception de requête et examiner l'instruction de requête complète, qui doit être comme suit :  
  
```  
SELECT  
  PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
  ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
FROM  
  [Sequence Clustering with Region]  
NATURAL PREDICTION JOIN  
(SELECT 'Europe' AS [Region]) AS t  
```  
  
### <a name="working-with-results"></a>Utilisation des résultats  
 En présence d'un grand nombre de tables imbriquées dans les résultats, vous pouvez aplatir les résultats pour faciliter leur affichage. Pour cela, vous pouvez modifier la requête manuellement et ajouter le mot clé `FLATTENED`.  
  
##### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a>Pour aplatir des ensembles de lignes imbriqués dans une requête de prédiction  
  
1.  Cliquez sur le bouton **requête** dans l’angle de la générateur de requêtes de prédiction.  
  
     La grille se transforme en un volet ouvert où vous pouvez afficher et modifier l'instruction DMX créée par le Générateur de requêtes de prédiction.  
  
2.  Après le mot clé `SELECT`, tapez `FLATTENED`.  
  
     Le texte complet de la requête doit être semblable aux éléments suivants :  
  
    ```  
    SELECT FLATTENED  
      PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
      ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
    FROM  
      [Sequence Clustering with Region]  
    NATURAL PREDICTION JOIN  
    (SELECT 'Europe' AS [Region]) AS t  
    ```  
  
3.  Cliquez sur le bouton **résultats** dans le coin supérieur de la générateur de requêtes de prédiction.  
  
 Après avoir modifié une requête manuellement, vous ne pourrez pas revenir en mode Conception sans perdre les modifications. Toutefois, vous pouvez enregistrer sous un fichier texte l'instruction DMX que vous avez créée manuellement, puis repasser en mode Conception. Dans ce cas, la requête est restaurée à la dernière version qui était valide en mode Conception.  
  
## <a name="creating-predictions-on-the-related-model"></a>Création de prédictions sur le modèle connexe  
 Les exemples précédents ont utilisé une colonne de table de cas, Région, comme entrée à la requête de prédiction singleton, parce que vous souhaitiez savoir si le modèle avait trouvé des différences entre des régions. Toutefois, après avoir exploré le modèle, vous avez décidé que les différences ne sont pas assez significatives pour justifier de personnaliser des recommandations de produits par région. Ce que vous cherchez vraiment à prédire sont les éléments que choisissent les clients. Par conséquent, dans les requêtes qui suivent, vous utiliserez le modèle Sequence Clustering qui n'inclut pas Région, pour générer des recommandations pour tous les clients.  
  
### <a name="using-nested-table-columns-as-input"></a>Utilisation de colonnes de table imbriquée comme entrée  
 En premier lieu, vous allez créer une requête de prédiction singleton qui prend un élément unique comme entrée et retourne l'élément suivant le plus probable. Pour obtenir une prédiction de ce type, vous devez utiliser une colonne de table imbriquée comme valeur d'entrée. En effet, l'attribut que vous prédisez, Model, fait partie d'une table imbriquée. Analysis Services fournit la boîte de dialogue entrée de la **table imbriquée** pour vous aider à créer facilement des requêtes de prédiction sur des attributs de tables imbriquées, à l’aide du générateur de requêtes de prédiction.  
  
##### <a name="to-use-a-nested-table-as-input-to-a-prediction"></a>Pour utiliser une table imbriquée comme entrée à une prédiction  
  
1.  Cliquez sur le bouton **conception** dans l’angle supérieur gauche de la générateur de requêtes de prédiction pour revenir à la grille de création de la requête.  
  
2.  Dans la boîte de dialogue **entrée de requête singleton** , cliquez sur la `Region`zone **valeur** pour, puis sélectionnez la ligne vide pour effacer l’entrée pour ce champ.  
  
3.  Dans la boîte de dialogue **entrée de requête singleton** , cliquez sur la `vAssocSeqLineItems`zone **valeur** pour, puis cliquez sur le bouton (...).  
  
4.  Dans la boîte de dialogue entrée de la **table imbriquée** , cliquez sur **Ajouter**.  
  
5.  Dans la nouvelle ligne, cliquez sur la zone `Model`sous, puis sélectionnez Touring Band dans la liste. Cliquez sur **OK**.  
  
6.  Cliquez sur le bouton **résultat** pour afficher les prédictions.  
  
 Le modèle recommande les éléments suivants pour tous les clients qui choisissent Touring Tire comme premier élément. L'exploration du modèle vous a déjà indiqué que les clients achètent fréquemment les produits Touring Tire et Touring Tire Tube en même temps, donc ces recommandations semblent correctes.  
  
|$SEQUENCE|Numéro de ligne|Modèle|  
|---------------|-----------------|-----------|  
|1||Touring Tire Tube (Pneu pour vélo de tourisme)|  
|2||Sport-100|  
|3||Long-Sleeve Logo Jersey (Pull-over à manches longues)|  
  
### <a name="creating-a-bulk-prediction-query-using-nested-table-inputs"></a>Création d'une requête de prédiction de masse à l'aide des entrées de table imbriquée  
 Maintenant que vous avez établi que le modèle crée le type des prédictions que vous pouvez utiliser pour faire des recommandations, vous allez créer une requête de prédiction mappée à une source de données externe. Cette source de données fournit des valeurs qui représentent des produits actuels. Comme vous souhaitez créer une requête de prédiction qui fournit l'ID du client et une liste des produits comme entrée, vous ajouterez la table des clients comme table de cas, et la table des achats comme table imbriquée. Puis, vous ajouterez des fonctions de prédiction comme vous l'avez fait précédemment pour créer des recommandations.  
  
 Il s'agit de la même procédure que vous utilisez pour créer des prédictions pour le scénario d'analyse du panier d'achat de la Leçon 3 ; toutefois, dans un modèle Sequence Clustering, les prédictions font aussi appel à cet ordre comme entrée.  
  
##### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a>Pour créer une requête de prédiction à l'aide d'entrées de table imbriquée  
  
1.  Dans le volet **modèle d’exploration de données** , sélectionnez le modèle Sequence Clustering, s’il n’est pas déjà sélectionné.  
  
2.  Dans la boîte de dialogue **Sélectionner une ou plusieurs tables d’entrée** , cliquez sur **Sélectionner la table de cas**.  
  
3.  Dans la boîte de dialogue **Sélectionner une table** , pour source de données, sélectionnez Orders. Dans la liste nom de la **table/vue** , sélectionnez vAssocSeqOrders, puis cliquez sur **OK**.  
  
4.  Dans la boîte de dialogue **Sélectionner une ou plusieurs tables d’entrée** , cliquez sur **Sélectionner la table imbriquée**.  
  
5.  Dans la boîte de dialogue **Sélectionner une table** , pour **source de données**, sélectionnez Orders. Dans la liste nom de la **table/vue** , sélectionnez vAssocSeqLineItems, puis cliquez sur **OK**.  
  
     Analysis Services va tenter de détecter des relations et de les créer automatiquement si les types de données correspondent et les noms de colonne sont similaires. Si les relations qu’il crée sont incorrectes, vous pouvez cliquer avec le bouton droit sur la ligne de jointure et sélectionner **modifier les connexions** pour modifier le mappage de colonne, ou vous pouvez cliquer avec le bouton droit sur la ligne de jointure et sélectionner **supprimer** pour supprimer complètement la relation. Dans ce cas, comme les tables ont déjà été jointes dans la vue de source de données, ces relations sont ajoutées automatiquement au volet de conception.  
  
6.  Ajoutez une nouvelle ligne à la grille. Pour **source**, sélectionnez vAssocSeqOrders, et pour **champ**, sélectionnez CustomerKey.  
  
7.  Ajoutez une nouvelle ligne à la grille. Pour **source**, sélectionnez **fonction de prédiction**, et pour **champ**, sélectionnez **PredictSequence**.  
  
8.  Faites glisser vAssocSeqLineItems vers la zone **critères/argument** . Cliquez à la fin de la zone **critères/argument** , puis tapez les arguments suivants : `2`.  
  
     Le texte complet de la zone **critères/argument** doit être :`[Sequence Clustering].[v Assoc Seq Line Items],2`  
  
9. Cliquez sur le bouton **résultat** pour afficher les prédictions pour chaque client.  
  
 Vous avez terminé le didacticiel sur les modèles Sequence Clustering.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Si vous avez terminé toutes les sections du didacticiel sur l' [exploration de données intermédiaire &#40;Analysis Services d’exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md), l’étape suivante peut consister à apprendre à utiliser des instructions DMX (Data Mining Extensions) pour créer des modèles et générer des prédictions. Pour plus d’informations, consultez [création et interrogation de modèles d’exploration de données à l’aide de DMX : didacticiels &#40;Analysis Services-exploration de données&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md).  
  
 Si vous maîtrisez les concepts de la programmation, vous pouvez utiliser également des objets AMO (Analysis Management Objects) pour utiliser par programme des objets d'exploration de données. Pour plus d’informations, consultez [Classes d’exploration de données AMO](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes de modèle Sequence Clustering](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)   
 [Contenu du modèle d’exploration de données pour les modèles Sequence Clustering &#40;Analysis Services d’exploration de données&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)  
  
  
