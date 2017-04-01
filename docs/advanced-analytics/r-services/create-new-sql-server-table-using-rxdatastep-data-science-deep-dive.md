---
title: "Cr&#233;er une table SQL Server &#224; l’aide de rxDataStep (Immersion dans la science des donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 98cead96-6de7-4edf-98b9-a1efb09297b9
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Cr&#233;er une table SQL Server &#224; l’aide de rxDataStep (Immersion dans la science des donn&#233;es)
Dans cette leçon, vous allez apprendre à déplacer des données entre des trames de données en mémoire, le contexte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des fichiers locaux.  
  
> [!NOTE]  
> Pour cette leçon, vous allez utiliser un autre dataset. Le dataset sur les retards des compagnies aériennes est un dataset public qui est largement utilisé pour les expérimentations en matière de Machine Learning. Si vous n’êtes pas familiarisé avec R, ce dataset vous sera utile pour effectuer des tests, car il est utilisé dans différents exemples de produits pour [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], qui ont été publiés avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les fichiers de données dont vous avez besoin pour cet exemple sont disponibles dans le même répertoire que les autres exemples de produits.  
  
## Créer une table SQL Server à partir de données locales  
Dans la première leçon de ce didacticiel, vous avez utilisé la fonction *RxTextData* pour importer des données dans R à partir d’un fichier texte, puis vous avez utilisé la fonction *RxDataStep* pour déplacer les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Dans cette leçon, vous allez utiliser une approche différente qui consiste à obtenir les données à partir d’un fichier enregistré au [format XDF](https://en.wikipedia.org/wiki/Extensible_Data_Format). Le format XDF est un standard XML développé pour les données comportant de nombreuses dimensions. C’est un format de fichier binaire avec une interface R qui optimise l’analyse et le traitement des colonnes et des lignes.  Vous pouvez également vous en servir pour déplacer des données et stocker des sous-ensembles de données qui sont utiles pour l’analyse.
  
Après avoir effectué quelques légères transformations sur les données à l’aide du fichier XDF, vous allez enregistrer les données transformées dans une nouvelle table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
> Vous avez besoin des autorisations DDL pour cette étape.  
  
1.  Définissez le contexte de calcul sur votre station de travail locale.  
  
    ```R  
    rxSetComputeContext("local")   
    ```  
  
2.  Définissez un nouvel objet de source de données utilisant la fonction *RxXdfData*. Pour une source de données XDF, spécifiez simplement le chemin du fichier de données.  Vous pouvez spécifier le chemin du fichier en utilisant une variable texte. Ici, il existe un raccourci pratique, car l’exemple de fichier de données (AirlineDemoSmall.xdf) se trouve dans le répertoire retourné par la fonction *rxGetOption*.
  
    ```R  
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))   
    ```  
  
  
3.  Appelez *rxGetVarInfo* dans les données en mémoire pour afficher un résumé du dataset.  
  
    ```R  
    rxGetVarInfo(xdfAirDemo)    
    ```  
  
**Résultats**  
  
*Var 1: ArrDelay, Type: integer, Low/High: (-86, 1490)*   
*Var 2: CRSDepTime, Type: numeric, Storage: float32, Low/High: (0,0167, 23,9833)*   
*Var 3: DayOfWeek 7 factor levels: Monday Tuesday Wednesday Thursday Friday Saturday Sunday*  

> [!NOTE]
> 
> Avez-vous remarqué que vous n’avez pas eu besoin d’appeler d’autres fonctions pour charger les données dans le fichier XDF et que vous avez pu appeler *rxGetVarInfo* dans les données immédiatement ? C’est parce que l’usage du fichier XDF constitue la méthode de stockage temporaire par défaut de RevoScaleR. Pour plus d’informations sur les fichiers XDF, consultez le [Guide de prise en main de ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-transform#using-the-data-step-to-create-an-xdf-file-from-a-data-frame) 
  
4.  Vous placez maintenant ces données dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], en stockant _DayOfWeek_ sous forme d’entier avec des valeurs comprises entre 1 et 7.  
  
    Pour cela, définissez d’abord une source de données SQL Server.  
  
    ```R  
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)   
    ```  
  
5.  Vérifiez l’existence d’une table du même nom et supprimez la table si elle existe.  
  
    ```R  
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)    
    ```  
  
6.  Créez la table et chargez les données à l’aide de `rxDataStep`.  
  
    ```R  
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,    
            transforms = list( DayOfWeek = as.integer(DayOfWeek),   
            rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),   
            overwrite = TRUE )    
    ```  
  
7.  Définissez le contexte de calcul à nouveau sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```R  
    rxSetComputeContext(sqlCompute)  
    ```  
  
8.  Définissez une partie des données à l’aide d’une instruction SQL simple.  
  
    ```R    
    SqlServerAirDemo <- RxSqlServerData(  
        sqlQuery = "SELECT * FROM AirDemoSmallTest",      
        connectionString = sqlConnString,   
        rowsPerRead = 50000,      
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))    
    ```  
  
9. Appelez *rxSummary* pour obtenir un résumé des données de votre requête.  
  
    ```R  
    rxSummary(~., data = sqlServerAirDemo)   
    ```  
  
## Étape suivante  
[Effectuer une analyse de segmentation à l’aide de rxDataStep &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/perform-chunking-analysis-using-rxdatastep-data-science-deep-dive.md)  
  
## Étape précédente  
[Charger des données en mémoire à l’aide de rxImport &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/load-data-into-memory-using-rximport-data-science-deep-dive.md)  
  
## Voir aussi  
[Immersion dans la science des données : utilisation des packages RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
