---
title: Création de prédictions sur un modèle Sequence Clustering (didacticiel d’exploration de données intermédiaire) | Microsoft Docs
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63217741"
---
# <a name="creating-predictions-on-a-sequence-clustering-model-intermediate-data-mining-tutorial"></a>Création de prédictions sur un modèle Sequence Clustering (Didacticiel intermédiaire sur l'exploration de données)
  Une fois que vous comprenez le modèle sequence clustering mieux parcouru dans la visionneuse, vous pouvez créer des requêtes de prédiction à l’aide du Générateur de requêtes de prédiction sur le **prévision de modèle d’exploration de données** onglet dans le Concepteur d’exploration de données. Pour créer une prédiction, commencez par sélectionner le modèle Sequence Clustering, puis sélectionnez les données d'entrée. Pour les entrées, vous pouvez utiliser une source de données externe, ou vous pouvez générer une requête singleton et fournir des valeurs dans une boîte de dialogue.  
  
 Cette leçon suppose que vous savez comment utiliser le générateur de requêtes de prédiction et souhaitez apprendre à générer des requêtes qui sont spécifiques à un modèle Sequence Clustering. Pour obtenir des informations générales sur l’utilisation du Générateur de requêtes de prédiction, consultez [Interfaces de requête d’exploration de données](../../2014/analysis-services/data-mining/data-mining-query-tools.md) ou la section du didacticiel d’exploration de données de base, [création de prédictions &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md).  
  
## <a name="creating-predictions-on-the-regional-model"></a>Création de prédictions sur le modèle régional  
 Pour ce scénario, vous commencerez par créer des requêtes de prédiction singleton pour avoir une idée des différences entre les prédictions selon la région.  
  
#### <a name="to-create-a-singleton-query-on-a-sequence-clustering-model"></a>Pour créer une requête singleton sur un modèle Sequence Clustering  
  
1.  Cliquez sur le **prévision de modèle d’exploration de données** onglet du Concepteur d’exploration de données.  
  
2.  Dans le **Mining Model** colonne, sélectionnez **requête Singleton**.  
  
     Le **Mining Model** volet et **entrée de requête Singleton** volet s’affiche.  
  
3.  Dans le **Mining Model** volet, cliquez sur **sélectionner un modèle**. (Vous pouvez ignorer cette étape si le mode Sequence Clustering est déjà sélectionné.)  
  
     Le **sélectionner un modèle d’exploration de données** boîte de dialogue s’ouvre.  
  
4.  Développez le nœud qui représente la structure d’exploration de données **Sequence Clustering avec Region**, puis sélectionnez le modèle **Sequence Clustering avec Region**. Cliquez sur **OK**. Pour le moment, ignorez le volet d'entrée ; vous spécifierez les entrées après avoir configuré les fonctions de prédiction.  
  
5.  Dans la grille, cliquez sur la cellule vide sous **Source** et sélectionnez **fonction de prédiction.** Dans la cellule sous **champ**, sélectionnez **PredictSequence**.  
  
    > [!NOTE]  
    >  Vous pouvez également utiliser le **Predict** (fonction). Si vous fassiez, veillez à choisir la version de la **Predict** fonction qui prend une colonne de table comme argument...  
  
6.  Dans le **Mining Model** volet, sélectionnez la table imbriquée `v Assoc Seq Line Items`et faites-le glisser dans la grille, à la **critères/Argument** zone pour le **PredictSequence** (fonction).  
  
     Le glisser-déplacer des noms de table et de colonne vous permet de générer des instructions complexes sans erreurs de syntaxe. Toutefois, cette opération remplace le contenu actuel de la cellule, qui inclut d’autres arguments facultatifs pour le **PredictSequence** (fonction). Pour consulter les autres arguments, vous pouvez ajouter temporairement une deuxième instance de la fonction à la grille pour référence.  
  
7.  Cliquez sur le **résultat** bouton dans le coin supérieur du Générateur de requêtes de prédiction.  
  
 Les résultats attendus contiennent une seule colonne avec l’en-tête **Expression**. Le **Expression** colonne contient une table imbriquée avec trois colonnes comme suit :  
  
|$SEQUENCE|Numéro de ligne|Modèle|  
|---------------|-----------------|-----------|  
|1||Mountain-200|  
  
 Que signifient ces résultats ? N'oubliez pas que vous n'avez pas spécifié d'entrées. Par conséquent, la prédiction est élaborée par rapport à la population globale de cas, et Analysis Services retourne la prédiction la plus probable en général.  
  
### <a name="adding-inputs-to-a-singleton-prediction-query"></a>Ajout d'entrées à une requête de prédiction singleton  
 Jusqu'à maintenant, vous n'avez pas spécifié d'entrées. Dans la tâche suivante, vous allez utiliser le **entrée de requête Singleton** volet pour spécifier des entrées à la requête. En premier lieu, vous utiliserez [Region] comme une entrée au modèle Sequence Clustering régional pour déterminer si les séquences prédites sont les mêmes pour toutes les régions. Vous apprendrez ensuite comment modifier la requête pour ajouter la probabilité pour chaque prédiction et aplatir les résultats pour faciliter leur affichage.  
  
##### <a name="to-generate-predictions-for-a-specific-customer-group"></a>Pour générer des prédictions pour un groupe de client spécifique  
  
1.  Cliquez sur le **conception** bouton dans le coin supérieur gauche du Générateur de requêtes de prédiction pour revenir à la grille de création de requête.  
  
2.  Dans le **entrée de requête Singleton** boîte de dialogue, cliquez sur le **valeur** boîte pour `Region`, puis sélectionnez **Europe**.  
  
3.  Cliquez sur le **résultat** bouton pour consulter des prédictions pour les clients en Europe.  
  
4.  Cliquez sur le **conception** bouton dans le coin supérieur gauche du Générateur de requêtes de prédiction pour revenir à la grille de création de requête.  
  
5.  Dans le **entrée de requête Singleton** boîte de dialogue, cliquez sur le **valeur** boîte pour `Region`, puis sélectionnez **Amérique du Nord**.  
  
6.  Cliquez sur le **résultat** bouton pour afficher des prédictions pour les clients en Amérique du Nord.  
  
### <a name="adding-probabilities-by-using-a-custom-expression"></a>Ajout des probabilités à l'aide d'une expression personnalisée  
 Générer la probabilité pour chaque prédiction est légèrement plus compliqué, parce que la probabilité est un attribut de la prédiction et est générée comme une table imbriquée. Si vous connaissez les extensions DMX, vous pouvez modifier facilement la requête pour ajouter une instruction de sous-sélection sur la table imbriquée. Toutefois, vous pouvez créer également une instruction de sous-sélection dans le Générateur de requêtes de prédiction en ajoutant une expression personnalisée.  
  
##### <a name="to-output-probabilities-for-a-predicted-sequence-by-using-a-custom-expression"></a>Pour générer des probabilités pour une séquence prédite à l'aide d'une expression personnalisée  
  
1.  Cliquez sur le **conception** bouton dans le coin supérieur gauche du Générateur de requêtes de prédiction pour revenir à la grille de création de requête.  
  
2.  Dans la grille, sous **Source**, cliquez sur une nouvelle ligne, puis sélectionnez **Expression personnalisée**.  
  
3.  Laissez la case sous **champ** vide.  
  
4.  Pour **Alias**, type `t`.  
  
5.  Dans le **critères/Argument** , tapez l’instruction de sous-sélection complète comme illustré dans l’exemple de code suivant. Veillez à inclure les parenthèses de début et de fin.  
  
    ```  
    (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))  
    ```  
  
6.  Cliquez sur le **résultat** bouton pour consulter des prédictions pour les clients en Europe.  
  
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
  
1.  Cliquez sur le **requête** bouton dans l’angle du Générateur de requêtes de prédiction.  
  
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
  
3.  Cliquez sur le **résultats** bouton dans le coin supérieur du Générateur de requêtes de prédiction.  
  
 Après avoir modifié une requête manuellement, vous ne pourrez pas revenir en mode Conception sans perdre les modifications. Toutefois, vous pouvez enregistrer sous un fichier texte l'instruction DMX que vous avez créée manuellement, puis repasser en mode Conception. Dans ce cas, la requête est restaurée à la dernière version qui était valide en mode Conception.  
  
## <a name="creating-predictions-on-the-related-model"></a>Création de prédictions sur le modèle connexe  
 Les exemples précédents ont utilisé une colonne de table de cas, Région, comme entrée à la requête de prédiction singleton, parce que vous souhaitiez savoir si le modèle avait trouvé des différences entre des régions. Toutefois, après avoir exploré le modèle, vous avez décidé que les différences ne sont pas assez significatives pour justifier de personnaliser des recommandations de produits par région. Ce que vous cherchez vraiment à prédire sont les éléments que choisissent les clients. Par conséquent, dans les requêtes qui suivent, vous utiliserez le modèle Sequence Clustering qui n'inclut pas Région, pour générer des recommandations pour tous les clients.  
  
### <a name="using-nested-table-columns-as-input"></a>Utilisation de colonnes de table imbriquée comme entrée  
 En premier lieu, vous allez créer une requête de prédiction singleton qui prend un élément unique comme entrée et retourne l'élément suivant le plus probable. Pour obtenir une prédiction de ce type, vous devez utiliser une colonne de table imbriquée comme valeur d'entrée. En effet, l'attribut que vous prédisez, Model, fait partie d'une table imbriquée. Analysis Services fournit le **entrée de la Table imbriquée** boîte de dialogue pour vous aider à créer facilement des requêtes de prédiction sur imbriqués des attributs de tables, en utilisant le Générateur de requête de prédiction.  
  
##### <a name="to-use-a-nested-table-as-input-to-a-prediction"></a>Pour utiliser une table imbriquée comme entrée à une prédiction  
  
1.  Cliquez sur le **conception** bouton dans le coin supérieur gauche du Générateur de requêtes de prédiction pour revenir à la grille de création de requête.  
  
2.  Dans le **entrée de requête Singleton** boîte de dialogue, cliquez sur le **valeur** boîte pour `Region`, puis sélectionnez la ligne vide pour effacer l’entrée pour ce champ.  
  
3.  Dans le **entrée de requête Singleton** boîte de dialogue, cliquez sur le **valeur** boîte pour `vAssocSeqLineItems`, puis cliquez sur le bouton (...).  
  
4.  Dans le **entrée de la Table imbriquée** boîte de dialogue, cliquez sur **ajouter**.  
  
5.  Dans la nouvelle ligne, cliquez sur la zone sous `Model`et sélectionnez Touring Tire dans la liste. Cliquez sur **OK**.  
  
6.  Cliquez sur le **résultat** bouton pour afficher les prédictions.  
  
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
  
1.  Dans le **Mining Model** volet, sélectionnez le modèle Sequence Clustering, si ce n’est pas déjà fait.  
  
2.  Dans le **sélectionner une ou plusieurs tables d’entrée** boîte de dialogue, cliquez sur **sélectionner la Table de cas**.  
  
3.  Dans le **sélectionner une Table** boîte de dialogue, pour la Source de données, sélectionnez Orders. Dans le **nom de la Table/vue** liste, sélectionnez vAssocSeqOrders, puis cliquez sur **OK**.  
  
4.  Dans le **sélectionner une ou plusieurs tables d’entrée** boîte de dialogue, cliquez sur **sélectionner la Table imbriquée**.  
  
5.  Dans le **sélectionner une Table** boîte de dialogue pour **Source de données**, sélectionnez Orders. Dans le **nom de la Table/vue** liste, sélectionnez vAssocSeqLineItems, puis cliquez sur **OK**.  
  
     Analysis Services va tenter de détecter des relations et de les créer automatiquement si les types de données correspondent et les noms de colonne sont similaires. Si les relations qu’il crée sont incorrectes, vous pouvez cliquez sur la ligne de jointure et sélectionner **modifier les connexions** pour modifier la colonne de mappage, ou vous pouvez avec le bouton droit de la ligne de jointure et sélectionner **supprimer** à supprimer complètement la relation. Dans ce cas, comme les tables ont déjà été jointes dans la vue de source de données, ces relations sont ajoutées automatiquement au volet de conception.  
  
6.  Ajoutez une nouvelle ligne à la grille. Pour **Source**, sélectionnez vAssocSeqOrders et pour **champ**, sélectionnez CustomerKey.  
  
7.  Ajoutez une nouvelle ligne à la grille. Pour **Source**, sélectionnez **fonction de prédiction**et pour **champ**, sélectionnez **PredictSequence**.  
  
8.  Faites glisser vAssocSeqLineItems dans la **critères/Argument** boîte. Cliquez sur à la fin de la **critères/Argument** zone, puis tapez les arguments suivants : `2`.  
  
     Le texte complet dans le **critères/Argument** case doit être : `[Sequence Clustering].[v Assoc Seq Line Items],2`  
  
9. Cliquez sur le **résultat** bouton pour afficher les prédictions pour chaque client.  
  
 Vous avez terminé le didacticiel sur les modèles Sequence Clustering.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Si vous avez terminé toutes les sections dans le [didacticiel d’exploration de données intermédiaire &#40;Analysis Services - Exploration de données&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md), l’étape suivante consiste à apprendre à utiliser les instructions des Extensions DMX (Data Mining) pour générer des modèles et générer des prédictions. Pour plus d’informations, consultez [création et interrogation de modèles d’exploration de données avec DMX : Didacticiels &#40;Analysis Services - Exploration de données&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md).  
  
 Si vous maîtrisez les concepts de la programmation, vous pouvez utiliser également des objets AMO (Analysis Management Objects) pour utiliser par programme des objets d'exploration de données. Pour plus d’informations, consultez [Classes d’exploration de données AMO](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes).  
  
## <a name="see-also"></a>Voir aussi  
 [Sequence Clustering Model Query Examples](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)   
 [Contenu du modèle d’exploration de données pour les modèles Sequence Clustering &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)  
  
  
