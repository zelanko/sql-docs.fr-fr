---
title: "Transformer des données à l’aide de R | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 0327e788-94cc-4a47-933b-7c5c027b9208
caps.latest.revision: 19
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 10670f1a5ac3e002d67eab076c41b822b2e757fd
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="transform-data-using-r"></a>Transformer des données à l’aide de R

Le package **RevoScaleR** fournit plusieurs fonctions pour transformer des données à différents stades de votre analyse :

- **rxDataStep** peut être utilisé pour créer et transformer des sous-ensembles de données.

- **rxImport** prend en charge la transformation des données à mesure qu’elles sont importées vers ou depuis un fichier XDF ou une trame de données en mémoire.

- Bien qu’elles ne soient pas spécifiquement conçues pour le déplacement des données, les fonctions **rxSummary**, **rxCube**, **rxLinMod**et **rxLogit** prennent toutes en charge les transformations de données à la volée.

Dans cette section, vous allez apprendre à utiliser ces fonctions. Commençons par rxDataStep.

## <a name="use-rxdatastep-to-transform-variables"></a>Utilisez rxDataStep pour transformer des variables

La fonction rxDataStep traite un segment de données à la fois, la lecture à partir d’une source de données et en écriture à un autre. Vous pouvez spécifier les colonnes à transformer, les transformations à charger, etc.

Pour rendre cet exemple intéressant, vous utiliserez une fonction à partir d’un autre package R pour transformer vos données.  Le package **boot** est un des packages « recommandés » ; en d’autres termes, **boot** est inclus avec chaque distribution de R, mais n’est pas chargé automatiquement au démarrage. Ainsi, le package doit être déjà disponible sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous utilisez avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

À partir du package de **boot** , vous allez utiliser la fonction `inv.logit`afin de calculer l’inverse d’un logit. Autrement dit, la fonction `inv.logit` convertit un logit en une probabilité sur l’échelle [0,1].

> [!TIP] 
> Une autre méthode pour obtenir des prédictions dans cette échelle consisterait à définir le *type* paramètre **réponse** dans l’appel d’origine à rxPredict.

1. Commencez par créer une source de données qui contiendra les données destinées à la table, *ccScoreOutput*.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
2. Ajoutez une autre source de données qui contiendra les données de la table ccScoreOutput2.
  
    ```R
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )
    ```
  
    Dans la nouvelle table, vous obtenez toutes les variables de la table *ccScoreOutput* précédente, ainsi que la variable créée.
  
3. Définissez le contexte de calcul sur l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Utilisez la fonction rxSqlServerTableExists pour vérifier si la table de sortie *ccScoreOutput2* déjà existe ; et dans ce cas, utilisez la fonction rxSqlServerDropTable pour supprimer la table.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")
    ```
  
5. Appelez la fonction rxDataStep et spécifier les transformations de votre choisies dans une liste.
  
    ```R
    rxDataStep(inData = sqlOutScoreDS,
        outFile = sqlOutScoreDS2,
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),
        transformPackages = "boot",
        overwrite = TRUE)
    ```

    Quand vous définissez les transformations qui sont appliquées à chaque colonne, vous pouvez également spécifier les packages R supplémentaires qui sont nécessaires pour effectuer les transformations.  Pour plus d’informations sur les types de transformations que vous pouvez effectuer, consultez  [Transforming and Subsetting Data](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-transform)(Transformation de données et création de sous-ensembles de données).
  
6. Appelez rxGetVarInfo pour afficher un résumé des variables dans le nouveau jeu de données.
  
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

Les scores de logit d’origine sont conservés, mais une nouvelle colonne, *ccFraudProb*, a été ajoutée. Les scores logit y sont représentés sous forme de valeurs comprises entre 0 et 1.

Notez que les variables de facteur ont été écrites dans la table *ccScoreOutput2* en tant que données de type caractère.  Pour les utiliser comme facteurs dans les analyses ultérieures, utilisez le paramètre *colInfo* pour spécifier les niveaux.

## <a name="next-step"></a>Étape suivante

[Charger des données dans la mémoire à l’aide de rxImport](../../advanced-analytics/tutorials/deepdive-load-data-into-memory-using-rximport.md)

## <a name="previous-step"></a>Étape précédente

[Créer et exécuter des Scripts R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)

