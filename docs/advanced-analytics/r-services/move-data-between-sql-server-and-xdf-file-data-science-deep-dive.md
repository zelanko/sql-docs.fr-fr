---
title: "D&#233;placer des donn&#233;es entre SQL Server et un fichier XDF (Immersion dans la science des donn&#233;es) | Microsoft Docs"
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
ms.assetid: 40887cb3-ffbb-4769-9f54-c006d7f4798c
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# D&#233;placer des donn&#233;es entre SQL Server et un fichier XDF (Immersion dans la science des donn&#233;es)
Quand vous travaillez dans un contexte de calcul local, vous avez accès à des fichiers de données locaux et à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (définie comme source de données *RxSqlServerData*).  
  
Dans cette section, vous allez apprendre à obtenir des données et à les stocker dans un fichier sur l’ordinateur local en vue de leur faire subir des transformations. Quand vous aurez terminé, vous utiliserez les données du fichier pour créer une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à l’aide de *rxDataStep*.  
  
## Créer une table SQL Server à partir d’un fichier XDF  

La fonction *rxImport* vous permet d’importer des données à partir d’une source de données prise en charge dans un fichier XDF local. Utiliser un fichier local peut être pratique si vous souhaitez effectuer de nombreuses analyses différentes sur les données stockées dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et ne pas avoir à exécuter la même requête à maintes reprises.  
  
Pour cet exercice, vous allez réutiliser les données de fraude à la carte de crédit. Dans ce scénario, vous avez été invité à effectuer des analyses supplémentaires sur les utilisateurs dans les États de la Californie, de l’Oregon et de Washington. Pour être plus efficace, vous avez décidé de stocker les données de ces seuls États sur votre ordinateur local et vous utilisez les variables gender, cardholder, state et balance (sexe, détenteur de la carte, état et solde).  
  
1.  Réutilisez le vecteur *stateAbb* que vous avez créé pour identifier les niveaux à inclure, puis affichez la nouvelle variable *statesToKeep* dans la console.  
  
    ```  
    statesToKeep <- sapply(c("CA", "OR", "WA"), grep, stateAbb)   
  
    statesToKeep  
  
    ```  
 **Résultats**
CA |  - ou -  | WA 
-- | -- | --
 5 |  38  | 48 
  
2.  À présent, vous allez définir les données que vous souhaitez déplacer à partir de SQL Server, à l’aide d’une requête [!INCLUDE[tsql](../../includes/tsql-md.md)].  Plus tard, vous utiliserez cette variable en tant qu’argument *inData* pour *rxImport*.  
  
    ```R  
    importQuery <- paste("SELECT gender,cardholder,balance,state FROM",  sqlFraudTable,  "WHERE (state = 5 OR state = 38 OR state = 48)")  
  
    ```  
  
    Vérifiez que la requête ne contient aucun caractère masqué, tel qu’un saut de ligne ou une tabulation.  
  
3.  Ensuite, vous allez définir les colonnes à utiliser lorsque vous utilisez des données dans R.  
  Par exemple, dans le dataset le plus petit, vous n’avez besoin que de trois niveaux de facteur, car la requête retourne les données de seulement trois états.  Vous pouvez réutiliser la variable *statesToKeep* pour identifier les niveaux à inclure.  
  
    ```R  
    importColInfo <- list(   
        gender = list( type = "factor",  levels = c("1", "2"), newLevels = c("Male", "Female")),       
        cardholder = list(  type = "factor",  levels = c("1", "2"), newLevels = c("Principal", "Secondary")),     
        state = list(   type = "factor",  levels = as.character(statesToKeep), newLevels = names(statesToKeep))   
            )  
  
    ```  
  
4.  Définissez le contexte de calcul sur **local**, car vous souhaitez toutes les données disponibles sur votre ordinateur local.  
  
    ```R  
    rxSetComputeContext("local")   
    ```  
  
5.  Créez l’objet de source de données en passant toutes les variables que vous venez de définir en tant qu’arguments à *RxSqlServerData*.  
  
    ```R  
    sqlServerImportDS <- RxSqlServerData(  
        connectionString = sqlConnString,   
        sqlQuery = importQuery,   
        colInfo = importColInfo)  
  
    ```  
  
6.  Ensuite, appelez *rxImport* pour enregistrer les données dans le répertoire de travail actuel, dans un fichier nommé `ccFraudSub.xdf`.  
  
    ```R  
    localDS <- rxImport(inData = sqlServerImportDS,   
        outFile = "ccFraudSub.xdf",    
        overwrite = TRUE)  
  
    ```  
  
    L’objet *localDs* retourné par la fonction *rxImport* est un objet de source de données *RxXdfData* léger qui représente le fichier de données ccFraud.xdf stocké localement sur le disque.  
  
7.  Appelez *rxGetVarInfo* dans le fichier XDF pour vérifier que le schéma de données est le même.  
  
    ```R  
    rxGetVarInfo(data = localDS)   
    ```  
    **Résultats**
    
    *rxGetVarInfo(data = localDS)*    
    *Var 1 : sexe, Type : facteur, aucun niveau de facteur disponible*    
    *Var 2 : titulaire de la carte, Type : facteur, aucun niveau de facteur disponible*    
    *Var 3 : solde, Type : entier Min./Max. : (0, 22463)*    
    *Var 4 : état, Type : facteur, aucun niveau de facteur disponible*
  
8.  Vous pouvez maintenant appeler différentes fonctions R pour analyser l’objet *localDs*, comme vous le feriez avec les données sources sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par exemple :  
  
    ```R  
    rxSummary(~gender + cardholder + balance + state, data = localDS)    
    ```  
  
L’utilisation des contextes de calcul et de différentes sources de données n’ayant plus de secret pour vous, il est temps d’essayer quelque chose d’amusant.  
  
Dans la prochaine et dernière leçon, vous allez créer une simulation simple à l’aide d’une fonction R personnalisée et l’exécuter sur le serveur distant.  
  
## Étape suivante  
[Leçon 5 : Créer une simulation simple &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/lesson-5-create-a-simple-simulation-data-science-deep-dive.md)  
  
## Étape précédente  
[Leçon 4 : Analyser les données dans le contexte de calcul local &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/lesson-4-analyze-data-in-local-compute-context-data-science-deep-dive.md)  
  
## Voir aussi  
[Immersion dans la science des données : utilisation des packages RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
