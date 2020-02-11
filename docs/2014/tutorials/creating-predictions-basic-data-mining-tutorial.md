---
title: Création de prédictions (didacticiel sur l’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a8410ed2-bb98-4d51-a9eb-b239be1201c2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 456aec6c6b9d0d1a5d0ee1d9949507a37577130c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67597529"
---
# <a name="creating-predictions-basic-data-mining-tutorial"></a>Création de prédictions (Didacticiel sur l'exploration de données de base)
  Une fois que vous avez testé la précision de vos modèles d’exploration de données et décidé que vous êtes satisfait des résultats, vous pouvez générer des prédictions à l’aide de la Générateur de requêtes de prédiction sous l’onglet **prédiction de modèle d’exploration** de données du concepteur d’exploration de données.  
  
 Le Générateur de requêtes de prédiction a trois vues. Avec les vues de **conception** et de **requête** , vous pouvez générer et examiner votre requête. Vous pouvez ensuite exécuter la requête et afficher les résultats dans l' **affichage des résultats.**  
  
 Toutes les requêtes de prédictions utilisent DMX, qui est l'abréviation du langage Data Mining Extensions (DMX). DMX a une syntaxe similaire à celle de T-SQL mais est utilisée pour des requêtes sur des objets d'exploration de données. Bien que la syntaxe DMX ne soit pas compliquée, l’utilisation d’un générateur de requêtes comme celui-ci, ou celle des [compléments d’exploration de données SQL Server pour Office](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md), facilite grandement la sélection des entrées et la création d’expressions. nous vous recommandons donc vivement d’apprendre les principes de base.  
  
## <a name="creating-the-query"></a>Création de la requête  
 La première étape dans la création d'une requête de prédiction consiste à sélectionner un modèle d'exploration de données et une table d'entrée.  
  
#### <a name="to-select-a-model-and-input-table"></a>Pour sélectionner un modèle et une table d'entrée  
  
1.  Sous l’onglet **prédiction de modèle d’exploration** de données du concepteur d’exploration de données, dans la zone modèle d' **exploration** de données, cliquez sur **Sélectionner un modèle**.  
  
2.  Dans la boîte de dialogue **Sélectionner le modèle d’exploration de données** , parcourez l’arborescence jusqu’à la structure de `TM_Decision_Tree` **publipostage ciblée** , développez la structure, sélectionnez, puis cliquez sur **OK**.  
  
3.  Dans la zone **Sélectionner une ou plusieurs tables d’entrée** , cliquez sur **Sélectionner la table de cas**.  
  
4.  Dans la boîte de dialogue **Sélectionner une table** , dans la liste **source de données** , sélectionnez la [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]vue de source de données.  
  
5.  Dans **nom de la table/vue**, sélectionnez la table **ProspectiveBuyer (DBO)** , puis cliquez sur **OK**.  
  
     La `ProspectiveBuyer` table ressemble le mieux à la table de cas **vTargetMail** .  
  
## <a name="mapping-the-columns"></a>Mappage des colonnes  
 Une fois la table d'entrée sélectionnée, le Générateur de requêtes de prédiction crée un mappage par défaut entre le modèle d'exploration de données et la table d'entrée en fonction des noms des colonnes. Au moins une colonne de la structure doit correspondre à une colonne dans les données externes.  
  
> [!IMPORTANT]  
>  Les données que vous utilisez pour déterminer la précision des modèles doivent contenir une colonne qui peut être mappée à la colonne prédictible. Si une telle colonne n'existe pas, vous pouvez en créer une avec des valeurs vides, mais elle doit avoir le même type de données que la colonne prédictible.  
  
#### <a name="to-map-the-inputs-to-the-model"></a>Pour mapper les entrées au modèle  
  
1.  Cliquez avec le bouton droit sur les lignes qui connectent la fenêtre du **modèle d’exploration de données** à la fenêtre Sélectionner une **table d’entrée** , puis sélectionnez **modifier les connexions**.  
  
     Vous remarquez que toutes les colonnes ne sont pas mappées. Nous allons ajouter des mappages pour plusieurs **colonnes de table**. Nous allons également générer une nouvelle colonne de date de naissance sur la colonne de date actuelle, afin que les colonnes correspondent mieux.  
  
2.  Sous **colonne de table**, cliquez `Bike Buyer` sur la cellule et sélectionnez ProspectiveBuyer. Unknown dans la liste déroulante.  
  
     Cette action mappe la colonne prédictible, [Bike Buyer], à une colonne de la table d'entrée.  
  
3.  Cliquez sur **OK**.  
  
4.  Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la vue de source de données de **publipostage ciblée** et sélectionnez **Concepteur de vues**.  
  
5.  Cliquez avec le bouton droit sur la table ProspectiveBuyer, puis sélectionnez **nouveau calcul nommé**.  
  
6.  Dans la boîte de dialogue **créer un calcul nommé** , pour **nom**de `calcAge`colonne, tapez.  
  
7.  Pour **Description**, tapez **calculer l’âge en fonction de la date de naissance**.  
  
8.  Dans la zone **expression** , tapez `DATEDIFF(YYYY,[BirthDate],getdate())` , puis cliquez sur **OK**.  
  
     Étant donné que la table d’entrée n’a pas de colonne **Age** qui correspond à celle du modèle, vous pouvez utiliser cette expression pour calculer l’âge du client à partir de la colonne BirthDate de la table d’entrée. Dans la mesure où **Age** a été identifié comme la colonne la plus influente pour la prédiction de l’achat de bicyclettes, il doit exister à la fois dans le modèle et dans la table d’entrée.  
  
9. Dans le concepteur d’exploration de données, sélectionnez l’onglet **prédiction de modèle d’exploration** de données et rouvrez la fenêtre **modifier les connexions** .  
  
10. Sous **colonne de table**, cliquez sur la cellule **Age** et sélectionnez ProspectiveBuyer. recalcing dans la liste déroulante.  
  
    > [!WARNING]  
    >  Si vous ne voyez pas la colonne dans la liste, vous devrez peut-être actualiser la définition de la vue de source de données chargée dans le concepteur. Pour ce faire, dans le menu **fichier** , sélectionnez **enregistrer tout**, puis fermez et rouvrez le projet dans le concepteur.  
  
11. Cliquez sur **OK**.  
  
## <a name="designing-the-prediction-query"></a>Conception de la requête de prédiction  
  
1.  Le premier bouton de la barre d’outils de l’onglet **prédiction de modèle d’exploration de données** est le bouton **basculer en mode création/basculer vers la vue résultat/basculer vers la vue requête** . Cliquez sur la flèche vers le bas de ce bouton, puis sélectionnez **conception**.  
  
2.  Dans la grille de l’onglet **prédiction de modèle d’exploration de données** , cliquez sur la cellule de la première ligne vide de la colonne **source** , puis sélectionnez **fonction de prédiction**.  
  
3.  Dans la ligne **fonction de prédiction** , dans la colonne **champ** , `PredictProbability`sélectionnez.  
  
     Dans la colonne **alias** de la même ligne, tapez **probabilité de résultat**.  
  
4.  Dans la fenêtre **modèle d’exploration de données** ci-dessus, sélectionnez et faites glisser [Bike Buyer] dans la cellule **Criteria/argument** .  
  
     Lorsque vous relâchez, [TM_Decision_Tree]. [Vélo Buyer] s’affiche dans la cellule **critères/argument** .  
  
     Ceci permet de spécifier la colonne cible pour la fonction `PredictProbability`. Pour plus d’informations sur les fonctions, consultez [Data Mining Extensions &#40;DMX&#41; Function Reference](/sql/dmx/data-mining-extensions-dmx-function-reference).  
  
5.  Cliquez sur la ligne vide suivante dans la colonne **source** , puis sélectionnez **TM_Decision_Tree** modèle d’exploration de données.  
  
6.  Dans la `TM_Decision_Tree` ligne, dans la colonne **champ** , sélectionnez `Bike Buyer`.  
  
7.  Dans la `TM_Decision_Tree` ligne, dans la colonne **critères/argument** , tapez `=1`.  
  
8.  Cliquez sur la ligne vide suivante dans la colonne **source** , puis sélectionnez la **table ProspectiveBuyer**.  
  
9. Dans la `ProspectiveBuyer` ligne, dans la colonne **champ** , sélectionnez **ProspectiveBuyerKey**.  
  
     Un identificateur unique est ainsi ajouté à la requête de prédiction, lequel vous permet d'identifier les personnes susceptibles ou non d'acheter un vélo.  
  
10. Ajoutez cinq lignes en plus à la grille. Pour chaque ligne, sélectionnez la **table ProspectiveBuyer** comme **source** , puis ajoutez les colonnes suivantes dans les cellules du **champ** :  
  
    -   calcAge  
  
    -   LastName  
  
    -   FirstName  
  
    -   AddressLine1  
  
    -   AddressLine2  
  
 Enfin, exécutez la requête et consultez les résultats.  
  
 Le **Générateur de requêtes de prédiction** comprend également les contrôles suivants :  
  
-   **Afficher** la case à cocher  
  
     Vous permet de supprimer des clauses de la requête sans devoir les supprimer du concepteur. Ceci s'avère utile lorsque vous travaillez avec des requêtes complexes et souhaitez conserver la syntaxe sans devoir copier et coller le DMX dans la fenêtre.  
  
-   **Groupe**  
  
     Insère une parenthèse ouvrante (gauche) au début de la ligne sélectionnée, ou insère une parenthèse fermante (droite) à la fin de la ligne active.  
  
-   **ET/OU**  
  
     Insère l'opérateur `AND` ou l'opérateur `OR` immédiatement après la fonction ou la colonne active.  
  
#### <a name="to-run-the-query-and-view-results"></a>Pour exécuter la requête et afficher les résultats  
  
1.  Sous l’onglet **prédiction de modèle d’exploration de données** , sélectionnez le bouton **résultat** .  
  
2.  Après l'exécution de la requête et l'affichage des résultats, vous pouvez examiner les résultats.  
  
     L’onglet **prédiction de modèle d’exploration** de données affiche les informations de contact des clients potentiels qui sont susceptibles d’être des acheteurs de vélos. La colonne **probabilité de résultat** indique la probabilité que la prédiction soit correcte. Ces résultats peuvent vous aider à déterminer les clients potentiels à cibler pour le publipostage.  
  
3.  À ce stade, vous pouvez enregistrer les résultats. Vous avez le choix entre trois options.  
  
    -   Cliquez avec le bouton droit sur une ligne de données dans les résultats, puis sélectionnez **copier** pour enregistrer uniquement cette valeur (et l’en-tête de colonne) dans le presse-papiers.  
  
    -   Cliquez avec le bouton droit sur une ligne dans les résultats, puis sélectionnez **copier tout** pour copier l’intégralité du jeu de résultats, y compris les en-têtes de colonne, dans le presse-papiers.  
  
    -   Cliquez sur **enregistrer le résultat** de la requête pour enregistrer les résultats directement dans une base de données comme suit :  
  
        1.  Dans la boîte de dialogue Enregistrer le résultat de la **requête d’exploration de données** , sélectionnez une source de données ou définissez une nouvelle source de données.  
  
        2.  Tapez le nom de la table dans laquelle seront enregistrés les résultats de la requête.  
  
        3.  Utilisez l’option **Ajouter à DSV**pour créer la table et l’ajouter à une vue de source de données existante. Cela est utile si vous souhaitez conserver toutes les tables associées pour un modèle, telles que les données d’apprentissage, les données sources de prédiction et les résultats de la requête, dans la même vue de source de données.  
  
        4.  Utilisez l’option **remplacer si Exists**pour mettre à jour une table existante avec les résultats les plus récents.  
  
             Vous devez utiliser l'option permettant de remplacer la table si vous avez ajouté des colonnes à la requête de prédiction, modifié les noms des types de données des colonnes dans la requête de prédiction ou si vous avez exécuté des instructions ALTER sur la table de destination.  
  
             En outre, si plusieurs colonnes portent le même nom (par exemple, l' **expression**de nom de colonne par défaut), vous devez créer un alias pour les colonnes avec des noms dupliqués, ou une erreur est déclenchée lorsque le concepteur tente d’enregistrer les résultats dans SQL Server. En effet, SQL Server n'autorise pas plusieurs colonnes à porter le même nom.  
  
             Pour plus d’informations, consultez [boîte de dialogue Enregistrer le résultat de la requête d’exploration de données &#40;vue prévision de modèle d’exploration de données&#41;](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md).  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Utilisation de l’extraction sur les données de structure &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une requête de prédiction à l’aide du Générateur de requêtes de prédiction](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
