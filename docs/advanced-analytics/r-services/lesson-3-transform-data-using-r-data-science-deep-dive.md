---
title: "Le&#231;on 3 : Transformer des donn&#233;es &#224; l’aide de R (Immersion dans la science des donn&#233;es) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "10/03/2016"
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
ms.assetid: 0327e788-94cc-4a47-933b-7c5c027b9208
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 18
---
# Le&#231;on 3 : Transformer des donn&#233;es &#224; l’aide de R (Immersion dans la science des donn&#233;es)
Le package **RevoScaleR** fournit plusieurs fonctions pour transformer des données à différents stades de votre analyse :  
  
-   **rxDataStep** peut être utilisé pour créer et transformer des sous-ensembles de données.  
  
-   **rxImport** prend en charge la transformation des données à mesure qu’elles sont importées vers ou depuis un fichier XDF ou une trame de données en mémoire.  
  
-   Bien qu’elles ne soient pas spécifiquement conçues pour le déplacement des données, les fonctions **rxSummary**, **rxCube**, **rxLinMod** et **rxLogit** prennent toutes en charge les transformations de données à la volée.  
  
Dans cette section, vous allez apprendre à utiliser ces fonctions. Commençons par *rxDataStep*.  
  
## Utilisez rxDataStep pour transformer des variables  
La fonction *rxDataStep* traite les données segment par segment, en lisant à partir d’une source de données et en écrivant dans une autre. Vous pouvez spécifier les colonnes à transformer, les transformations à charger, etc.  
  
Pour rendre cet exemple intéressant, vous utiliserez une fonction à partir d’un autre package R pour transformer vos données.  Le package **boot** est un des packages « recommandés » ; en d’autres termes, **boot** est inclus avec chaque distribution de R, mais n’est pas chargé automatiquement au démarrage. Ainsi, le package doit être déjà disponible sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous utilisez avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
À partir du package de **démarrage**, vous allez utiliser la fonction *inv.logit* afin de calculer l’inverse d’un logit. Autrement dit, la fonction *inv.logit* convertit un logit en une probabilité sur l’échelle [0,1].  
  
> [!TIP]  
> Une autre façon d’obtenir des prédictions dans cette échelle consiste à définir le paramètre *type* sur **response** dans l’appel initial à *rxPredict*.  
  
1.  Commencez par créer une source de données qui contiendra les données destinées à la table, *ccScoreOutput*.  
  
    ```R  
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )  
  
    ```  
  
2.  Ajoutez une autre source de données qui contiendra les données de la table ccScoreOutput2.  
  
    ```R  
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )  
  
    ```  
  
    Dans la nouvelle table, vous obtenez toutes les variables de la table *ccScoreOutput* précédente, ainsi que la variable créée.  
  
3.  Définissez le contexte de calcul sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```R  
    rxSetComputeContext(sqlCompute)  
  
    ```  
  
4.  Utilisez la fonction *rxSqlServerTableExists* pour vérifier si la table de sortie *ccScoreOutput2* existe déjà, et si tel est le cas, utilisez la fonction *rxSqlServerDropTable* pour supprimer la table.  
  
    ```R    
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")  
  
    ```  
  
5.  Appelez la fonction *rxDataStep* et spécifiez les transformations de votre choix dans une liste.  
  
    ```R  
    rxDataStep(inData = sqlOutScoreDS,   
        outFile = sqlOutScoreDS2,         
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),        
        transformPackages = "boot",   
        overwrite = TRUE)    
    ```  
  
    Quand vous définissez les transformations qui sont appliquées à chaque colonne, vous pouvez également spécifier les packages R supplémentaires qui sont nécessaires pour effectuer les transformations.  Pour plus d’informations sur les types de transformations que vous pouvez effectuer, consultez [Transforming and Subsetting Data](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-transform) (Transformation de données et création de sous-ensembles de données).
  
6.  Appelez *rxGetVarInfo* pour afficher un récapitulatif des variables dans le nouveau dataset.  
  
    ```R  
    rxGetVarInfo(sqlOutScoreDS2)  
    ```  
  
**Résultats**  
  
*Var 1 : ccFraudLogitScore, Type : numérique*  
*Var 2 : state, Type : caractère*  
*Var 3 : gender, Type : caractère*  
*Var 4 : cardholder, Type : caractère*  
*Var 5 : balance, Type : entier*  
*Var 6 : numTrans, Type : entier*  
*Var 7 : numIntlTrans, Type : entier*  
*Var 8 : creditLine, Type : entier*  
*Var 9 : ccFraudProb, Type : numérique*  
  
Les scores de logit d’origine sont conservés, mais une nouvelle colonne, *ccFraudProb*, a été ajoutée. Les scores logit y sont représentés sous forme de valeurs comprises entre 0 et 1. 

Notez que les variables de facteur ont été écrites dans la table *ccScoreOutput2* en tant que données de type caractère.  Pour les utiliser comme facteurs dans les analyses ultérieures, utilisez le paramètre *colInfo* pour spécifier les niveaux.  

  
## Étape suivante  
[Charger des données en mémoire à l’aide de rxImport &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/load-data-into-memory-using-rximport-data-science-deep-dive.md)  
  
## Étape précédente  
[Leçon 2 : Créer et exécuter des scripts R &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
  
  
