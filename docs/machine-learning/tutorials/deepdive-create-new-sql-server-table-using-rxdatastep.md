---
title: Créer une table avec rxDataStep
description: 'Tutoriel RevoScaleR 11 : Comment créer une table SQL Server à l’aide du langage R sur SQL Server.'
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0550c90807328cf89d8d533ac583c8410c79f5c2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85728594"
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Créer une table SQL Server à l’aide de rxDataStep (tutoriel SQL Server et RevoScaleR)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Il s’agit du tutoriel 11 de la [série de tutoriels RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) qui traite de l’utilisation des [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans ce tutoriel, vous allez apprendre à déplacer des données entre des trames de données en mémoire, le contexte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des fichiers locaux.

> [!NOTE]
> Ce tutoriel utilise un jeu de données différent. Le jeu de données sur les retards des compagnies aériennes est un jeu de données public qui est largement utilisé pour les expérimentations en matière de Machine Learning. Les fichiers de données utilisés dans cet exemple sont disponibles dans le même répertoire que les autres exemples de produits.

## <a name="load-data-from-a-local-xdf-file"></a>Charger des données à partir d’un fichier XDF local

Dans la première partie de cette série de tutoriels, vous avez utilisé la fonction **RxTextData** pour importer des données dans R à partir d’un fichier texte, puis vous avez utilisé la fonction **RxDataStep** pour déplacer les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Ce tutoriel utilise une approche différente qui consiste à utiliser les données à partir d’un fichier enregistré au [format XDF](https://en.wikipedia.org/wiki/Extensible_Data_Format). Après avoir effectué quelques légères transformations sur les données à l’aide du fichier XDF, vous allez enregistrer les données transformées dans une nouvelle table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

**Qu’est-ce que XDF ?**

Le format XDF est une norme XML développée pour les données de grande dimension. Il s’agit du format de fichier natif utilisé par [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). C’est un format de fichier binaire avec une interface R qui optimise l’analyse et le traitement des colonnes et des lignes.  Vous pouvez également vous en servir pour déplacer des données et stocker des sous-ensembles de données qui sont utiles pour l’analyse.

1. Définissez le contexte de calcul sur votre station de travail locale. **Les autorisations DDL sont nécessaires pour cette étape.**

    ```R
    rxSetComputeContext("local")
    ```
  
2. Définissez un nouvel objet de source de données utilisant la fonction **RxXdfData** . Pour définir une source de données XDF, spécifiez le chemin du fichier de données.  

    Vous pouvez spécifier le chemin d’accès au fichier à l’aide d’une variable de texte. Toutefois, dans ce cas, il existe un raccourci pratique, qui consiste à utiliser la fonction **rxGetOption** et à obtenir le fichier (AirlineDemoSmall.xdf) à partir du répertoire des exemples de données.
  
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
> Avez-vous remarqué que vous n’avez pas eu besoin d’appeler d’autres fonctions pour charger les données dans le fichier XDF et que vous avez pu appeler **rxGetVarInfo** dans les données immédiatement ? C’est parce que l’usage du fichier XDF constitue la méthode de stockage temporaire par défaut de **RevoScaleR**. En plus des fichiers XDF, la fonction **rxGetVarInfo** prend désormais en charge plusieurs types de sources.

## <a name="move-contents-to-sql-server"></a>Déplacer du contenu vers SQL Server

Une fois la source de données XDF créée dans la session R locale, vous pouvez désormais déplacer ces données dans une table de base de données, en stockant *DayOfWeek* sous la forme d’un entier avec des valeurs comprises entre 1 et 7.

1. Définissez un objet de source de données SQL Server, en spécifiant une table pour contenir les données et une connexion au serveur distant.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
2. Par précaution, incluez une étape pour vérifier si une table du même nom existe déjà et, si tel est le cas, supprimez-la. Une table existante portant le même nom empêche toute création d’une nouvelle table.
  
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
  
    Il s’agit d’une table relativement volumineuse. Patientez jusqu’à ce qu’un message d’état final semblable à celui-ci s’affiche : *Lignes lues : 200 000, Nombre total de lignes traitées : 600 000*.
     
## <a name="load-data-from-a-sql-table"></a>Charger des données à partir d’une table SQL

Une fois que les données existent dans la table, vous pouvez les charger à l’aide d’une requête SQL simple. 

1. Créez une source de données SQL Server. L’entrée est une requête sur la nouvelle table que vous venez de créer et sur laquelle vous avez chargé les données. Cette définition ajoute des niveaux de facteur pour la colonne *DayOfWeek* à l’aide de l’argument *colInfo* à **RxSqlServerData**.
  
    ```R
    sqlServerAirDemo2 <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
2. Appelez **rxSummary** une fois de plus pour obtenir un résumé des données de votre requête.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo2)
    ```

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Effectuer une analyse de segmentation à l’aide de rxDataStep](../../machine-learning/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)