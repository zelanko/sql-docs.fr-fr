---
title: "Créer la nouvelle Table SQL Server à l’aide de rxDataStep | Documents Microsoft"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 98cead96-6de7-4edf-98b9-a1efb09297b9
caps.latest.revision: "19"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c37cb44bdf2cc30e826ced8e06d47ec64c80f1b1
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="create-new-sql-server-table-using-rxdatastep"></a>Créer une table SQL Server à l’aide de rxDataStep

Dans cette leçon, vous allez apprendre à déplacer des données entre des trames de données en mémoire, le contexte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des fichiers locaux.

> [!NOTE]
> Pour cette leçon, vous allez utiliser un autre dataset. Le dataset de retards de billet d’avion est un jeu de données publique est largement utilisé pour une expérience d’apprentissage. Si vous n’êtes pas familiarisé avec R, ce dataset vous sera utile pour effectuer des tests, car il est utilisé dans différents exemples de produits pour [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] , qui ont été publiés avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les fichiers de données dont vous avez besoin pour cet exemple sont disponibles dans le même répertoire que les autres exemples de produits.

## <a name="create-sql-server-table-from-local-data"></a>Créer une table SQL Server à partir de données locales

Dans la première partie de ce didacticiel, vous avez utilisé le **RxTextData** de fonction pour importer des données dans le code R à partir d’un fichier texte, puis utilisé le **RxDataStep** pour déplacer les données en fonction [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Dans cette leçon, vous allez utiliser une approche différente qui consiste à obtenir les données à partir d’un fichier enregistré au [format XDF](https://en.wikipedia.org/wiki/Extensible_Data_Format). Le format XDF est un standard XML développé pour les données comportant de nombreuses dimensions. C’est un format de fichier binaire avec une interface R qui optimise l’analyse et le traitement des colonnes et des lignes.  Vous pouvez également vous en servir pour déplacer des données et stocker des sous-ensembles de données qui sont utiles pour l’analyse.

Après avoir effectué quelques légères transformations sur les données à l’aide du fichier XDF, vous allez enregistrer les données transformées dans une nouvelle table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

> [!NOTE]
> Vous avez besoin des autorisations DDL pour cette étape.

1. Définissez le contexte de calcul sur votre station de travail locale.
  
    ```R
    rxSetComputeContext("local")
    ```
  
2. Définissez un nouvel objet de source de données utilisant la fonction **RxXdfData** . Pour une source de données XDF, spécifiez simplement le chemin du fichier de données.  Vous pouvez spécifier le chemin d’accès au fichier à l’aide d’une variable de texte, mais dans ce cas, il existe un raccourci pratique, car l’exemple de fichier de données (AirlineDemoSmall.xdf) se trouve dans le répertoire retourné par la fonction rxGetOption.
  
    ```R
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))
    ```

3. Appeler rxGetVarInfo sur les données en mémoire pour afficher un résumé du jeu de données.
  
    ```R
    rxGetVarInfo(xdfAirDemo)
    ```

**Résultats**

*Var 1: ArrDelay, Type: integer, Low/High: (-86, 1490)*

*Var 2: CRSDepTime, Type: numeric, Storage: float32, Low/High: (0,0167, 23,9833)*

*Var 3: DayOfWeek 7 factor levels: Monday Tuesday Wednesday Thursday Friday Saturday Sunday*

> [!NOTE]
> 
> Avez-vous remarqué que vous n’était pas nécessaire d’appeler d’autres fonctions pour charger les données dans le fichier XDF et Impossible d’appeler rxGetVarInfo sur les données immédiatement ? C’est parce que l’usage du fichier XDF constitue la méthode de stockage temporaire par défaut de RevoScaleR. Pour plus d’informations sur les fichiers XDF, consultez [créer un XDF](https://msdn.microsoft.com/microsoft-r/scaler-data-xdf).
  
4. Vous placez maintenant ces données dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , en stockant _DayOfWeek_ sous forme d’entier avec des valeurs comprises entre 1 et 7.
  
    Pour cela, définissez d’abord une source de données SQL Server.
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
5. Vérifiez si une table du même nom existe déjà et, si tel est le cas, supprimez-la.
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
6. Créez la table et chargez les données à l’aide de **rxDataStep**. Cette fonction déplace les données entre deux déjà défini les sources de données et peuvent transformer les données en cours de route.
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
            transforms = list( DayOfWeek = as.integer(DayOfWeek),
            rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
            overwrite = TRUE )
    ```
  
    Cette table étant assez volumineuse, attendez l’apparition du message d’état final : *Rows Read: 200000, Total Rows Processed: 600000*.
     
7. Définissez le contexte de calcul à nouveau sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
8. Créez une source de données SQL Server à l’aide d’une requête SQL simple sur la nouvelle table. Cette définition ajoute des niveaux de facteur pour la colonne *DayOfWeek* à l’aide de l’argument *colInfo* à RxSqlServerData.
  
    ```R
    SqlServerAirDemo <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
9. Appelez rxSummary pour consulter un résumé des données dans votre requête.
  
    ```R
    rxSummary(~., data = sqlServerAirDemo)
    ```

## <a name="next-step"></a>Étape suivante

[Effectuer une analyse de segmentation à l’aide de rxDataStep](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)

## <a name="previous-step"></a>Étape précédente

[Charger des données dans la mémoire à l’aide de rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)


