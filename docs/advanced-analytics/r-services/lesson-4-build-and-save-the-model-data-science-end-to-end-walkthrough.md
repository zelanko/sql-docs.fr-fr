---
title: "Le&#231;on 4 : Cr&#233;er et enregistrer le mod&#232;le (proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "11/22/2016"
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
ms.assetid: 69b374c1-2042-4861-8f8b-204a6297c0db
caps.latest.revision: 20
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 18
---
# Le&#231;on 4 : Cr&#233;er et enregistrer le mod&#232;le (proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es)
Dans cette leçon, vous allez découvrir comment créer un modèle d’apprentissage automatique et enregistrer le modèle dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="creating-a-classification-model"></a>Création d’un modèle de classification  
Le modèle que vous allez générer est un classifieur binaire qui évalue la probabilité que le conducteur obtienne un pourboire lors d’un trajet donné. Vous allez utiliser la source de données que vous avez créée dans la leçon précédente, `featureDataSource,` , pour former le classifieur de pourboires, à l’aide de la régression logistique.  
  
Voici les caractéristiques que vous utiliserez dans le modèle :  
  
-   passenger_count  
  
-   trip_distance  
  
-   trip_time_in_secs  
  
-   direct_distance  

### <a name="create-the-model-using-rxlogit"></a>Créer le modèle à l’aide de rxLogit  
1.  Appelez la fonction *rxLogit*, comprise dans le package **RevoScaleR**, pour créer un modèle de régression logistique.  
  
    ```R  
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource))    
    ```  
  
2.  Après avoir créé le modèle, vous devez l’examiner à l’aide de la fonction `summary` et afficher les coefficients.  
  
    ```  
    summary(logitObj)  
    ```  

     *Résultats*

     *Logistic Regression Results for: tipped ~ passenger_count + trip_distance + trip_time_in_secs +*  
     *direct_distance*  
     *Data: featureDataSource (RxSqlServerData Data Source)*  
     *Dependent variable(s): tipped*  
     *Total independent variables: 5*   
     *Number of valid observations: 17068*  
     *Number of missing observations: 0*   
     *-2\*LogLikelihood: 23540.0602 (Residual deviance on 17063 degrees of freedom)*  
     *Coefficients:*  
     *Estimate Std. Error z value Pr(>|z|)*   
     *(Intercept)       -2.509e-03  3.223e-02  -0.078  0.93793*   
     *passenger_count   -5.753e-02  1.088e-02  -5.289 1.23e-07 \*\*\**  
     *trip_distance     -3.896e-02  1.466e-02  -2.658  0.00786 \*\**   
     *trip_time_in_secs  2.115e-04  4.336e-05   4.878 1.07e-06 \*\*\**  
     *direct_distance    6.156e-02  2.076e-02   2.966  0.00302 \*\**   
     *---*  
     *Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1*  
     *Condition number of final variance-covariance matrix: 48.3933*   
     *Number of iterations: 4*  
  
### <a name="use-the-logistic-regression-model-for-scoring"></a>Utiliser le modèle de régression logistique pour calculer les scores  
Maintenant que le modèle est créé, vous pouvez l’utiliser pour évaluer la probabilité que le conducteur obtienne un pourboire lors d’un trajet donné.  
  
1.  Tout d’abord, définissez l’objet de données à utiliser pour stocker les résultats des calculs de scores.  
  
    ```R  
    scoredOutput <- RxSqlServerData(  
      connectionString = connStr,  
      table = "taxiScoreOutput"  )  
    ```  
    + Pour simplifier cet exemple, l’entrée du modèle de régression logistique est le même `featureDataSource` que celui utilisé pour former le modèle.  Plus généralement, vous aurez sans doute de nouvelles données avec lesquelles calculer les scores, ou vous aurez peut-être mis de côté certaines données de test et de formation.  
  
    + Les résultats de la prédiction sont enregistrés dans la table _taxiscoreOutput_. Notez que le schéma de cette table n’est pas défini quand vous la créez à l’aide de `rxSqlServerData`, mais est obtenu à partir de l’objet de sortie *scoredOutput* de `rxPredict`.  
  
    + Pour créer la table qui stocke les valeurs prédites, la connexion SQL qui exécute la fonction de données `rxSqlServer` doit disposer de privilèges DDL dans la base de données. Si la connexion ne peut pas créer de table, l’instruction échoue.  
  
2.  Appelez la fonction *rxPredict* pour générer les résultats.  
  
    ```R  
    rxPredict(modelObject = logitObj, data = featureDataSource, outData = scoredOutput,   
                       predVarNames = "Score", type = "response",   
                       writeModelVars = TRUE, overwrite = TRUE)  
    ```  

  
## <a name="plotting-model-accuracy"></a>Précision du modèle de traçage  
Pour obtenir une idée de la précision du modèle, vous pouvez utiliser la fonction *rxRocCurve* pour tracer la courbe Receiver Operating Curve. *rxRocCurve* étant l’une des nouvelles fonctions fournies par le package RevoScaleR qui prend en charge les contextes de calcul distants, vous avez deux options :  
  
+ Vous pouvez utiliser la fonction `rxRocCurve` pour exécuter le tracé dans le contexte de l’ordinateur distant, puis retourner le tracé à votre client local.
+ Vous pouvez également importer les données sur votre ordinateur client R et utiliser d’autres fonctions de traçage R pour créer le graphique de performances.  
  
Dans cette section, vous allez utiliser les deux techniques.  
  
### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Exécuter un tracé dans le contexte de calcul distant (SQL Server)  
  
1.  Appelez la fonction *rxRocCurve* et fournissez les données définies précédemment en tant qu’entrée.  
  
    ```R  
    rxRocCurve( "tipped", "Score", scoredOutput)  
    ```  
  
    Notez que vous devez également spécifier la colonne d’étiquette « tipped » (la variable que vous essayez de prédire) et le nom de la colonne qui stocke la prédiction (_Score_).  
  
2.  Affichez le graphique généré en ouvrant le périphérique graphique R ou en cliquant sur la fenêtre **Tracer** dans RStudio.  
  
    ![ROC plot for the model](../../advanced-analytics/r-services/media/rsql-e2e-rocplot.png "ROC plot for the model")  

    Le graphique est créé dans le contexte de calcul distant, puis retourné à votre environnement R.   
    
### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Créer les tracés dans le contexte de calcul local à l’aide de données de SQL Server  
  
1.  Utilisez la fonction *rxImport* pour ajouter les données spécifiées à votre environnement R local.  
  
    ```R  
    scoredOutput = rxImport(scoredOutput)  
    ```  
  
2.  Après avoir chargé les données dans la mémoire locale, vous pouvez appeler la bibliothèque **ROCR** pour créer des prédictions et générer le tracé.  
  
    ```R  
    library('ROCR')  
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped)  
  
    acc.perf = performance(pred, measure = 'acc')  
    plot(acc.perf)  
    ind = which.max( slot(acc.perf, 'y.values')[[1]] )  
    acc = slot(acc.perf, 'y.values')[[1]][ind]  
    cutoff = slot(acc.perf, 'x.values')[[1]][ind]  
    ```  
  
3.  Le tracé suivant est généré dans les deux cas.  
  
    ![plotting model performance using R](../../advanced-analytics/r-services/media/rsql-e2e-performanceplot.png "plotting model performance using R")  
  
## <a name="deploying-a-model"></a>Déploiement d’un modèle  

Après avoir créé un modèle et vous être assuré que ses performances vous conviennent, vous souhaiterez peut-être *l’opérationnaliser*. Étant donné que [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] vous permet d’appeler un modèle R à l’aide d’une procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] , il est très facile d’utiliser R dans une application cliente.  
  
Toutefois, avant de pouvoir appeler le modèle à partir d’une application externe, vous devez l’enregistrer dans la base de données utilisée pour la production. Dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], les modèles formés sont stockés sous forme binaire, dans une seule colonne de type **varbinary(max)**.

Par conséquent, déplacer un modèle formé depuis R vers SQL Server comprend les étapes suivantes :  
  
+ Sérialisation du modèle dans une chaîne hexadécimale
+ Transmission de l’objet sérialisé à la base de données
+ Enregistrement du modèle dans une colonne varbinary(max)  
  
Dans cette section, vous allez découvrir comment rendre le modèle persistant et comment l’appeler pour effectuer des prédictions.  
  
### <a name="serialize-the-model"></a>Sérialiser le modèle  
  
+  Dans votre environnement R local, sérialisez le modèle et enregistrez-le dans une variable.  
  
    ```R  
    modelbin <- serialize(logitObj, NULL)  
    modelbinstr=paste(modelbin, collapse="")  
    ```  
  
    La fonction *serialize* est comprise dans le package R de **base** et fournit une interface de bas niveau simple pour sérialiser des connexions. Pour plus d’informations, consultez [http://www.inside-r.org/r-doc/base/serialize](http://www.inside-r.org/r-doc/base/serialize).  
  
### <a name="move-the-model-to-sql-server"></a>Déplacer le modèle vers SQL Server

+ Ouvrez une connexion ODBC et appelez une procédure stockée pour stocker la représentation binaire du modèle dans une colonne de la base de données. 
  
    ```R  
    library(RODBC)  
    conn <- odbcDriverConnect(connStr )  
  
    # persist model by calling a stored procedure from SQL  
    q<-paste("EXEC PersistModel @m='", modelbinstr,"'", sep="")  
    sqlQuery (conn, q)    
    ```  

L’enregistrement d’un modèle dans une table nécessite uniquement une instruction INSERT. Toutefois, pour des raisons de simplification, nous utilisons ici la procédure stockée _PersistModel_. 
 
À titre de référence, voici le code complet de la procédure stockée :  
  
```tsql  
CREATE PROCEDURE [dbo].[PersistModel]  @m nvarchar(max)  
AS  
BEGIN  
        -- SET NOCOUNT ON added to prevent extra result sets from  
        -- interfering with SELECT statements.  
        SET NOCOUNT ON;  
        insert into nyc_taxi_models (model) values (convert(varbinary(max),@m,2))  
END   
```  
> [!TIP] Nous vous recommandons de créer des fonctions d’assistance telles que cette procédure stockée pour faciliter la gestion et la mise à jour de vos modèles R dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
### <a name="invoke-the-saved-model"></a>Appeler le modèle enregistré  
Une fois que vous avez enregistré le modèle dans la base de données, vous pouvez l’appeler directement à partir de code [!INCLUDE[tsql](../../includes/tsql-md.md)], à l’aide de la procédure stockée système [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  
  
Par exemple, pour générer des prédictions, il vous suffit de vous connecter à la base de données et d’exécuter une procédure stockée qui utilise le modèle enregistré comme entrée, avec des données d’entrée.  
  
Toutefois, si vous avez un modèle que vous utilisez souvent, il est plus facile d’encapsuler la requête d’entrée et l’appel au modèle, ainsi que tout autre paramètre, dans une procédure stockée personnalisée.  
  
Dans la leçon suivante, vous allez découvrir comment effectuer le calcul de scores sur le modèle enregistré à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 5 : Déployer et utiliser le modèle &#40;procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-5-deploy-and-use-the-model-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Leçon précédente  
[Leçon 3 : Créer des caractéristiques de données &#40;procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-3-create-data-features-data-science-end-to-end-walkthrough.md)  
  
  
  
