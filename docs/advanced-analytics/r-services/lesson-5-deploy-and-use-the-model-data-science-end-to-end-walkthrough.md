---
title: "Le&#231;on 5 : D&#233;ployer et utiliser le mod&#232;le (proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es) | Microsoft Docs"
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
ms.assetid: f28a7aac-6d08-4781-ad28-b48d18cc16a0
caps.latest.revision: 17
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 17
---
# Le&#231;on 5 : D&#233;ployer et utiliser le mod&#232;le (proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es)
Dans cette leçon, vous allez utiliser vos modèles R dans un environnement de production, en encapsulant le modèle persistant dans une procédure stockée. Vous pourrez ensuite appeler la procédure stockée à partir de R ou de n’importe quel langage de programmation d’application prenant en charge [!INCLUDE[tsql](../../includes/tsql-md.md)] (tel que C#, Java, Python, etc.), pour utiliser le modèle afin d’effectuer des prédictions sur de nouvelles observations.  
  
Vous pouvez appeler un modèle à des fins d’évaluation de deux façons différentes :  
  
-   Le**mode d’évaluation par lot** vous permet de créer plusieurs prédictions basées sur une entrée à partir d’une requête SELECT.  
  
-   Quant au**mode d’évaluation individuelle** , vous pouvez l’utiliser pour créer des prédictions une à la fois, en transmettant un ensemble de valeurs de caractéristiques pour un cas particulier à la procédure stockée, qui retourne une prédiction unique ou une autre valeur comme résultat.  
  
Vous allez apprendre à créer des prédictions à l’aide des deux méthodes d’évaluation (individuelle et par lot).  
  
## <a name="batch-scoring"></a>Évaluation par lot  
Pour plus de commodité, vous pouvez utiliser une procédure stockée qui a été créée quand vous avez exécuté le script PowerShell à la leçon 1. Elle effectue les actions suivantes :  
  
-   Elle obtient un jeu de données d’entrée sous la forme d’une requête SQL.    
-   Elle appelle le modèle de régression logistique formé que vous avez enregistré à la leçon précédente.    
-   Elle prédit la probabilité que le chauffeur obtienne un pourboire.  
  
### <a name="use-the-stored-procedure-predicttipbatchmode"></a>Utilisez la procédure stockée PredictTipBatchMode

1. Prenez une minute pour vérifier le script qui définit la procédure stockée, *PredictTipBatchMode*. Il illustre plusieurs aspects de la façon dont un modèle peut être mis en œuvre à l’aide de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
    ```tsql  
    CREATE PROCEDURE [dbo].[PredictTipBatchMode]   
    @input nvarchar(max)  
    AS  
    BEGIN  
  
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  FROM nyc_taxi_models);  
      EXEC sp_execute_external_script @language = N'R',  
         @script = N'  
           mod <- unserialize(as.raw(model));  
           print(summary(mod))  
           OutputDataSet<-rxPredict(modelObject = mod, 
               data = InputDataSet, 
               outData = NULL, 
               predVarNames = "Score", type = "response", 
               writeModelVars = FALSE, overwrite = TRUE);  
           str(OutputDataSet)  
           print(OutputDataSet)',  
      @input_data_1 = @input,  
      @params = N'@model varbinary(max)',  
      @model = @lmodel2  
      WITH RESULT SETS ((Score float));  
    END    
    ```  

    + Notez l’instruction SELECT qui appelle le modèle stocké. Vous pouvez stocker n’importe quel modèle formé dans une table SQL, à l’aide d’une colonne de type **varbinary (max)**. Dans ce code, le modèle est récupéré de la table, stocké dans la variable SQL _@lmodel2_, puis passé comme paramètre *mod* à la procédure stockée système [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
    + Les données d’entrée utilisées pour l’évaluation sont passées à la procédure stockée sous forme de chaîne.  
  
        Pour définir les données d’entrée pour ce modèle spécifique, créez une requête qui retourne des données valides. À mesure que les données sont récupérées de la base de données, elles sont stockées dans une trame de données appelée *InputDataSet*. Toutes les lignes dans cette trame de données sont utilisées pour l’évaluation par lot.
        + *InputDataSet* est le nom par défaut des données d’entrée de la procédure [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) ; vous pouvez définir un autre nom de variable si nécessaire.
        + Pour générer les scores, la procédure stockée appelle la fonction *rxPredict* à partir de la bibliothèque **RevoScaleR**.
    + La valeur de retour de la procédure stockée, *Score*, est une probabilité prédite que le chauffeur obtienne un pourboire.  
  
2.  Si vous le souhaitez, vous pouvez facilement appliquer un filtre aux valeurs retournées pour les regrouper selon qu’un pourboire est obtenu ou non.  Par exemple, une probabilité de moins de 0,5 signifie qu’aucun pourboire n’est susceptible d’être obtenu.  
  
3.  Appelez la procédure stockée en mode batch :  
  
    ```R  
    input = "N' 
      SELECT TOP 10 
          a.passenger_count AS passenger_count,   
          a.trip_time_in_secs AS trip_time_in_secs,  
          a.trip_distance AS trip_distance,  
          a.dropoff_datetime AS dropoff_datetime,    
          dbo.fnCalculateDistance(
            pickup_latitude, 
            pickup_longitude, 
            dropoff_latitude,
            dropoff_longitude) AS direct_distance   
      FROM  
      
      (SELECT medallion, hack_license, pickup_datetime,   
      passenger_count,trip_time_in_secs,trip_distance,    
      dropoff_datetime, pickup_latitude, pickup_longitude,   
      dropoff_latitude, dropoff_longitude from nyctaxi_sample)a  
      
      LEFT OUTER JOIN  
 
      ( SELECT medallion, hack_license, pickup_datetime 
        FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b  

      ON a.medallion=b.medallion 
        AND a.hack_license=b.hack_license 
        AND a.pickup_datetime=b.pickup_datetime  

      WHERE b.medallion is null  
    '"  
    q<-paste("EXEC PredictTipBatchMode @inquery = ", input, sep="")  
    sqlQuery (conn, q)  
  
    ```  
  
## <a name="single-row-scoring"></a>Ligne unique de score  

Au lieu d’utiliser une requête pour transmettre les valeurs d’entrée au modèle R enregistré, vous pouvez fournir les caractéristiques en tant qu’arguments à la procédure stockée.  

### <a name="use-the-stored-procedure-predicttipsinglemode"></a>Utilisez la procédure stockée PredictTipSingleMode
1.  Prenez une minute pour examiner le code suivant pour la procédure stockée, *PredictTipSingleMode*, qui doit déjà être créé dans votre base de données.  
  
    ```tsql  
    CREATE PROCEDURE [dbo].[PredictTipSingleMode] @passenger_count int = 0,  
    @trip_distance float = 0,  
    @trip_time_in_secs int = 0,  
    @pickup_latitude float = 0,  
    @pickup_longitude float = 0,  
    @dropoff_latitude float = 0,  
    @dropoff_longitude float = 0  
    AS  
    BEGIN  
      DECLARE @inquery nvarchar(max) = N'  
        SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, 
            @trip_distance,  
            @trip_time_in_secs,  
            @pickup_latitude,  
            @pickup_longitude,  
            @dropoff_latitude,  
            @dropoff_longitude)  
        '  
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);  

      EXEC sp_execute_external_script @language = N'R',  @script = N'  
            mod <- unserialize(as.raw(model));  
            print(summary(mod))  
            OutputDataSet<-rxPredict(
                     modelObject = mod, 
                     data = InputDataSet, 
                     outData = NULL,   
                     predVarNames = "Score", 
                     type = "response", 
                     writeModelVars = FALSE, 
                     overwrite = TRUE);  
            str(OutputDataSet)  
            print(OutputDataSet)  
            ',  
      @input_data_1 = @inquery,  
      @params = N'@model varbinary(max),
                @passenger_count int,
                @trip_distance float,
                @trip_time_in_secs int ,  
                @pickup_latitude float ,
                @pickup_longitude float ,
                @dropoff_latitude float ,
                @dropoff_longitude float',  
                @model = @lmodel2,  
                @passenger_count =@passenger_count ,  
                @trip_distance=@trip_distance,  
                @trip_time_in_secs=@trip_time_in_secs,    
                @pickup_latitude=@pickup_latitude,  
                @pickup_longitude=@pickup_longitude,  
                @dropoff_latitude=@dropoff_latitude,  
                @dropoff_longitude=@dropoff_longitude  
      WITH RESULT SETS ((Score float));  
    END    
    ```  
  
    Cette procédure stockée prend des valeurs de caractéristiques en entrée, telles que le nombre de passagers et la distance du trajet, évalue ces caractéristiques à l’aide du modèle R stocké et génère un score.  
  
### <a name="call-the-stored-procedure-and-pass-parameters"></a>Appelez la procédure stockée et transférez les paramètres

1. Dans SQL Server Management Studio, vous pouvez utiliser la méthode [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXEC** pour appeler la procédure stockée et la transférer aux entrées requises. .  
    ```tsql  
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303   
    ```  
  
    Les valeurs transmises ici correspondent, respectivement, aux variables _passenger_count_, _trip_distance_, _trip_time_in_secs_, _pickup_latitude_, _pickup_longitude_, _dropoff_latitude_et _dropoff_longitude_.  
  
2.  Pour exécuter ce même appel à partir du code R, il vous suffit de définir une variable R qui contient l’appel de procédure stockée complet. 
  
    ```R  
    q = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 "  
    ```  
  
    Les valeurs transmises ici correspondent, respectivement, aux variables _passenger_count_, _trip_distance_, _trip_time_in_secs_, _pickup_latitude_, _pickup_longitude_, _dropoff_latitude_et _dropoff_longitude_.  
  
### <a name="generate-scores"></a>Générer des scores

1. Appelez la fonction *sqlQuery* du package **RODBC**, puis transmettez la chaîne de connexion et la variable de type chaîne contenant l’appel de procédure stockée.  
  
    ```R  
    # predict with stored procedure in single mode  
    sqlQuery (conn, q)   
    ```  
  
    Pour plus d’informations sur **RODBC**, consultez [http://www.inside-r.org/packages/cran/RODBC/docs/sqlQuery](http://www.inside-r.org/packages/cran/RODBC/docs/sqlQuery).  
  
## <a name="conclusion"></a>Conclusion  
Après avoir appris à utiliser des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et à rendre persistants des modèles R formés pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devriez pouvoir assez facilement créer des modèles supplémentaires basés sur ce jeu de données. Par exemple, vous pouvez essayer de créer des modèles comme ceux-ci :  
  
-   Un modèle de régression qui prédit le montant du pourboire    
-   Un modèle de classification multiclasse qui prédit si le pourboire est petit, moyen ou élevé.  

Nous vous recommandons également de consulter certains de ces exemples et ressources supplémentaires : 
+ [Scénarios de science des données et modèles de solutions](../../advanced-analytics/r-services/data-science-scenarios-and-solution-templates.md)
+ [Analytique avancée en base de données](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)
+ [Microsoft R - Plongée dans l’analyse des données](https://msdn.microsoft.com/microsoft-r/data-analysis-in-microsoft-r)
+ [Ressources supplémentaires](https://msdn.microsoft.com/microsoft-r/microsoft-r-more-resources)
## <a name="previous-lesson"></a>Leçon précédente  
[Leçon 4 : Créer et enregistrer le modèle &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-4-build-and-save-the-model-data-science-end-to-end-walkthrough.md)  
  
## <a name="see-also"></a>Voir aussi  
[Didacticiels pour SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
