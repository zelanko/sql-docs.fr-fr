---
title: Créer une table SQL Server à l’aide de RevoScaleR rxDataStep
description: Didacticiel procédure pas à pas sur la création d’une table SQL Server à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 5f5d65bf3b57f40ca881aa9e6f0285fab0432a1e
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344791"
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Créer une nouvelle table SQL Server à l’aide de rxDataStep (didacticiel SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie du [didacticiel RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans cette leçon, vous allez apprendre à déplacer des données entre des trames de données en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mémoire, le contexte et des fichiers locaux.

> [!NOTE]
> Cette leçon utilise un jeu de données différent. Le jeu de données retards de la compagnie aérienne est un jeu de données public largement utilisé pour les expériences Machine Learning. Les fichiers de données utilisés dans cet exemple sont disponibles dans le même répertoire que les autres exemples de produits.

## <a name="load-data-from-a-local-xdf-file"></a>Charger des données à partir d’un fichier XDF local

Dans la première moitié de ce didacticiel, vous avez utilisé la fonction **RxTextData** pour importer des données dans R à partir d’un fichier texte, puis vous avez utilisé la fonction **RxDataStep** pour déplacer les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Cette leçon adopte une approche différente et utilise les données d’un fichier enregistré au [format XDF](https://en.wikipedia.org/wiki/Extensible_Data_Format). Après avoir effectué des transformations légères sur les données à l’aide du fichier XDF, vous enregistrez les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transformées dans une nouvelle table.

**Qu’est-ce que XDF?**

Le format XDF est une norme XML développée pour les données de grande dimension. il s’agit du format de fichier natif utilisé par [machine learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). C’est un format de fichier binaire avec une interface R qui optimise l’analyse et le traitement des colonnes et des lignes.  Vous pouvez également vous en servir pour déplacer des données et stocker des sous-ensembles de données qui sont utiles pour l’analyse.

1. Définissez le contexte de calcul sur votre station de travail locale. **Des autorisations DDL sont nécessaires pour cette étape.**

    ```R
    rxSetComputeContext("local")
    ```
  
2. Définissez un nouvel objet de source de données utilisant la fonction **RxXdfData** . Pour définir une source de données XDF, spécifiez le chemin d’accès au fichier de données.  

    Vous pouvez spécifier le chemin d’accès au fichier à l’aide d’une variable de texte. Toutefois, dans ce cas, il existe un raccourci pratique, qui consiste à utiliser la fonction **rxGetOption** et à obtenir le fichier (AirlineDemoSmall. XDF) à partir du répertoire des exemples de données.
  
    ```R
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))
    ```

3. Appelez [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) dans les données en mémoire pour afficher un résumé du dataset.
  
    ```R
    rxGetVarInfo(xdfAirDemo)
    ```

**Résultats**

```R
Var 1: ArrDelay, Type: integer, Low/High: (-86, 1490)
Var 2: CRSDepTime, Type: numeric, Storage: float32, Low/High: (0.0167, 23.9833)
Var 3: DayOfWeek 7 factor levels: Monday Tuesday Wednesday Thursday Friday Saturday Sunday
```

> [!NOTE]
> 
> Avez-vous remarqué que vous n’avez pas eu besoin d’appeler d’autres fonctions pour charger les données dans le fichier XDF et que vous avez pu appeler **rxGetVarInfo** dans les données immédiatement ? Cela est dû au fait que XDF est la méthode de stockage intermédiaire par défaut pour **RevoScaleR**. En plus des fichiers XDF, la fonction **rxGetVarInfo** prend désormais en charge plusieurs types de sources.

## <a name="move-contents-to-sql-server"></a>Déplacer le contenu vers SQL Server

Une fois la source de données XDF créée dans la session R locale, vous pouvez désormais déplacer ces données dans une table de base de données, en stockant *DayOfWeek* sous la forme d’un entier avec des valeurs comprises entre 1 et 7.

1. Définir un SQL Server objet de source de données, en spécifiant une table pour contenir les données et une connexion au serveur distant.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
2. Par précaution, incluez une étape qui vérifie si une table portant le même nom existe déjà, et supprimez la table si elle existe. Une table existante portant le même nom empêche toute création d’une nouvelle table.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
3. Chargez les données dans la table à l’aide de **rxDataStep**. Cette fonction déplace les données entre deux sources de données déjà définies et peut éventuellement transformer les données en route.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
        transforms = list( DayOfWeek = as.integer(DayOfWeek),
        rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
        overwrite = TRUE )
    ```
  
    Il s’agit d’une table relativement volumineuse. Patientez jusqu’à ce qu’un message d’état final semblable à celui-ci s’affiche: *Lignes lues: 200000, nombre total de lignes traitées: 600000*.
     
## <a name="load-data-from-a-sql-table"></a>Charger des données à partir d’une table SQL

Une fois que les données existent dans la table, vous pouvez les charger à l’aide d’une requête SQL simple. 

1. Créez une nouvelle source de données SQL Server. L’entrée est une requête sur la nouvelle table que vous venez de créer et de charger avec des données. Cette définition ajoute des niveaux de facteur pour la colonne *DayOfWeek* , à l’aide de l’argument *colInfo* pour **RxSqlServerData**.
  
    ```R
    sqlServerAirDemo2 <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
2. Appelez **rxSummary** une fois de plus pour consulter un résumé des données dans votre requête.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo2)
    ```

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Effectuer une analyse de segmentation à l’aide de rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)