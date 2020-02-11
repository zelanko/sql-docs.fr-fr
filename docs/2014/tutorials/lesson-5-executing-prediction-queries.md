---
title: 'Leçon 5 : exécution des requêtes de prédiction | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0037bd2f-aa2d-464b-bf86-b0210f0438b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a5f4d6dd79f62541e207df688349f694680e2421
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62822311"
---
# <a name="lesson-5-executing-prediction-queries"></a>Leçon 5 : exécution des requêtes de prédiction
  Dans cette leçon, vous allez utiliser la forme [Select \<from Model> PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) de l’instruction SELECT pour créer deux types de prédictions différents en fonction du modèle d’arbre de décision que vous avez créé au cours de la [leçon 2 : ajout de modèles d’exploration de données à la structure d’exploration de données d’association](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md). Ces types de prédiction sont définis ci-dessous.  
  
 Requête singleton  
 Utilisez une requête singleton pour fournir les valeurs appropriées lors des prédictions. Par exemple, vous pouvez déterminer si un client est susceptible d'acheter un vélo, en intégrant dans la requête des entrées telles que la distance domicile-travail, le code postal ou le nombre d'enfants du client. La requête singleton renvoie une valeur qui indique la probabilité que la personne achète un vélo en fonction de ces entrées.  
  
 Requête par lot  
 Optez pour une requête par lot si vous souhaitez déterminer qui, dans une liste de clients potentiels, est susceptible d'acheter un vélo. Par exemple, si votre service marketing vous communique une liste de clients et d'attributs de clients, vous pouvez alors procéder à une prédiction par lot pour évaluer qui dans la liste des clients est un acheteur de vélo potentiel.  
  
 La forme [Select \<from Model> PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) de l’instruction SELECT contient trois parties :  
  
-   Liste des colonnes du modèle d'exploration de données et des fonctions de prédiction retournées dans les résultats. Ces résultats peuvent également contenir les colonnes d'entrée issues des données sources.  
  
-   Requête source définissant les données utilisées pour créer une prédiction. Par exemple, dans le cadre d'une requête par lot, il peut s'agir d'une liste de clients.  
  
-   Mappage entre les colonnes du modèle d'exploration de données et les données source. Si les noms correspondent, vous pouvez alors adopter la syntaxe NATURAL et ignorer les mappages de colonnes.  
  
 Vous pouvez davantage affiner la requête à l'aide de fonctions de prédiction. Les fonctions de prédiction fournissent des informations supplémentaires, notamment la probabilité d'une prédiction, et offrent une prise en charge de la prédiction dans le dataset d'apprentissage. Pour plus d’informations sur les fonctions de prédiction, consultez [fonctions &#40;DMX&#41;](/sql/dmx/functions-dmx).  
  
 Les prédictions de ce didacticiel sont fondées sur la table ProspectiveBuyer de l'exemple de base de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]. La table ProspectiveBuyer renferme une liste de clients potentiels et de leurs caractéristiques associées. Les clients de cette table sont indépendants des clients avec lesquels le modèle d'exploration de données d'arbre de décision a été créé.  
  
 Vous pouvez également créer des prédictions à l'aide du générateur de requêtes de prédiction disponible dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="lesson-tasks"></a>Tâches de la leçon  
 Dans cette leçon, vous allez effectuer les tâches suivantes :  
  
-   Créez une requête singleton pour déterminer si un client donné est susceptible d'acheter un vélo.  
  
-   Créez une requête par lot pour déterminer qui, dans une liste de clients potentiels, est susceptible d'acheter un vélo.  
  
## <a name="singleton-query"></a>Requête singleton  
 La première étape consiste à utiliser le [modèle SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) dans une requête de prédiction Singleton. L'exemple générique suivant utilise l'instruction singleton :  
  
```  
SELECT <select list> FROM [<mining model name>]   
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
```  
  
 La première ligne du code définit les colonnes du modèle d'exploration de données que doit retourner la requête et spécifie le nom du modèle d'exploration de données utilisé pour générer la prédiction :  
  
```  
SELECT <select list> FROM [<mining model name>]   
```  
  
 Les lignes suivantes du code définissent les caractéristiques du client avec lequel vous avez généré une prédiction :  
  
```  
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
ORDER BY <expression>  
```  
  
 Si vous spécifiez NATURAL PREDICTION JOIN, le serveur fait correspondre chaque colonne du modèle avec une colonne d'entrée en se basant sur les noms des colonnes. Si les noms des colonnes ne correspondent pas, les colonnes sont ignorées.  
  
#### <a name="to-create-a-singleton-prediction-query"></a>Pour créer une requête de prédiction singleton  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]droit sur l’instance de, pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
2.  Copiez l'exemple générique de l'instruction singleton dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <select list>   
    ```  
  
     par :  
  
    ```  
    [Bike Buyer] AS Buyer, PredictHistogram([Bike Buyer]) AS Statistics  
    ```  
  
     L'instruction AS est employée pour créer des alias pour les colonnes retournées par la requête. La fonction [PredictHistogram](/sql/dmx/predicthistogram-dmx) retourne des statistiques sur la prédiction, notamment la probabilité et la prise en charge. Pour plus d’informations sur les fonctions qui peuvent être utilisées dans une instruction de prédiction, consultez [fonctions &#40;DMX&#41;](/sql/dmx/functions-dmx).  
  
4.  Remplacez le code suivant :  
  
    ```  
    [<mining model>]   
    ```  
  
     par :  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  Remplacez le code suivant :  
  
    ```  
    (SELECT '<value>' AS [<column name>], ...)  AS t  
    ```  
  
     par :  
  
    ```  
    (SELECT 35 AS [Age],  
      '5-10 Miles' AS [Commute Distance],  
      '1' AS [House Owner Flag],  
      2 AS [Number Cars Owned],  
      2 AS [Total Children]) AS t  
    ```  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    SELECT  
       [Bike Buyer] AS Buyer,  
       PredictHistogram([Bike Buyer]) AS Statistics  
    FROM  
       [Decision Tree]  
    NATURAL PREDICTION JOIN  
    (SELECT 35 AS [Age],  
       '5-10 Miles' AS [Commute Distance],  
       '1' AS [House Owner Flag],  
       2 AS [Number Cars Owned],  
       2 AS [Total Children]) AS t  
    ```  
  
6.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
7.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `Singleton_Query.dmx`.  
  
8.  Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
     La requête retourne une prédiction indiquant dans quelle mesure un client avec les caractéristiques précisées est susceptible d'acheter un vélo, ainsi que des statistiques sur cette prédiction.  
  
## <a name="batch-query"></a>Requête par lot  
 L’étape suivante consiste à utiliser le [modèle SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) dans une requête de prédiction par lot. L'exemple générique suivant utilise une instruction par lot :  
  
```  
SELECT TOP <number> <select list>   
FROM [<mining model name>]  
PREDICTION JOIN  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
ON <on clause, mapping,>  
WHERE <where clause, boolean expression,>  
ORDER BY <expression>  
```  
  
 Tout comme dans la requête singleton, les deux premières lignes du code définissent les colonnes du modèle d'exploration de données que retourne la requête, ainsi que le nom du modèle d'exploration utilisé pour générer la prédiction. L’instruction \<TOP Number> spécifie que la requête retourne uniquement le nombre ou les résultats spécifiés \<par le nombre>.  
  
 Les lignes suivantes du code définissent les données source sur lesquelles les prédictions sont fondées :  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
```  
  
 Vous disposez de plusieurs options pour la méthode d'extraction des données source mais, dans ce didacticiel, vous utiliserez OPENQUERY. Pour plus d’informations sur les options disponibles, consultez [&#60;&#62;de requête de données source ](/sql/dmx/source-data-query).  
  
 La ligne suivante définit le mappage entre les colonnes source du modèle d'exploration et les colonnes des données source :  
  
```  
ON <column mappings>  
```  
  
 La clause WHERE filtre les résultats retournés par la requête de prédiction :  
  
```  
WHERE <where clause, boolean expression,>  
```  
  
 La dernière ligne du code, qui est facultative, précise la colonne selon laquelle les résultats seront triés :  
  
```  
ORDER BY <expression> [DESC|ASC]  
```  
  
 Utilisez ORDER BY conjointement avec l’instruction TOP \<Number> pour filtrer les résultats retournés. Par exemple, dans cette prédiction, vous allez retourner les dix meilleurs acheteurs de vélos triés selon la probabilité d'exactitude de la prédiction. Vous pouvez recourir à la syntaxe [DESC|ASC] pour contrôler l'ordre d'affichage des résultats.  
  
#### <a name="to-create-a-batch-prediction-query"></a>Pour créer une requête de prédiction par lot  
  
1.  Dans l' **Explorateur d’objets**, cliquez avec le bouton [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]droit sur l’instance de, pointez sur **nouvelle requête**, puis cliquez sur **DMX**.  
  
     L'Éditeur de requête s'ouvre et contient une nouvelle requête vide.  
  
2.  Copiez l'exemple générique de l'instruction par lot dans la requête vide.  
  
3.  Remplacez le code suivant :  
  
    ```  
    <select list>   
    ```  
  
     par :  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    ```  
  
     La clause TOP 10 indique que la requête retourne uniquement les dix meilleurs résultats. L'instruction ORDER BY de cette requête trie les résultats selon la probabilité d'exactitude de la prédiction. Ainsi, seuls les dix meilleurs résultats possibles sont retournés.  
  
4.  Remplacez l'espace réservé suivant :  
  
    ```  
    [<mining model>]   
    ```  
  
     Par le nom du modèle de données :  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  Remplacez l'instruction générique OPENQUERY suivante :  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     Par une instruction qui fait référence à l'entrepôt de données Adventureworks, notamment :  
  
    ```  
    OPENQUERY([Adventure Works DW 2014],  
      'SELECT  
        [LastName],  
        [FirstName],  
        [MaritalStatus],  
        [Gender],  
        [YearlyIncome],  
        [TotalChildren],  
        [NumberChildrenAtHome],  
        [Education],  
        [Occupation],  
        [HouseOwnerFlag],  
        [NumberCarsOwned]  
      FROM  
        [dbo].[ProspectiveBuyer]  
      ') AS t  
    ```  
  
6.  Remplacez la syntaxe générique suivante :  
  
    ```  
    <ON clause, mapping,>   
    WHERE <where clause, boolean expression,>  
    ORDER BY <expression>  
    ```  
  
     Par les mappages de colonnes nécessaire pour ce modèle et un jeu de données d'entrée :  
  
    ```  
    [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
     Spécifiez `DESC` pour afficher en premier les résultats à plus forte probabilité.  
  
     L'instruction tout entière doit se présenter comme suit :  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    FROM  
      [Decision Tree]  
    PREDICTION JOIN  
      OPENQUERY([Adventure Works DW 2014],  
        'SELECT  
          [LastName],  
          [FirstName],  
          [MaritalStatus],  
          [Gender],  
          [YearlyIncome],  
          [TotalChildren],  
          [NumberChildrenAtHome],  
          [Education],  
          [Occupation],  
          [HouseOwnerFlag],  
          [NumberCarsOwned]  
        FROM  
          [dbo].[ProspectiveBuyer]  
        ') AS t  
    ON  
      [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
7.  Dans le menu **fichier** , cliquez sur **Enregistrer DMXQuery1. DMX sous**.  
  
8.  Dans la boîte de dialogue **Enregistrer sous** , accédez au dossier approprié et nommez le fichier `Batch_Prediction.dmx`.  
  
9. Dans la barre d’outils, cliquez sur le bouton **exécuter** .  
  
     La requête retourne une table répertoriant les noms des clients, une prédiction indiquant si chaque client est un acheteur de vélo potentiel et la probabilité de cette prédiction.  
  
 C'est la dernière étape du didacticiel Bike Buyer. Vous disposez désormais d'un ensemble de modèles d'exploration de données à l'aide desquels vous pouvez examiner des similitudes entre vos clients et prévoir qui parmi eux sont des acheteurs potentiels de vélos.  
  
 Pour savoir comment utiliser DMX dans un scénario de panier d’évolution, consultez le didacticiel sur le panier d’un [marché DMX](../../2014/tutorials/market-basket-dmx-tutorial.md).  
  
  
