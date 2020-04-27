---
title: 'Leçon 4 : exécution des prédictions du panier de marché | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b3238f1b-ea04-4253-ade2-838a806b62fe
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3b49fc242eb8b2242269c5af33cc094937bbe0de
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63312111"
---
# <a name="lesson-4-executing-market-basket-predictions"></a>Leçon 4 : Exécution de prédictions Market Basket
  Dans cette leçon, vous allez utiliser l’instruction `SELECT` DMX pour créer des prédictions basées sur les modèles d’association que vous avez créés au cours de la [leçon 2 : ajout de modèles d’exploration de données à la structure d’exploration de données Market panier](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md). Une requête de prédiction est créée en utilisant l'instruction DMX `SELECT` et en ajoutant une clause `PREDICTION JOIN` Pour plus d’informations sur la syntaxe d’une jointure de prédiction, consultez [SELECT FROM &#60;model&#62; Prediction join &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx).  
  
 Le formulaire **Select \<from Model> PREDICTION JOIN** de l' `SELECT` instruction contient trois parties :  
  
-   Liste des colonnes du modèle d'exploration de données et des fonctions de prédiction renvoyées dans l'ensemble de résultats. Cette liste peut également contenir les colonnes d'entrée issues des données source.  
  
-   Requête source qui définit les données utilisées pour créer une prédiction. Par exemple, si vous créez de nombreuses prédictions dans un lot, la requête source pourrait extraire une liste de clients.  
  
-   Mappage entre les colonnes du modèle d'exploration de données et les données source. Si les noms des colonnes correspondent, vous pouvez utiliser la syntaxe `NATURAL PREDICTION JOIN` et omettre les mappages de colonnes.  
  
 Vous pouvez affiner la requête à l'aide de fonctions de prédiction. Les fonctions de prédiction fournissent des informations supplémentaires, notamment la probabilité d'une prédiction, ou offrent la prise en charge d'une prédiction dans le dataset d'apprentissage. Pour plus d’informations sur les fonctions de prédiction, consultez [fonctions &#40;DMX&#41;](/sql/dmx/functions-dmx).  
  
 Vous pouvez également faire appel au générateur de requêtes de prédiction disponible dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer des requêtes de prédiction.  
  
## <a name="singleton-prediction-join-statement"></a>Instruction singleton PREDICTION JOIN  
 La première étape consiste à créer une requête singleton, en utilisant la syntaxe **Select \<from Model> PREDICTION JOIN** et en fournissant un ensemble unique de valeurs comme entrée. L'exemple générique suivant utilise l'instruction singleton :  
  
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
 Dans cette leçon, vous allez effectuer les tâches suivantes :  
  
-   Créez une requête qui prédit les autres éléments qu’un client est susceptible d’acheter, en fonction des éléments déjà présents dans le panier. Vous allez créer cette requête à l’aide du modèle d’exploration de données avec le *MINIMUM_PROBABILITY*par défaut.  
  
-   créer une requête pour prédire quels autres articles un client est susceptible d'acheter, en vous basant sur des articles déjà présents dans son panier d'achat. Cette requête est basée sur un modèle différent, dans lequel *MINIMUM_PROBABILITY* a été défini sur 0,01. Étant donné que la valeur par défaut pour *MINIMUM_PROBABILITY* dans les modèles d’association est 0,3, la requête sur ce modèle doit retourner plus d’éléments possibles que la requête sur le modèle par défaut.  
  
## <a name="create-a-prediction-by-using-a-model-with-the-default-minimum_probability"></a>Création d'une prédiction à l'aide d'un modèle avec le paramètre MINIMUM_PROBABILITY par défaut  
  
#### <a name="to-create-an-association-query"></a>Pour créer une requête Association  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]droit sur l’instance de, pointez sur **nouvelle requête**, puis cliquez sur **DMX** pour ouvrir l’éditeur de requête.  
  
2.  Copiez l'exemple générique de l'instruction `PREDICTION JOIN` dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <select list>   
    ```  
  
     par :  
  
    ```  
    PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
     Vous pouvez simplement inclure le nom de colonne [Products], mais à l’aide de la fonction [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) , vous pouvez limiter le nombre de produits retournés par l’algorithme à trois. Vous pouvez également utiliser l'instruction `INCLUDE_STATISTICS` pour vous procurer des informations supplémentaires sur chaque produit, notamment sur la prise en charge, la probabilité et la probabilité ajustée. Ces statistiques vous aident à évaluer la précision de la prédiction.  
  
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
  
6.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
7.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `Association Prediction.dmx`.  
  
8.  Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
     La requête retourne une table qui contient trois produits : HL Mountain Tire, Fender Set – Mountain et ML Mountain Tire. La table répertorie ces produits retournés par ordre de probabilité. Le produit retourné le plus susceptible d'être inclus dans le même panier d'achat que les trois produits spécifiés dans la requête apparaît en haut de la table. Les deux produits qui suivent sont les produits suivants les plus susceptibles d'être inclus dans le panier d'achat. La table renferme également des statistiques indiquant la précision de la prédiction.  
  
## <a name="create-a-prediction-by-using-a-model-with-a-minimum_probability-of-001"></a>Création d'une prédiction à l'aide d'un modèle avec un paramètre MINIMUM_PROBABILITY de 0.01  
  
#### <a name="to-create-an-association-query"></a>Pour créer une requête Association  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]droit sur l’instance de, pointez sur **nouvelle requête**, puis cliquez sur **DMX** pour ouvrir l’éditeur de requête.  
  
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
  
6.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
7.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `Modified Association Prediction.dmx`.  
  
8.  Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
     La requête retourne une table qui contient trois produits : HL Mountain Tire, Water Bottle et Fender Set – Mountain. La table répertorie ces produits par ordre de probabilité. Le produit affiché en haut de la table est le produit le plus susceptible d'être inclus dans le même panier d'achat que les trois produits spécifiés dans la requête. Les produits restants sont les produits suivants les plus susceptibles d'être inclus dans le panier d'achat. La table renferme également des statistiques qui indiquent la précision de la prédiction.  
  
     Vous pouvez voir à partir des résultats de cette requête que la valeur du paramètre *MINIMUM_PROBABILITY* affecte les résultats retournés par la requête.  
  
 C'est la dernière étape du didacticiel Market Basket. Vous disposez à présent d'un ensemble de modèles à l'aide desquels il vous est possible de prévoir les produits que les clients sont susceptibles d'acheter en même temps.  
  
 Pour en savoir plus sur l’utilisation de DMX dans un autre scénario prédictif, consultez le [didacticiel DMX Buyer](../../2014/tutorials/bike-buyer-dmx-tutorial.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes de modèle d’association](../../2014/analysis-services/data-mining/association-model-query-examples.md)   
 [Interface de requête d'exploration de données](../../2014/analysis-services/data-mining/data-mining-query-tools.md)  
  
  
