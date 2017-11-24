---
title: "Visualiser des données SQL Server à l’aide de R (Immersion dans la science des données) | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 10def0b3-9b09-4df9-b8aa-69516f7d7659
caps.latest.revision: "14"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a67480daf011a021002e1688b006a1f0593f8e5f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="visualize-sql-server-data-using-r"></a>Visualiser des données SQL Server à l’aide de R

Les packages améliorés dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] incluent une série de fonctions qui ont été optimisées pour la scalabilité et le traitement parallèle. En général, ces fonctions sont précédées de *rx* ou *Rx*.

Dans le cadre de cette procédure pas à pas, vous allez utiliser la fonction **rxHistogram** pour afficher la distribution des valeurs dans la colonne _creditLine_ , par sexe.

## <a name="visualize-data-using-rxhistogram"></a>Visualiser les données à l’aide de rxHistogram

1. Utilisez le code R suivant pour appeler la fonction rxHistogram et passer d’une source de données et de la formule. Le code peut être exécuté localement dans un premier temps, afin de voir les résultats attendus et combien de temps peut durer son exécution.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    En interne, rxHistogram appelle la fonction rxCube, qui est incluse dans le **RevoScaleR** package. La fonction rxCube génère une seule liste (ou la trame de données) qui contient une colonne pour chaque variable spécifiée dans la formule, plus une colonne de nombres.
    
2. Maintenant, définir le contexte de calcul à l’ordinateur SQL Server distant et exécutez de nouveau rxHistogram.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
 
3. Les résultats sont exactement les mêmes, puisque vous utilisez la même source de données. Cependant, les calculs sont effectués sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Les résultats sont ensuite renvoyés à votre station de travail locale à des fins de traçage.
   
![Résultats de l’histogramme](media/rsql-sue-histogramresults.jpg "Résultats de l’histogramme")

4. Vous pouvez également appeler la fonction rxCube et passer les résultats à une fonction de traçage de R.  Par exemple, l’exemple suivant utilise rxCube pour calculer la moyenne des *fraudRisk* pour chaque combinaison de *numTrans* et *numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Pour spécifier les groupes utilisés pour calculer les moyennes de groupe, utilisez la notation `F()` . Dans cet exemple, `F(numTrans):F(numIntlTrans)` indique que les entiers dans les variables _numTrans_ et _numIntlTrans_ doivent être traités comme des variables catégorielles, avec un niveau pour chaque valeur d’entier.
  
    Étant donné que les niveaux faibles et élevés ont déjà été ajoutés à la source de données *sqlFraudDS* (à l’aide du paramètre *colInfo* ), les niveaux sont automatiquement utilisés dans l’histogramme.
  
5. La valeur de retour de rxCube est par défaut un *rxCube objet*, qui représente un tableau croisé. Toutefois, vous pouvez utiliser la fonction **rxResultsDF** pour convertir les résultats en une trame de données facilement exploitable dans l’une des fonctions de traçage standard de R.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    > [!TIP]
    > 
    > Notez que la fonction rxCube contient un argument facultatif, *returnDataFrame* = vrai, que vous pouvez utiliser pour convertir les résultats une trame de données directement. Exemple :
    >   
    > `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
    >   
    > Toutefois, la sortie de rxResultsDF est beaucoup plus claire et conserve les noms des colonnes sources.
  
6. Enfin, exécutez le code suivant pour créer une carte de chaleur à l’aide de la `levelplot` fonction à partir de la **treillis** package, qui est inclus avec toutes les distributions de R.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Résultats**
  
    ![Résultats du nuage de points](media/rsql-sue-scatterplotresults.jpg "Résultats de nuage de points")
  
Même à partir de cette analyse rapide, vous pouvez voir que le risque de fraude augmente avec le nombre de transactions et le nombre de transactions internationales.

Pour plus d’informations sur la rxCube (fonction) et celles des analyses croisées en général, consultez [des résumés de données](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries).

## <a name="next-step"></a>Étape suivante

[Créer des modèles](../../advanced-analytics/tutorials/deepdive-create-models.md)

## <a name="previous-step"></a>Étape précédente

[Leçon 2 : Créer et exécuter des scripts R](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)


