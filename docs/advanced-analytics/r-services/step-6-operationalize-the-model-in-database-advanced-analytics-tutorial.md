---
title: "&#201;tape 6 : Rendre le mod&#232;le op&#233;rationnel (didacticiel sur l’analytique avanc&#233;e en base de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
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
  - "TSQL"
ms.assetid: 52b05828-11f5-4ce3-9010-59c213a674d1
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# &#201;tape 6 : Rendre le mod&#232;le op&#233;rationnel (didacticiel sur l’analytique avanc&#233;e en base de donn&#233;es)
Lors de cette étape, vous allez découvrir comment *rendre le modèle opérationnel* à l’aide d’une procédure stockée. Cette procédure stockée peut être appelée directement par d’autres applications, pour effectuer des prédictions sur de nouvelles observations.  
  
Lors de cette étape, vous allez découvrir deux méthodes d’appel d’un modèle R à partir d’une procédure stockée :  
  
-   **Mode de calcul de score du lot** : utiliser une requête SELECT pour fournir plusieurs lignes de données. La procédure stockée retourne une table d’observations correspondant aux cas d’entrée.  
  
-   **Mode de calcul de score individuel** : passer un ensemble de valeurs de paramètres en tant qu’entrée.  La procédure stockée retourne une seule ligne ou valeur.  
  
Tout d’abord, examinons le fonctionnement du calcul de score en général.  
  
## Calcul de score de base  
La procédure stockée _PredictTip_ illustre la syntaxe de base pour l’encapsulation d’un appel de prédiction dans une procédure stockée.  
  
```  
CREATE PROCEDURE [dbo].[PredictTip] @inquery nvarchar(max)  
AS  
BEGIN  
  
  DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  
  FROM nyc_taxi_models);  
  EXEC sp_execute_external_script @language = N'R',  
                                  @script = N'  
mod <- unserialize(as.raw(model));  
print(summary(mod))  
OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,   
          predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
str(OutputDataSet)  
print(OutputDataSet)  
',  
                                  @input_data_1 = @inquery,  
                                  @params = N'@model varbinary(max)',  
                                  @model = @lmodel2  
  WITH RESULT SETS ((Score float));  
  
END  
  
GO  
  
```  
  
-   L’instruction SELECT obtient le modèle sérialisé à partir de la base de données et stocke le modèle dans la variable R `mod` pour un traitement ultérieur à l’aide de R.  
  
-   Les nouveaux cas dont le score sera calculé sont obtenus à partir de la requête [!INCLUDE[tsql](../../includes/tsql-md.md)] spécifiée dans `@inquery`, le premier paramètre de la procédure stockée. Lors de la lecture des données de requête, les lignes sont enregistrées dans la trame de données par défaut, `InputDataSet`. Cette trame de données est passée à la fonction `rxPredict` en R, qui génère les scores.  
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,            predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`  
  
    Une trame de données ne pouvant contenir qu’une seule ligne, vous pouvez utiliser le même code pour le calcul de score unique ou de lot.  
  
-   La valeur retournée par la fonction `rxPredict` est une valeur **float** qui représente la probabilité qu’un pourboire (d’un montant quelconque) soit donné.  
  
## Calcul de score du lot à l’aide d’une requête SELECT  
Examinons maintenant le fonctionnement du calcul de score du lot.  
  
1.  Commençons par obtenir un plus petit jeu de données d’entrée à utiliser.  
  
    ```  
    select top 10 a.passenger_count as passenger_count,   
        a.trip_time_in_secs as trip_time_in_secs,  
        a.trip_distance as trip_distance,  
        a.dropoff_datetime as dropoff_datetime,    
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) as direct_distance   
    from  
    (  
        select medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance,    
            dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude  
        from nyctaxi_sample  
    )a  
    left outer join  
    (  
    select medallion, hack_license, pickup_datetime  
    from nyctaxi_sample  
    tablesample (70 percent) repeatable (98052)  
    )b  
    on a.medallion=b.medallion and a.hack_license=b.hack_license and a.pickup_datetime=b.pickup_datetime  
    where b.medallion is null  
    ```  
  
    Cette requête crée une liste « top 10 » des trajets avec le nombre de passagers et d’autres caractéristiques nécessaires pour établir une prédiction.  
  
 **Résultats**  
  
*passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance*  
*1  283 0.7 2013-03-27 14:54:50.000   0.5427964547*  
*1  289 0.7 2013-02-24 12:55:29.000   0.3797099614*  
*1  214 0.7 2013-06-26 13:28:10.000   0.6970098661*  
*1  276 0.7 2013-06-27 06:53:04.000   0.4478814362*  
*1  282 0.7 2013-02-21 07:59:54.000   0.5340645749*  
*1  260 0.7 2013-03-27 15:40:49.000   0.5513900727*  
*1  230 0.7 2013-02-05 09:47:59.000   0.5161578519*  
*1  250 0.7 2013-05-08 14:35:51.000   0.5626440915*  
*1  280 0.7 2013-05-11 12:22:01.000   0.5598517959*  
*1  308 0.7 2013-04-10 08:06:00.000   0.4478814362*  
  
Vous utiliserez cette requête comme entrée de la procédure stockée, _PredictTipBatchMode_, qui a été fournie dans le cadre du téléchargement.  
  
2.  Tout d’abord, prenez une minute pour examiner le code de la procédure stockée _PredictTipBatchMode_ dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
    ```  
    /****** Object:  StoredProcedure [dbo].[PredictTipBatchMode]  ******/  
    SET ANSI_NULLS ON  
    GO  
    SET QUOTED_IDENTIFIER ON  
    GO  
  
    CREATE PROCEDURE [dbo].[PredictTipBatchMode] @inquery nvarchar(max)  
    AS  
    BEGIN  
  
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  
      FROM nyc_taxi_models);  
      EXEC sp_execute_external_script @language = N'R',  
                                      @script = N'  
    mod <- unserialize(as.raw(model));  
    print(summary(mod))  
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,   
              predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
    str(OutputDataSet)  
    print(OutputDataSet)  
    ',  
                                      @input_data_1 = @inquery,  
                                      @params = N'@model varbinary(max)',  
                                      @model = @lmodel2  
      WITH RESULT SETS ((Score float));  
  
    END  
    ```  
  
3.  Pour créer des prédictions, vous allez fournir le texte de requête dans une variable et la passer en tant que paramètre à la procédure stockée, à l’aide d’une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] comme suit.  
  
    ```  
    -- Specify input query  
  
    DECLARE @query_string nvarchar(max)  
    SET @query_string='  
    select top 10 a.passenger_count as passenger_count,   
        a.trip_time_in_secs as trip_time_in_secs,  
        a.trip_distance as trip_distance,  
        a.dropoff_datetime as dropoff_datetime,    
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) as direct_distance   
    from  
        select medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance,    
            dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude  
        from nyctaxi_sample  
    )a  
    left outer join  
    (  
    select medallion, hack_license, pickup_datetime  
    from nyctaxi_sample  
    tablesample (70 percent) repeatable (98052)  
    )b  
    on a.medallion=b.medallion and a.hack_license=b.hack_license and a.pickup_datetime=b.pickup_datetime  
    where b.medallion is null'  
  
    -- Call stored procedure for scoring  
    EXEC [dbo].[PredictTip] @inquery = @query_string;  
  
    ```  
  
4.  La procédure stockée retourne une série de valeurs qui représentent la prédiction pour chacun des 10 principaux trajets. Si l’on examine les valeurs d’entrée, on constate que les 10 principaux trajets sont des trajets à un seul passager avec une distance relativement courte. D’après les données, le conducteur a très peu de chances de recevoir un pourboire durant ces trajets.  
  
    Plutôt que de retourner simplement les résultats « pourboire/pas de pourboire », vous pouvez aussi retourner le score de probabilité pour la prédiction, puis appliquer une clause WHERE aux valeurs de la colonne _Score_ pour classer le score comme « susceptible de donner lieu à un pourboire » ou « peu susceptible de donner lieu à un pourboire », à l’aide d’une valeur de seuil comme 0,5 ou 0,7. Cette étape n’est pas incluse dans la procédure stockée, mais elle est facile à implémenter.  
  
## Calculer le score de lignes spécifiques  
Parfois, vous souhaitez transmettre des valeurs spécifiques à partir d’une application, et obtenir un résultat unique basé sur ces valeurs. Par exemple, vous pouvez configurer une feuille de calcul Excel, une application web ou un rapport Reporting Services pour appeler la procédure stockée et fournir des entrées tapées ou sélectionnées par les utilisateurs.  
  
Dans cette section, vous allez découvrir comment créer des prédictions uniques à l’aide d’une procédure stockée.  
  
1.  Prenez une minute pour examiner le code de la procédure stockée _PredictTipSingleMode_, inclus dans le téléchargement.  
  
    ```  
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
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  
      FROM nyc_taxi_models);  
      EXEC sp_execute_external_script @language = N'R',  
                                      @script = N'  
    mod <- unserialize(as.raw(model));  
    print(summary(mod))  
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL,   
              predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
    str(OutputDataSet)  
    print(OutputDataSet)  
    ',  
    @input_data_1 = @inquery,  
    @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,@trip_time_in_secs int ,  
    @pickup_latitude float ,@pickup_longitude float ,@dropoff_latitude float ,@dropoff_longitude float',  
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
  
    -   Cette procédure stockée accepte plusieurs valeurs uniques comme entrée, telles que le nombre de passagers, la distance du trajet, et ainsi de suite.  
  
        Si vous appelez la procédure stockée à partir d’une application externe, vérifiez que les données répondent aux critères du modèle R. Vous pourriez par exemple vérifier que les données d’entrée peuvent être transtypées ou converties en un type de données R, ou valider le type de données et la longueur des données. Pour plus d’informations, consultez [Utilisation des types de données R](https://msdn.microsoft.com/library/mt590948.aspx).  
  
    -   La procédure stockée crée un score basé sur le modèle R stocké.  
  
2.  Essayez-la en fournissant les valeurs manuellement.  
  
    Ouvrez une nouvelle fenêtre **Requête** et appelez la procédure stockée en tapant des paramètres pour chacune des colonnes de caractéristiques.  
  
    ```  
  
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303  
  
    ```  
  
    Les valeurs correspondent à ces colonnes de caractéristiques, dans l’ordre :  
  
    -   *trip_time_in_secs*  
    -   *pickup_latitude*  
    -   *pickup_longitude*  
    -   *dropoff_latitude*  
    -   *dropoff_longitude*  
  
3.  Les résultats indiquent que la probabilité de recevoir un pourboire est très faible sur ces 10 principaux trajets, qui sont tous des trajets à un seul passager sur une distance relativement courte.  
  
## Conclusions  
Dans ce didacticiel, vous avez découvert comment utiliser du code R incorporé dans des procédures stockées. L’intégration à [!INCLUDE[tsql](../../includes/tsql-md.md)] simplifie grandement le déploiement de modèles R pour la prédiction et l’incorporation de la reformation de modèle dans le cadre d’un workflow de données d’entreprise.  
  
  
## Étape précédente  
[Étape 4 : Créer des caractéristiques de données à l’aide de T-SQL](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)  
  
## Voir aussi  
[Analytique avancée en base de données pour les développeurs SQL &#40;Didacticiel&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Didacticiels pour SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
