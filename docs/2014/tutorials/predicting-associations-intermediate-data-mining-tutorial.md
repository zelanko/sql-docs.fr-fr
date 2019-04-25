---
title: Prédiction d’Associations (didacticiel d’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9140c5f2-b340-45a6-9c27-d870d15aafea
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bee5ca4ded1b2fd5cbda0712cb766c825b9d0318
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472844"
---
# <a name="predicting-associations-intermediate-data-mining-tutorial"></a>Prédiction d'associations (Didacticiel sur l'exploration de données intermédiaire)
  Après avoir traité les modèles, vous pouvez utiliser les informations sur les associations stockées dans le modèle pour créer des prédictions. Dans la dernière tâche de cette leçon, vous apprenez comment générer des requêtes de prédiction sur les modèles d'association que vous avez créés. Cette leçon suppose que vous savez comment utiliser le Générateur de requêtes de prédiction et que vous souhaitez apprendre à générer des requêtes de prédiction sur des modèles d'association. Pour plus d’informations comment utiliser le Générateur de requête de prédiction, consultez [Interfaces de requête d’exploration de données](../../2014/analysis-services/data-mining/data-mining-query-tools.md).  
  
## <a name="creating-a-singleton-prediction-query"></a>Création d'une requête singleton de prédiction  
 Les requêtes de prédiction sur un modèle d'association peuvent être très utiles :  
  
-   pour recommander des éléments à un client, selon les achats antérieurs ou connexes ;  
  
-   pour rechercher des événements associés ;  
  
-   pour identifier des relations entre ou au sein de jeux de transactions.  
  
 Pour générer une requête de prédiction, vous sélectionnez d'abord le modèle d'association à utiliser, puis vous spécifiez les données d'entrée. Les entrées peuvent provenir d'une source de données externe, telle qu'une liste de valeurs, ou vous pouvez générer une requête singleton et fournir des valeurs au fur et à mesure.  
  
 Pour ce scénario, vous allez d'abord créer des requêtes singleton de prédiction, pour comprendre comment la prédiction fonctionne. Ensuite, vous allez créer une requête pour les prédictions par lot que vous pourriez utiliser pour faire des recommandations basées sur les achats actuels d'un client.  
  
#### <a name="to-create-a-prediction-query-on-an-association-model"></a>Pour créer une requête de prédiction sur un modèle d'association  
  
1.  Cliquez sur le **prévision de modèle d’exploration de données** onglet du Concepteur d’exploration de données.  
  
2.  Dans le **Mining Model** volet, cliquez sur **sélectionner un modèle**. (Vous pouvez ignorer cette étape et l'étape suivante si le modèle correct est déjà sélectionné.)  
  
3.  Dans le **sélectionner un modèle d’exploration de données** boîte de dialogue, développez le nœud qui représente la structure d’exploration de données **Association**, puis sélectionnez le modèle **Association**. Cliquez sur **OK**.  
  
     Pour le moment, vous pouvez ignorer le volet d'entrée.  
  
4.  Dans la grille, cliquez sur la cellule vide sous **Source** et sélectionnez **fonction de prédiction.** Dans la cellule sous **champ**, sélectionnez `PredictAssociation`.  
  
     Vous pouvez également utiliser le **Predict** fonction permettant de prédire des associations. Si vous fassiez, veillez à choisir la version de la **Predict** fonction qui prend une colonne de table comme argument.  
  
5.  Dans le **Mining Model** volet, sélectionnez la table imbriquée `vAssocSeqLineItems`et faites-le glisser dans la grille, à la **critères/Argument** zone pour le `PredictAssociation` (fonction).  
  
     Le déplacement des noms de table et de colonne vous permet de générer des instructions complexes sans commettre d'erreur de syntaxe. Toutefois, cette opération remplace le contenu actuel de la cellule, qui inclut d’autres arguments facultatifs pour le `PredictAssociation` (fonction). Pour consulter les autres arguments, vous pouvez ajouter temporairement une deuxième instance de la fonction à la grille pour référence.  
  
6.  Cliquez sur le **critères/Argument** puis tapez le texte suivant après le nom de table : `,3`  
  
     Le texte complet dans le **critères/Argument** boîte doit se présenter comme suit :  
  
     `[Association].[v Assoc Seq Line Items],3`  
  
7.  Cliquez sur le **résultats** bouton dans le coin supérieur du Générateur de requêtes de prédiction.  
  
 Les résultats attendus contiennent une seule colonne avec l’en-tête **Expression**. Le **Expression** colonne contient une table imbriquée avec une seule colonne et les trois lignes suivantes. Étant donné que vous n'avez pas spécifié de valeur d'entrée, ces prédictions représentent les associations de produits les plus probables pour le modèle dans son ensemble.  
  
|Modèle|  
|-----------|  
|Women's Mountain Shorts|  
|Water Bottle|  
|Touring-3000|  
  
 Ensuite, vous allez utiliser le **entrée de requête Singleton** volet pour spécifier un produit en tant qu’entrée à la requête et afficher les produits qui sont probables associé à cet élément.  
  
#### <a name="to-create-a-singleton-prediction-query-with-nested-table-inputs"></a>Pour créer une requête singleton de prédiction avec des entrées de table imbriquée  
  
1.  Cliquez sur le **conception** bouton dans l’angle du Générateur de requêtes de prédiction pour revenir à la grille de création de requête.  
  
2.  Sur le **Mining Model** menu, sélectionnez **requête Singleton**.  
  
3.  Dans le **Mining Model** boîte de dialogue, sélectionnez le **Association** modèle.  
  
4.  Dans la grille, cliquez sur la cellule vide sous **Source** et sélectionnez **fonction de prédiction.** Dans la cellule sous **champ**, sélectionnez `PredictAssociation`.  
  
5.  Dans le **Mining Model** volet, sélectionnez la table imbriquée `vAssocSeqLineItems`et faites-le glisser dans la grille, à la **critères/Argument** zone pour le `PredictAssociation` (fonction). Type `,3` après le nom de table imbriquée comme dans la procédure précédente.  
  
6.  Dans le **entrée de requête Singleton** boîte de dialogue, cliquez sur le **valeur** zone située en regard **Vassocseqlineitems**, puis cliquez sur le **(...)**  bouton.  
  
7.  Dans le **entrée de la Table imbriquée** boîte de dialogue, sélectionnez `Touring Tire` dans le **colonne clé** volet, puis cliquez sur **ajouter**.  
  
8.  Cliquez sur le **résultats** bouton.  
  
 Les résultats affichent maintenant les prédictions pour les produits les plus probablement associés à Touring Tire.  
  
|Modèle|  
|-----------|  
|Touring Tire Tube (Pneu pour vélo de tourisme)|  
|Sport-100|  
|Water Bottle|  
  
 Toutefois, vous savez déjà de l'exploration du modèle que le produit Touring Tire Tube est souvent acheté avec le produit Touring Tire ; vous souhaitez plus savoir quels produits vous pouvez recommander aux clients qui achètent ces articles ensemble. Vous allez modifier la requête afin qu'elle prédise les produits associés en fonction des deux articles contenus dans le panier. Vous allez également modifier la requête afin d'ajouter la probabilité de chaque produit prédit.  
  
#### <a name="to-add-inputs-and-probabilities-to-the-singleton-prediction-query"></a>Pour ajouter des entrées et des probabilités à la requête singleton de prédiction  
  
1.  Cliquez sur le **conception** bouton dans l’angle du Générateur de requêtes de prédiction pour revenir à la grille de création de requête.  
  
2.  Dans le **entrée de requête Singleton** boîte de dialogue, cliquez sur le **valeur** zone située en regard **Vassocseqlineitems**, puis cliquez sur le **(...)**  bouton.  
  
3.  Dans le **colonne clé** volet, sélectionnez `Touring Tire`, puis cliquez sur **ajouter**.  
  
4.  Dans la grille, cliquez sur la cellule vide sous **Source** et sélectionnez **fonction de prédiction.** Dans la cellule sous **champ**, sélectionnez `PredictAssociation`.  
  
5.  Dans le **Mining Model** volet, sélectionnez la table imbriquée `vAssocSeqLineItems`et faites-le glisser dans la grille, à la **critères/Argument** zone pour le `PredictAssociation` (fonction). Type `,3` après le nom de table imbriquée comme dans la procédure précédente.  
  
6.  Dans le **entrée de la Table imbriquée** boîte de dialogue, sélectionnez `Touring Tire Tube` dans le **colonne clé** volet, puis cliquez sur **ajouter**.  
  
7.  Dans la grille, dans la ligne de la `PredictAssociation` de fonction, cliquez sur le **critères/Argument** , puis modifiez les arguments pour ajouter l’argument INCLUDE_STATISTICS.  
  
     Le texte complet dans le **critères/Argument** boîte doit se présenter comme suit :  
  
     `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`  
  
8.  Cliquez sur le **résultats** bouton.  
  
 Les résultats indiqués dans la table imbriquée se modifient à présent afin de présenter les prédictions, avec la prise en charge et la probabilité. Pour plus d’informations sur l’interprétation de ces valeurs, consultez [modèle d’exploration de données contenu pour les modèles d’Association &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).  
  
|Modèle|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291...|0.252...|  
|Water Bottle|2866|0.192...|0.175...|  
|Patch Kit|2113|0.142...|0.132|  
  
## <a name="working-with-results"></a>Utilisation des résultats  
 En présence d'un grand nombre de tables imbriquées dans les résultats, vous pouvez aplatir les résultats pour faciliter leur affichage. Pour cela, vous pouvez modifier la requête manuellement et ajouter le mot clé `FLATTENED`.  
  
#### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a>Pour aplatir des ensembles de lignes imbriqués dans une requête de prédiction  
  
1.  Cliquez sur le **SQL** bouton dans l’angle du Générateur de requêtes de prédiction.  
  
     La grille se transforme en un volet ouvert où vous pouvez afficher et modifier l'instruction DMX créée par le Générateur de requêtes de prédiction.  
  
2.  Après le mot clé `SELECT`, tapez `FLATTENED`.  
  
     Le texte complet de la requête doit se présenter comme suit :  
  
    ```  
    SELECT FLATTENED  
      PredictAssociation([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,3)  
    FROM  
      [Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Touring Tire' AS [Model]  
      UNION SELECT 'Touring Tire Tube' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
    ```  
  
3.  Cliquez sur le **résultats** bouton dans le coin supérieur du Générateur de requêtes de prédiction.  
  
 Notez qu'après avoir modifié une requête manuellement, vous ne pouvez pas revenir en mode Conception sans perdre les modifications. Si vous souhaitez enregistrer la requête, vous pouvez copier l'instruction DMX que vous avez créée manuellement dans un fichier texte. Lorsque vous revenez en mode Conception, la requête est restaurée à la dernière version qui était valide en mode Conception.  
  
## <a name="creating-multiple-predictions"></a>Création de plusieurs prédictions  
 Supposons que vous souhaitez déterminer les meilleures prédictions pour des clients individuels, en fonction de leurs achats passés. Vous pouvez utiliser des données externes en tant qu'entrée de la requête de prédiction, notamment des tables contenant l'ID du client et ses achats les plus récents. Les conditions requises impliquent que les tables de données soient déjà définies comme une vue de source de données Analysis Services. De plus, les données d'entrée doivent contenir des tables de cas et des tables imbriquées comme celles utilisées dans le modèle. Elles ne doivent pas porter les mêmes noms, mais la structure doit être similaire. Dans le cadre de ce didacticiel, vous allez utiliser les tables d'origine sur lesquelles l'apprentissage du modèle a été effectué.  
  
#### <a name="to-change-the-input-method-for-the-prediction-query"></a>Pour modifier la méthode d'entrée pour la requête de prédiction  
  
1.  Dans le **Mining Model** menu, sélectionnez **requête Singleton** là encore, désactivez la case à cocher.  
  
2.  Un message d'erreur apparaît et stipule que votre requête singleton sera perdue. Cliquez sur **Oui**.  
  
     Le nom de la boîte de dialogue d’entrée devient **sélectionner une ou plusieurs tables d’entrée**.  
  
 Comme vous souhaitez créer une requête de prédiction qui fournit l'ID du client et une liste des produits comme entrée, vous ajouterez la table des clients comme table de cas, et la table des achats comme table imbriquée. Ensuite, vous ajouterez des fonctions de prédiction pour créer des recommandations.  
  
#### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a>Pour créer une requête de prédiction à l'aide d'entrées de table imbriquée  
  
1.  Dans le volet Modèle d'exploration de données, sélectionnez le modèle Association avec filtre.  
  
2.  Dans le **sélectionner une ou plusieurs tables d’entrée** boîte de dialogue, cliquez sur **sélectionner la Table de cas**.  
  
3.  Dans le **sélectionner une Table** boîte de dialogue pour **Source de données**, sélectionnez AdventureWorksDW2008. Dans le **nom de la Table/vue** liste, sélectionnez vAssocSeqOrders, puis cliquez sur **OK**.  
  
     La table vAssocSeqOrders s'ajoute au volet.  
  
4.  Dans le **sélectionner une ou plusieurs tables d’entrée** boîte de dialogue, cliquez sur **sélectionner la Table imbriquée**.  
  
5.  Dans le **sélectionner une Table** boîte de dialogue pour **Source de données**, sélectionnez AdventureWorksDW2008. Dans le **nom de la Table/vue** liste, sélectionnez vAssocSeqLineItems, puis cliquez sur **OK**.  
  
     La table vAssocSeqLineItems s'ajoute au volet.  
  
6.  Dans le **spécifier la jointure imbriquée** boîte de dialogue, faites glisser le OrderNumber champ à partir de la table de cas et déposez-le sur le champ OrderNumber de la table imbriquée.  
  
     Vous pouvez également cliquer sur **ajouter une relation** et créer la relation en sélectionnant des colonnes dans une liste.  
  
7.  Dans le **spécifier une relation** boîte de dialogue, vérifiez que les champs OrderNumber sont correctement mappés, puis cliquez sur **OK**.  
  
8.  Cliquez sur **OK** pour fermer la **spécifier la jointure imbriquée** boîte de dialogue.  
  
     Les tables de cas et imbriquées sont mises à jour dans le volet de conception pour montrer les jointures qui relient les colonnes de données externes aux colonnes du modèle. Si les relations sont incorrectes, vous pouvez cliquez sur la ligne de jointure et sélectionner **modifier les connexions** pour modifier la colonne de mappage, ou vous pouvez avec le bouton droit de la ligne de jointure et sélectionner **supprimer** pour supprimer le relation complètement.  
  
9. Ajoutez une nouvelle ligne à la grille. Pour **Source**, sélectionnez **table vAssocSeqOrders**. Pour **champ**, sélectionnez CustomerKey.  
  
10. Ajoutez une nouvelle ligne à la grille. Pour **Source**, sélectionnez **table vAssocSeqOrders**. Pour **champ**, sélectionnez la région.  
  
11. Ajoutez une nouvelle ligne à la grille. Pour **Source**, sélectionnez **fonction de prédiction**et pour **champ**, sélectionnez `PredictAssociation`.  
  
12. Faites glisser vAssocSeqLineItems dans la **critères/Argument** boîte de le `PredictAssociation` ligne. Cliquez sur à la fin de la **critères/Argument** puis puis tapez le texte suivant : `INCLUDE_STATISTICS,3`  
  
     Le texte complet dans le **critères/Argument** case doit être : `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`  
  
13. Cliquez sur le **résultat** bouton pour afficher les prédictions pour chaque client.  
  
 Vous pouvez essayer de créer une requête de prédiction similaire sur les multiples modèles, pour déterminer si le filtrage modifie les résultats de la prédiction. Pour plus d’informations sur la création des prédictions et autres types de requêtes, consultez [Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contenu du modèle d’exploration de données pour les modèles d’association &#40;Analysis Services - Exploration de données&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)   
 [PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx)   
 [Créer une requête de prédiction à l’aide du Générateur de requêtes de prédiction](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
