---
title: Modifier des données SQL à l’aide de RevoScaleR
description: Découvrez comment interroger et modifier des données à l’aide du langage R sur SQL Server, en particulier la fonction RevoScaleR.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d66452796f3c3cd669784ae7233fb9dcf8e5bc5c
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92195101"
---
# <a name="query-and-modify-the-sql-server-data-sql-server-and-revoscaler-tutorial"></a>Interroger et modifier des données SQL Server (tutoriel SQL Server et RevoScaleR)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Il s’agit du tutoriel 3 de la [série de tutoriels RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) qui traite de l’utilisation des [fonctions RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans le tutoriel précédent, vous avez chargé les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dans le présent tutoriel, vous pouvez explorer et modifier des données à l’aide de **RevoScaleR** :

> [!div class="checklist"]
> * Renvoyer des informations de base sur les variables
> * Créer des données de catégorie à partir de données brutes

Les données de catégorie, ou les *variables de facteur*, sont utiles pour les visualisations de données exploratoires. Vous pouvez les utiliser en tant qu’entrées dans des histogrammes pour avoir une idée de l’apparence des données de variables.

## <a name="query-for-columns-and-types"></a>Requête pour les colonnes et les types

Utilisez un environnement de développement intégré R ou RGui. exe pour exécuter le script R. 

Obtenez d’abord la liste des colonnes et leurs types de données. Vous pouvez utiliser la fonction [rxGetVarInfo](/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) et spécifier la source de données à analyser. Selon votre version de **RevoScaleR**, vous pouvez également utiliser [rxGetVarNames](/machine-learning-server/r-reference/revoscaler/rxgetvarnames). 
  
```R
rxGetVarInfo(data = sqlFraudDS)
```

**Résultats**

```R
Var 1: custID, Type: integer
Var 2: gender, Type: integer
Var 3: state, Type: integer
Var 4: cardholder, Type: integer
Var 5: balance, Type: integer
Var 6: numTrans, Type: integer
Var 7: numIntlTrans, Type: integer
Var 8: creditLine, Type: integer
Var 9: fraudRisk, Type: integer
```

## <a name="create-categorical-data"></a>Créer des données de catégorie

Toutes les variables sont stockées sous forme d’entiers, mais certaines variables représentent des données de catégorie appelées *variables de facteur* dans R. Par exemple, la colonne *state* contient des nombres qui représentent des identificateurs pour les 50 états, plus le District de Columbia. Pour mieux comprendre les données, vous pouvez remplacer les numéros par une liste d’abréviations des noms des états.

Dans cette étape, vous créez un vecteur de chaîne qui contient les abréviations, puis mappez ces valeurs de catégorie aux identificateurs entiers d’origine. Vous allez utiliser la nouvelle variable dans l’argument *colInfo* pour spécifier que cette colonne doit être gérée comme un facteur. Chaque fois que vous analysez ou déplacez les données, les abréviations sont utilisées et la colonne est traitée en tant que facteur.

Le fait de mapper la colonne vers les abréviations avant de l’utiliser comme facteur améliore également les performances. Pour plus d’informations, consultez [R et optimisation des données](../r/r-and-data-optimization-r-services.md).

1. Commencez par créer la variable R *stateAbb*et par définir le vecteur des chaînes que vous lui ajoutez, comme suit :
  
    ```R
    stateAbb <- c("AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC",
        "DE", "FL", "GA", "HI","IA", "ID", "IL", "IN", "KS", "KY", "LA",
        "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NB", "NC", "ND",
        "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI","SC",
        "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY")
    ```

2. Ensuite, créez un objet d’informations de colonne, nommé *ccColInfo*, qui spécifie le mappage des valeurs entières existantes aux niveaux des catégories (les abréviations du nom des états).
  
    Cette instruction crée également des variables de facteur pour gender et cardholder.
  
    ```R
    ccColInfo <- list(
    gender = list(
              type = "factor",
              levels = c("1", "2"),
              newLevels = c("Male", "Female")
              ),
    cardholder = list(
                  type = "factor",
                  levels = c("1", "2"),
                  newLevels = c("Principal", "Secondary")
                   ),
    state = list(
             type = "factor",
             levels = as.character(1:51),
             newLevels = stateAbb
             ),
    balance = list(type = "numeric")
    )
    ```
  
3. Pour créer la source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui utilise les données mises à jour, appelez la fonction **RxSqlServerData** comme précédemment, mais ajoutez l’argument *colInfo*.
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
    table = sqlFraudTable, colInfo = ccColInfo,
    rowsPerRead = sqlRowsPerRead)
    ```
  
    - Pour le paramètre *table* , passez la variable *sqlFraudTable*qui contient la source de données que vous avez créée.
    - Pour le paramètre *colInfo* , passez la variable *ccColInfo* , qui contient les types de données de colonne et les niveaux de facteur.

4.  Vous pouvez maintenant utiliser la fonction **rxGetVarInfo** pour demander des informations sur les variables dans la nouvelle source de données.
  
    ```R
    rxGetVarInfo(data = sqlFraudDS)
    ```

    **Résultats**
    
    ```R
    Var 1: custID, Type: integer
    Var 2: gender  2 factor levels: Male Female
    Var 3: state   51 factor levels: AK AL AR AZ CA ... VT WA WI WV WY
    Var 4: cardholder  2 factor levels: Principal Secondary
    Var 5: balance, Type: integer
    Var 6: numTrans, Type: integer
    Var 7: numIntlTrans, Type: integer
    Var 8: creditLine, Type: integer
    Var 9: fraudRisk, Type: integer
    ```

Les trois variables que vous avez spécifiées (*gender*, *state*et *cardholder*) sont maintenant traitées comme des facteurs.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Définir et utiliser des contextes de calcul](../../machine-learning/tutorials/deepdive-define-and-use-compute-contexts.md)