---
title: "&#201;tape 4 : Cr&#233;er des caract&#233;ristiques de donn&#233;es &#224; l’aide de T-SQL (Didacticiel sur l’analytique avanc&#233;e en base de donn&#233;es) | Microsoft Docs"
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
ms.assetid: 5b2f4c44-6192-40df-abf1-fc983844f1d0
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# &#201;tape 4 : Cr&#233;er des caract&#233;ristiques de donn&#233;es &#224; l’aide de T-SQL (Didacticiel sur l’analytique avanc&#233;e en base de donn&#233;es)
Après plusieurs séries d’exploration de données, vous avez recueilli des informations utiles grâce aux données et vous êtes prêt à passer à *l’ingénierie des caractéristiques*. Ce processus de création de caractéristiques à partir des données brutes est une étape essentielle de la modélisation de l’analytique avancée.  
  
Lors de cette étape, vous allez découvrir comment créer des caractéristiques à partir de données brutes en utilisant une fonction [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ensuite, vous appellerez cette fonction à partir d’une procédure stockée pour créer une table qui contient les valeurs des caractéristiques.  
  
## Définir la fonction  
Les valeurs de distance indiquées dans les données d’origine sont basées sur la distance signalée au compteur, et ne représente pas nécessairement la distance géographique ou la distance parcourue. Ainsi, vous devrez calculer la distance directe entre les lieux de prise en charge et de dépose, en utilisant les coordonnées disponibles dans le dataset source « NYC Taxi ». Vous pouvez pour cela utiliser la [formule de Haversine](https://en.wikipedia.org/wiki/Haversine_formula) dans une fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] personnalisée.  
  
Vous allez utiliser une fonction T-SQL personnalisée, _fnCalculateDistance_, pour calculer la distance à l’aide de la formule de Haversine, et utiliser une seconde fonction T-SQL personnalisée, _fnEngineerFeatures_, pour créer une table contenant toutes les caractéristiques.  
  
#### Pour calculer la distance des trajets à l’aide de fnCalculateDistance  
  
1.  La fonction _fnCalculateDistance_ doit avoir été téléchargée et inscrite auprès de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le cadre de la préparation de cette procédure pas à pas. Passer le code en revue  
  
    Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], développez **Programmabilité**, **Fonctions** puis **Fonctions scalaires**.   
    Cliquez avec le bouton droit sur _fnCalculateDistance_, puis sélectionnez **Modifier** pour ouvrir le script [!INCLUDE[tsql](../../includes/tsql-md.md)] dans une nouvelle fenêtre de requête.  
  
    ```  
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)  
    -- User-defined function that calculates the direct distance between two geographical coordinates.  
    RETURNS float  
    AS  
    BEGIN  
      DECLARE @distance decimal(28, 10)  
      -- Convert to radians  
      SET @Lat1 = @Lat1 / 57.2958  
      SET @Long1 = @Long1 / 57.2958  
      SET @Lat2 = @Lat2 / 57.2958  
      SET @Long2 = @Long2 / 57.2958  
      -- Calculate distance  
      SET @distance = (SIN(@Lat1) * SIN(@Lat2)) + (COS(@Lat1) * COS(@Lat2) * COS(@Long2 - @Long1))  
      --Convert to miles  
      IF @distance <> 0  
      BEGIN  
        SET @distance = 3958.75 * ATAN(SQRT(1 - POWER(@distance, 2)) / @distance);  
      END  
      RETURN @distance  
    END  
    GO  
  
    ```  
  
    -   La fonction est une fonction scalaire qui retourne une valeur de données unique d’un type prédéfini.  
  
    -   Elle accepte des valeurs de latitude et de longitude comme entrées, obtenues à partir des lieux de prise en charge et de dépose des passagers. La formule de Haversine convertit les emplacements en radians et utilise ces valeurs pour calculer la distance directe en miles entre ces deux emplacements.  
  
Pour ajouter la valeur calculée à une table qui peut être utilisée pour l’apprentissage du modèle, vous allez utiliser une autre fonction, _fnEngineerFeatures_.  
  
#### Pour enregistrer les caractéristiques à l’aide de _fnEngineerFeatures_  
  
1.  Prenez une minute pour examiner le code de la fonction T-SQL personnalisée, _fnEngineerFeatures_, qui doit avoir été créé pour vous dans le cadre de la préparation de cette procédure pas à pas.  
  
    Il s’agit d’une fonction table qui prend plusieurs colonnes comme entrées et retourne une table avec plusieurs colonnes de caractéristiques.  Le rôle de cette fonction consiste à créer un ensemble de caractéristiques servant à générer un modèle. La fonction _fnEngineerFeatures_ appelle la fonction T-SQL créée précédemment, _fnCalculateDistance_, pour obtenir la distance directe entre les lieux de prise en charge et de dépose des passagers.  
  
    ```  
    CREATE FUNCTION [dbo].[fnEngineerFeatures] (  
    @passenger_count int = 0,  
    @trip_distance float = 0,  
    @trip_time_in_secs int = 0,  
    @pickup_latitude float = 0,  
    @pickup_longitude float = 0,  
    @dropoff_latitude float = 0,  
    @dropoff_longitude float = 0)  
    RETURNS TABLE  
    AS  
      RETURN  
      (  
      -- Add the SELECT statement with parameter references here  
      SELECT  
        @passenger_count AS passenger_count,  
        @trip_distance AS trip_distance,  
        @trip_time_in_secs AS trip_time_in_secs,  
        [dbo].[fnCalculateDistance](@pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude) AS direct_distance  
  
      )  
    GO  
  
    ```  
  
2.  Pour vérifier que cette fonction fonctionne, vous pouvez l’utiliser pour calculer la distance géographique pour les trajets où la distance au compteur était égale à 0, mais où les lieux de prise en charge et de dépose étaient différents.  
  
    ```  
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,  
        trip_distance, pickup_datetime, dropoff_datetime,   
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance  
        FROM nyctaxi_sample  
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0  
        ORDER BY trip_time_in_secs DESC  
    ```  
  
    Comme vous pouvez le voir, la distance signalée par le compteur ne correspond pas toujours à la distance géographique. C’est pourquoi l’ingénierie des caractéristiques est si importante.  
  
À l’étape suivante, vous allez découvrir comment utiliser ces caractéristiques de données pour former un modèle d’apprentissage automatique à l’aide de R.  
  
## Étape suivante  
[Step 5 : Former et enregistrer un modèle à l’aide de T-SQL](../../advanced-analytics/r-services/step-5-train-and-save-a-model-using-t-sql.md)  
  
## Étape précédente  
[Étape 3 : Explorer et visualiser les données](../../advanced-analytics/r-services/step-3-explore-and-visualize-the-data-in-database-advanced-analytics-tutorial.md)  
  
## Voir aussi  
[Analyse avancée en base de données pour les développeurs SQL &#40;Didacticiel&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Didacticiels pour SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
