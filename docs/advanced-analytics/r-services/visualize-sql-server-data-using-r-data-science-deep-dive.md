---
title: "Visualiser des donn&#233;es SQL Server &#224; l’aide de R (Immersion dans la science des donn&#233;es) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
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
ms.assetid: 10def0b3-9b09-4df9-b8aa-69516f7d7659
caps.latest.revision: 14
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Visualiser des donn&#233;es SQL Server &#224; l’aide de R (Immersion dans la science des donn&#233;es)
Les packages améliorés dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] incluent une série de fonctions qui ont été optimisées pour la scalabilité et le traitement parallèle. En général, ces fonctions sont précédées de *rx* ou *Rx*.  
  
Dans le cadre de cette procédure pas à pas, vous allez utiliser la fonction *rxHistogram* pour afficher la distribution des valeurs dans la colonne _creditLine_, par sexe.  
  
## Visualiser les données à l’aide de rxHistogram et rxCube  
  
1.  Le code R suivant permet d’appeler la fonction *rxHistogram* et de passer une formule et une source de données. Le code peut être exécuté localement dans un premier temps, afin de voir les résultats attendus et combien de temps peut durer son exécution.
  
    ```R  
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")   
    ```  
 
    En interne, *rxHistogram* appelle la fonction *rxCube*, qui est incluse dans le package **RevoScaleR**. La fonction *rxCube* génère une liste unique (ou trame de données) qui contient une colonne pour chaque variable spécifiée dans la formule, plus une colonne de nombres.
    
2. À présent, définissez le contexte de calcul sur l’ordinateur SQL Server distant, puis réexécutez la fonction *rxHistogram*.
  
    ```R  
    rxSetComputeContext(sqlCompute)  
    ```  
 
3.    Les résultats sont exactement les mêmes, puisque vous utilisez la même source de données. Cependant, les calculs sont effectués sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Les résultats sont ensuite renvoyés à votre station de travail locale à des fins de traçage.  
   
![histogram results](../../advanced-analytics/r-services/media/rsql-sue-histogramresults.jpg "histogram results")  

  
4.  Vous pouvez également appeler la fonction *rxCube* et transmettre les résultats à des fonctions R de traçage.  L’exemple suivant utilise *rxCube* pour calculer la moyenne de *fraudRisk* pour chaque combinaison de *numTrans* et *numIntlTrans* :  
  
    ```R  
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)   
    ```  
  
    Pour spécifier les groupes utilisés pour calculer les moyennes de groupe, utilisez la notation `F()`. Dans cet exemple, `F(numTrans):F(numIntlTrans)` indique que les entiers dans les variables _numTrans_ et _numIntlTrans_ doivent être traités comme des variables catégorielles, avec un niveau pour chaque valeur d’entier.  
  
    Étant donné que les niveaux faibles et élevés ont déjà été ajoutés à la source de données *sqlFraudDS* (à l’aide du paramètre *colInfo*), les niveaux sont automatiquement utilisés dans l’histogramme.  
  
5.  La valeur de retour de *rxCube* est par défaut un *objet rxCube* qui représente un tableau croisé. Toutefois, vous pouvez utiliser la fonction *rxResultsDF* pour convertir les résultats en une trame de données facilement exploitable dans l’une des fonctions de traçage standard de R.  
  
    ```R  
    cubePlot <- rxResultsDF(cube1)   
    ```  
  
    > [!TIP]  
    > Notez que la fonction *rxCube* inclut un argument facultatif, *returnDataFrame* = TRUE, que vous pouvez utiliser pour convertir les résultats en une trame de données directement. Par exemple :  
    >   
    > `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`  
    >   
    > Toutefois, la sortie de *rxResultsDF* est beaucoup plus propre et préserve le nom des colonnes sources.  
  
6.  Enfin, exécutez le code suivant pour créer une carte thermique en utilisant la fonction *levelplot* du package **lattice** inclus dans toutes les distributions de R.  
  
    ```R  
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)   
    ```  
  
    **Résultats**  
  
    ![scatterplot results](../../advanced-analytics/r-services/media/rsql-sue-scatterplotresults.jpg "scatterplot results")  
  
Même à partir de cette analyse rapide, vous pouvez voir que le risque de fraude augmente avec le nombre de transactions et le nombre de transactions internationales.

Pour plus d’informations sur la fonction *rxCube* et sur les analyses croisées en général, consultez [Data Summaries](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-summaries) (Synthèses de données).  
  
## Étape suivante  
[Créer des modèles &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/create-models-data-science-deep-dive.md)  
  
## Étape précédente  
[Leçon 2 : Créer et exécuter des scripts R &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
## Voir aussi  
[Immersion dans la science des données : utilisation des packages RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
