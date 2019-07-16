---
title: Créer la nouvelle table SQL Server à l’aide de rxDataStep RevoScaleR - SQL Server Machine Learning
description: Didacticiel pas à pas sur la création d’une table SQL Server à l’aide du langage R sur SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 484f238e53db21030b04cdf46b86271236509989
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962266"
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>Créer la nouvelle table SQL Server à l’aide de rxDataStep (didacticiel sur SQL Server et RevoScaleR)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cette leçon fait partie de la [RevoScaleR didacticiel](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) sur l’utilisation [fonctions RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) avec SQL Server.

Dans cette leçon, vous allez apprendre à déplacer des données entre des trames de données en mémoire, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contexte et des fichiers locaux.

> [!NOTE]
> Cette leçon est basée sur un autre jeu de données. Le jeu de données des retards des compagnies aériennes est un jeu de données public qui est largement utilisé pour l’expérience d’apprentissage. Les fichiers de données utilisés dans cet exemple sont disponibles dans le même répertoire que les autres exemples de produits.

## <a name="load-data-from-a-local-xdf-file"></a>Charger des données à partir d’un fichier XDF local

Dans la première moitié de ce didacticiel, vous avez utilisé le **RxTextData** fonction pour importer des données dans R à partir d’un fichier texte, puis utilisé la **RxDataStep** fonction permettant de déplacer les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Cette leçon adopte une approche différente, et utilise des données à partir d’un fichier enregistrement dans le [format XDF](https://en.wikipedia.org/wiki/Extensible_Data_Format). Après avoir effectué quelques légères transformations sur les données à l’aide du fichier XDF, vous enregistrez les données transformées dans un nouveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.

**Qu’est XDF ?**

Le format XDF est un standard XML développé pour les données de grande dimension et est le format de fichier natif utilisé par [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf). C’est un format de fichier binaire avec une interface R qui optimise l’analyse et le traitement des colonnes et des lignes.  Vous pouvez également vous en servir pour déplacer des données et stocker des sous-ensembles de données qui sont utiles pour l’analyse.

1. Définissez le contexte de calcul sur votre station de travail locale. **Autorisations DDL sont nécessaires pour cette étape.**

    ```R
    rxSetComputeContext("local")
    ```
  
2. Définissez un nouvel objet de source de données utilisant la fonction **RxXdfData** . Pour définir une source de données XDF, spécifiez le chemin d’accès au fichier de données.  

    Vous pouvez spécifier le chemin d’accès au fichier à l’aide d’une variable de texte. Toutefois, dans ce cas, il existe un raccourci pratique, qui consiste à utiliser le **rxGetOption** de fonction et obtenir le fichier (AirlineDemoSmall.xdf) à partir du répertoire de données d’exemple.
  
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
> Avez-vous remarqué que vous n’avez pas eu besoin d’appeler d’autres fonctions pour charger les données dans le fichier XDF et que vous avez pu appeler **rxGetVarInfo** dans les données immédiatement ? C’est parce que le format XDF est la méthode de stockage temporaire par défaut **RevoScaleR**. En plus des fichiers XDF, le **rxGetVarInfo** fonction prend désormais en charge plusieurs types de sources.

## <a name="move-contents-to-sql-server"></a>Déplacer le contenu vers SQL Server

Avec la source de données XDF créée dans la session R locale, vous pouvez maintenant déplacer ces données dans une table de base de données, stockage *DayOfWeek* en tant qu’entier avec des valeurs comprises entre 1 et 7.

1. Définir un objet de source de données SQL Server, en spécifiant une table pour contenir les données et la connexion au serveur distant.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
2. Par précaution, inclure une étape qui vérifie si une table portant le même nom existe déjà et supprimez la table si elle existe. Une table existante du même nom empêche la création d’un autre.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
3. Charger les données dans la table à l’aide **rxDataStep**. Cette fonction déplace des données entre deux déjà défini les sources de données et peuvent éventuellement transformer les données en cours de route.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
        transforms = list( DayOfWeek = as.integer(DayOfWeek),
        rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
        overwrite = TRUE )
    ```
  
    Il s’agit d’une table très volumineuse, aussi attendez jusqu'à ce que vous voyiez un dernier message d’état comme celle-ci : *Lignes lues : 200000, total des lignes traitées : 600000*.
     
## <a name="load-data-from-a-sql-table"></a>Charger des données à partir d’une table SQL

Une fois que les données existent dans la table, vous pouvez le charger à l’aide d’une simple requête SQL. 

1. Créer une nouvelle source de données SQL Server. L’entrée est une requête sur la nouvelle table que vous venez de créer et chargé avec les données. Cette définition ajoute des niveaux de facteur pour la *DayOfWeek* colonne, à l’aide de la *colInfo* l’argument de **RxSqlServerData**.
  
    ```R
    sqlServerAirDemo2 <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
2. Appelez **rxSummary** une fois de plus pour obtenir un résumé des données dans votre requête.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo2)
    ```

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Effectuer une analyse de segmentation à l’aide de rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)