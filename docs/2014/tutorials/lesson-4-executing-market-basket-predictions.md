---
title: 'Leçon 4 : Exécution de prédictions Market Basket | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: b3238f1b-ea04-4253-ade2-838a806b62fe
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6db486a5d497ba6b6c5bfe312197d78a5656d388
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177493"
---
# <a name="lesson-4-executing-market-basket-predictions"></a>Leçon 4 : Exécution de prédictions Market Basket
  Dans cette leçon, vous allez utiliser l’instruction DMX `SELECT` instruction pour créer des prédictions basées sur l’association des modèles que vous avez créé dans [leçon 2 : ajout de modèles d’exploration de données à la Structure d’exploration de données Market Basket](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md). Une requête de prédiction est créée en utilisant l'instruction DMX `SELECT` et en ajoutant une clause `PREDICTION JOIN` Pour plus d’informations sur la syntaxe d’une jointure de prédiction, consultez [SELECT FROM &#60;modèle&#62; jointure de prédiction &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx).  
  
 Le **SELECT FROM \<modèle > PREDICTION JOIN** formulaire de la `SELECT` instruction composé de trois parties :  
  
-   Liste des colonnes du modèle d'exploration de données et des fonctions de prédiction renvoyées dans l'ensemble de résultats. Cette liste peut également contenir les colonnes d'entrée issues des données source.  
  
-   Requête source qui définit les données utilisées pour créer une prédiction. Par exemple, si vous créez de nombreuses prédictions dans un lot, la requête source pourrait extraire une liste de clients.  
  
-   Mappage entre les colonnes du modèle d'exploration de données et les données source. Si les noms des colonnes correspondent, vous pouvez utiliser la syntaxe `NATURAL PREDICTION JOIN` et omettre les mappages de colonnes.  
  
 Vous pouvez affiner la requête à l'aide de fonctions de prédiction. Les fonctions de prédiction fournissent des informations supplémentaires, notamment la probabilité d'une prédiction, ou offrent la prise en charge d'une prédiction dans le dataset d'apprentissage. Pour plus d’informations sur les fonctions de prédiction, consultez [fonctions &#40;DMX&#41;](/sql/dmx/functions-dmx).  
  
 Vous pouvez également faire appel au générateur de requêtes de prédiction disponible dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer des requêtes de prédiction.  
  
## <a name="singleton-prediction-join-statement"></a>Instruction singleton PREDICTION JOIN  
 La première étape consiste à créer une requête singleton, à l’aide de la **SELECT FROM \<modèle > PREDICTION JOIN** syntaxe et en fournissant un ensemble unique de valeurs en tant qu’entrée. L'exemple générique suivant utilise l'instruction singleton :  
  
```  
SELECT <select list>  
    FROM [<mining model>]   
[NATURAL] PREDICTION JOIN  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
AS [<input alias>]  
```  
  
 La première ligne du code définit les colonnes du modèle d'exploration de données que retourne la requête et spécifie le nom du modèle d'exploration utilisé pour générer la prédiction :  
  
```  
SELECT <select list> FROM [<mining model>]   
```  
  
 La ligne suivante du code indique l'opération à effectuer. Étant donné que vous spécifierez des valeurs pour chacune des colonnes et que vous taperez les noms de colonnes exactement pour qu'ils correspondent au modèle, vous pouvez utiliser la syntaxe `NATURAL PREDICTION JOIN`. Toutefois, si les noms de colonne étaient différents, il vous faudra spécifier des mappages entre les colonnes dans le modèle et les colonnes dans les nouvelles données en ajoutant une clause `ON`.  
  
```  
[NATURAL] PREDICTION JOIN  
```  
  
 Les lignes suivantes du code définissent les produits du panier d'achat à utiliser pour prédire d'autres produits ajoutés par un client :  
  
```  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
```  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Vous allez effectuer les tâches suivantes dans cette leçon :  
  
-   Créer une requête qui prédit les autres éléments, un client est susceptible d’acheter, en fonction des éléments existants dans leur panier d’achat. Vous allez créer cette requête en utilisant le modèle d’exploration de données avec la valeur par défaut *MINIMUM_PROBABILITY*.  
  
-   créer une requête pour prédire quels autres articles un client est susceptible d'acheter, en vous basant sur des articles déjà présents dans son panier d'achat. Cette requête est basée sur un modèle différent, dans lequel *MINIMUM_PROBABILITY* a été défini sur 0.01. Étant donné que la valeur par défaut pour *MINIMUM_PROBABILITY* dans les modèles d’association étant égale à 0.3, la requête sur ce modèle doit retourner davantage d’éléments possibles que la requête sur le modèle par défaut.  
  
## <a name="create-a-prediction-by-using-a-model-with-the-default-minimumprobability"></a>Création d'une prédiction à l'aide d'un modèle avec le paramètre MINIMUM_PROBABILITY par défaut  
  
#### <a name="to-create-an-association-query"></a>Pour créer une requête Association  
  
1.  Dans **Explorateur d’objets**, avec le bouton droit de l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], pointez sur **nouvelle requête**, puis cliquez sur **DMX** pour ouvrir l’éditeur de requête.  
  
2.  Copiez l'exemple générique de l'instruction `PREDICTION JOIN` dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <select list>   
    ```  
  
     par :  
  
    ```  
    PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
     Vous pourriez inclure le nom de colonne [Products], mais à l’aide de la [Predict &#40;DMX&#41; ](/sql/dmx/predict-dmx) (fonction), vous pouvez limiter le nombre de produits qui sont retournées par l’algorithme à trois. Vous pouvez également utiliser l'instruction `INCLUDE_STATISTICS` pour vous procurer des informations supplémentaires sur chaque produit, notamment sur la prise en charge, la probabilité et la probabilité ajustée. Ces statistiques vous aident à évaluer la précision de la prédiction.  
  
4.  Remplacez le code suivant :  
  
    ```  
    [<mining model>]   
    ```  
  
     par :  
  
    ```  
    [Default Association]  
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     par :  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     Cette instruction utilise l'instruction `UNION` pour spécifier trois produits à inclure dans le panier d'achat avec les produits prédits. La colonne Model dans l'instruction `SELECT` correspond à la colonne de modèle figurant dans la table imbriquée des produits.  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    SELECT  
      PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Default Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  Sur le **fichier** menu, cliquez sur **enregistrer DMXQuery1.dmx sous**.  
  
7.  Dans le **enregistrer en tant que** boîte de dialogue, accédez au dossier approprié et nommez le fichier `Association Prediction.dmx`.  
  
8.  Dans la barre d’outils, cliquez sur le **Execute** bouton.  
  
     La requête retourne une table qui contient trois produits : HL Mountain Tire, Fender Set – Mountain et ML Mountain Tire. La table répertorie ces produits retournés par ordre de probabilité. Le produit retourné le plus susceptible d'être inclus dans le même panier d'achat que les trois produits spécifiés dans la requête apparaît en haut de la table. Les deux produits qui suivent sont les produits suivants les plus susceptibles d'être inclus dans le panier d'achat. La table renferme également des statistiques indiquant la précision de la prédiction.  
  
## <a name="create-a-prediction-by-using-a-model-with-a-minimumprobability-of-001"></a>Création d'une prédiction à l'aide d'un modèle avec un paramètre MINIMUM_PROBABILITY de 0.01  
  
#### <a name="to-create-an-association-query"></a>Pour créer une requête Association  
  
1.  Dans **Explorateur d’objets**, avec le bouton droit de l’instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], pointez sur **nouvelle requête**, puis cliquez sur **DMX** pour ouvrir l’éditeur de requête.  
  
2.  Copiez l'exemple générique de l'instruction `PREDICTION JOIN` dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <select list>   
    ```  
  
     par :  
  
    ```  
    PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
4.  Remplacez le code suivant :  
  
    ```  
    [<mining model>]   
    ```  
  
     par :  
  
    ```  
    [Modified Association]  
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     par :  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     Cette instruction utilise l'instruction `UNION` pour spécifier trois produits à inclure dans le panier d'achat avec les produits prédits. La colonne `[Model]` dans l'instruction `SELECT` correspond à la colonne figurant dans la table imbriquée des produits.  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    SELECT  
      PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Modified Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  Sur le **fichier** menu, cliquez sur **enregistrer DMXQuery1.dmx sous**.  
  
7.  Dans le **enregistrer en tant que** boîte de dialogue, accédez au dossier approprié et nommez le fichier `Modified Association Prediction.dmx`.  
  
8.  Dans la barre d’outils, cliquez sur le **Execute** bouton.  
  
     La requête retourne une table qui contient trois produits : HL Mountain Tire, Water Bottle et Fender Set – Mountain. La table répertorie ces produits par ordre de probabilité. Le produit affiché en haut de la table est le produit le plus susceptible d'être inclus dans le même panier d'achat que les trois produits spécifiés dans la requête. Les produits restants sont les produits suivants les plus susceptibles d'être inclus dans le panier d'achat. La table renferme également des statistiques qui indiquent la précision de la prédiction.  
  
     Vous pouvez le voir dans les résultats de cette requête que la valeur de la *MINIMUM_PROBABILITY* paramètre affecte les résultats retournés par la requête.  
  
 C'est la dernière étape du didacticiel Market Basket. Vous disposez à présent d'un ensemble de modèles à l'aide desquels il vous est possible de prévoir les produits que les clients sont susceptibles d'acheter en même temps.  
  
 Pour savoir comment utiliser DMX dans un autre scénario prédictif, consultez [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes de modèle association](../../2014/analysis-services/data-mining/association-model-query-examples.md)   
 [Interface de requête d’exploration de données](../../2014/analysis-services/data-mining/data-mining-query-tools.md)  
  
  
