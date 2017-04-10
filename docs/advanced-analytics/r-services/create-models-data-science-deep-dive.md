---
title: "Cr&#233;er des mod&#232;les (Immersion dans la science des donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
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
ms.assetid: a195d5e2-72e2-4dd6-bf43-947312e4a52a
caps.latest.revision: 14
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Cr&#233;er des mod&#232;les (Immersion dans la science des donn&#233;es)
Maintenant que vous avez enrichi les données d’apprentissage, il est temps d’analyser les données en utilisant la régression linéaire. Les modèles linéaires sont un outil important dans le monde de la prédiction analytique et le package **RevoScaleR** de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] inclut un algorithme évolutif à hautes performances.  
  
## Créer un modèle de régression linéaire  
Vous allez créer un modèle linéaire simple qui estime le solde de carte de crédit du client, en utilisant comme variables indépendantes les valeurs des colonnes *gender* et *creditLine*.  
  
Pour cela, vous utilisez la nouvelle fonction *rxLinMod*, qui prend en charge les contextes de calcul à distance.  
  
1.  Créez une variable R pour stocker le modèle terminé et appelez la fonction *rxLinMod*, en passant la formule qui convient.  
  
    ```R  
    linModObj <- rxLinMod(balance ~ gender + creditLine,  data = sqlFraudDS)   
    ```  
  
2.   Pour afficher un résumé des résultats, appelez la fonction *summary* standard de R sur l’objet de modèle.  
  
     ```R  
     summary(linModObj)   
     ```  

Il peut vous paraître étrange qu’une simple fonction R comme **summary** fonctionne ici, puisque dans l’étape précédente, vous avez défini le contexte de calcul sur le serveur. Toutefois, même lorsque la fonction **rxLinMod** utilise le contexte de calcul à distance pour créer le modèle, il retourne également un objet qui contient le modèle pour votre station de travail locale et le stocke dans le répertoire partagé.

Par conséquent, vous pouvez exécuter des commandes R standard sur le modèle comme s’il avait été créé en utilisant le contexte « local ».
  
**Résultats**  
  
*Linear Regression Results for: balance ~ gender + creditLineData: sqlFraudDS (RxSqlServerData Data Source)*  
*Dependent variable(s): balance*  
*Total independent variables: 4 (Including number dropped: 1)*  
*Number of valid observations: 10000*  
*Number of missing observations: 0*    
*Coefficients: (1 not defined because of singularities)*      
*Estimate Std. Error t value Pr(>|t|) (Intercept)*   
*3253,575 71,194 45,700 2,22e-16*   
*gender=Male -88.813 78,360 -1,133 0.257*   
*gender=Female Dropped Dropped Dropped Dropped*   
*creditLine 95,379 3,862 24,694 2,22e-16*   
*Signif. codes: 0  0,001  0,01 ‘*’ 0,05 ‘.’ 0,1 ‘ ’ 1*  
  
*Residual standard error: 3812 on 9997 degrees of freedom*  
*Multiple R-squared: 0,05765*   
*Adjusted R-squared: 0,05746*   
*F-statistic: 305,8 on 2 and 9997 DF, p-value: < 2,2e-16*  
*Condition number: 1,0184*  
  
## Créer un modèle de régression logistique  
Vous allez maintenant créer un modèle de régression logistique qui indique si un client particulier présente un risque de fraude.  
  
Vous utilisez la fonction *rxLogit* (incluse dans le package **RevoScaleR**), qui prend en charge l’ajustement des modèles de régression logistique dans des contextes de calcul à distance.  
  
1.  Conservez le contexte de calcul tel quel. Vous continuez aussi à utiliser la même source de données.  
  
2.  Appelez la fonction *rxLogit*, puis passez la formule nécessaire pour définir le modèle.  
  
    ```R  
    logitObj <- rxLogit(fraudRisk ~ state + gender + cardholder + balance +      numTrans + numIntlTrans + creditLine, data = sqlFraudDS,      dropFirst = TRUE)   
    ```  
  
    Comme il s’agit d’un modèle de grande taille, contenant 60 variables indépendantes, y compris les trois variables factices qui sont supprimées, vous devrez peut-être attendre que le contexte de calcul retourne l’objet.  
    
    La raison pour laquelle la taille du modèle est si importante est que, dans R (et dans le package **RevoScaleR**), chaque niveau d’une variable de facteur de catégorie est automatiquement traité comme une variable factice distincte.  
  
3.  Pour afficher un résumé du modèle retourné, appelez la fonction R *summary*.  
  
    ```R  
    summary(logitObj)  
    ```  
  
**Résultats partiels**  
  
*Logistic Regression Results for: fraudRisk ~ state + gender +     cardholder + balance + numTrans + numIntlTrans + creditLine*   
*Data: sqlFraudDS (RxSqlServerData Data Source)*   
*Dependent variable(s): fraudRisk*   
*Total independent variables: 60 (Including number dropped: 3)*   
*Number of valid observations: 10000 -2\*  
*LogLikelihood: 2032,8699 (Residual deviance on 9943 degrees of freedom)*  
*Coefficients:*   
*Estimate Std. Error z value Pr(>|z|)     (Intercept)*  
*-8,627e+00  1,319e+00  -6,538 6,22e-11 \*\*\*   
state=AK                Dropped    Dropped Dropped  Dropped       
state=AL             -1,043e+00  1,383e+00  -0,754   0,4511* (other states omitted) *gender=Male             Dropped    Dropped Dropped  Dropped*  
*gender=Female         7,226e-01  1,217e-01   5,936 2.92e-09 \*\*\**  
*cardholder=Principal    Dropped    Dropped Dropped  Dropped*       
*cardholder=Secondary  5,635e-01  3,403e-01   1,656   0,0977 .*     
*balance               3,962e-04  1,564e-05  25,335 2,22e-16 \*\*\**  
*numTrans              4,950e-02  2,202e-03  22,477 2,22e-16 \*\*\**  
*numIntlTrans          3,414e-02  5,318e-03   6,420 1,36e-10 \*\*\**  
*creditLine            1,042e-01  4,705e-03  22,153 2,22e-16 \*\*\**   
*---*   
*Signif. codes:  0 ‘\*\*\*’ 0,001 ‘\*\*’ 0,01 ‘\*’ 0,05 ‘.’ 0,1 ‘ ’ 1*   
*Condition number of final variance-covariance matrix: 3997,308*   
*Number of iterations: 15*  
  
## Étape suivante  
[Affecter un score à de nouvelles données &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/score-new-data-data-science-deep-dive.md)  
  
## Étape précédente  
[Visualiser des données SQL Server à l’aide de R &#40;Immersion dans la science des données&#41;](../../advanced-analytics/r-services/visualize-sql-server-data-using-r-data-science-deep-dive.md)  
  
## Voir aussi  
[Immersion dans la science des données : utilisation des packages RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
  
  
