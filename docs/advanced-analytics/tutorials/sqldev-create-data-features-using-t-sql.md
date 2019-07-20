---
title: Leçon 2 créer des fonctionnalités de données à l’aide des fonctions R et T-SQL
description: Didacticiel expliquant comment ajouter des calculs aux procédures stockées à utiliser dans les modèles R Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 7570c6769a780c5a6d98bdfc762092524bf5000c
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345927"
---
# <a name="lesson-2-create-data-features-using-r-and-t-sql"></a>Leçon 2 : Créer des fonctionnalités de données à l’aide de R et de T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fait partie d’un didacticiel pour les développeurs SQL sur l’utilisation de R dans SQL Server.

Lors de cette étape, vous allez découvrir comment créer des caractéristiques à partir de données brutes en utilisant une fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] . Ensuite, vous appellerez cette fonction à partir d’une procédure stockée pour créer une table qui contient les valeurs des caractéristiques.

## <a name="about-feature-engineering"></a>À propos de l’ingénierie des fonctionnalités

Après plusieurs séries d’exploration de données, vous avez recueilli des informations utiles grâce aux données et vous êtes prêt à passer à *l’ingénierie des caractéristiques*. Ce processus de création de fonctionnalités significatives à partir des données brutes est une étape critique dans la création de modèles d’analyse.

Dans ce jeu de données, les valeurs de distance sont basées sur la distance de compteur signalée et ne représentent pas nécessairement la distance géographique ou la distance réelle parcourue. Ainsi, vous devrez calculer la distance directe entre les lieux de prise en charge et de dépose, en utilisant les coordonnées disponibles dans le dataset source « NYC Taxi ». Vous pouvez pour cela utiliser la [formule de Haversine](https://en.wikipedia.org/wiki/Haversine_formula) dans une fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] personnalisée.

Vous allez utiliser une fonction T-SQL personnalisée, _fnCalculateDistance_, pour calculer la distance à l’aide de la formule de Haversine, et utiliser une seconde fonction T-SQL personnalisée, _fnEngineerFeatures_, pour créer une table contenant toutes les caractéristiques.

Le processus global est le suivant:

- Créer la fonction T-SQL qui effectue les calculs

- Appeler la fonction pour générer les données de fonctionnalité

- Enregistrer les données de fonctionnalités dans une table

## <a name="calculate-trip-distance-using-fncalculatedistance"></a>Calculer la distance du trajet à l’aide de fnCalculateDistance

La fonction _fnCalculateDistance_ doit avoir été téléchargée et inscrite avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le cadre de la préparation de ce didacticiel. Prenez une minute pour examiner le code.
  
1. Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], développez **Programmabilité**, **Fonctions** puis **Fonctions scalaires**.   

2. Cliquez avec le bouton droit sur _fnCalculateDistance_, puis sélectionnez **Modifier** pour ouvrir le script [!INCLUDE[tsql](../../includes/tsql-md.md)] dans une nouvelle fenêtre de requête.
  
    ```sql
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
  
    - La fonction est une fonction scalaire qui retourne une valeur de données unique d’un type prédéfini.
  
    - Elle accepte des valeurs de latitude et de longitude comme entrées, obtenues à partir des lieux de prise en charge et de dépose des passagers. La formule de Haversine convertit les emplacements en radians et utilise ces valeurs pour calculer la distance directe en miles entre ces deux emplacements.

## <a name="generate-the-features-using-fnengineerfeatures"></a>Générer les fonctionnalités à l’aide de _fnEngineerFeatures_

Pour ajouter les valeurs calculées à une table qui peut être utilisée pour l’apprentissage du modèle, vous allez utiliser une autre fonction, _fnEngineerFeatures_. La nouvelle fonction appelle la fonction T-SQL créée précédemment, _fnCalculateDistance_, pour atteindre la distance directe entre les emplacements de prise en charge et de dépose. 

1. Prenez une minute pour examiner le code de la fonction T-SQL personnalisée, _fnEngineerFeatures_, qui doit avoir été créé pour vous dans le cadre de la préparation de cette procédure pas à pas.
  
    ```sql
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

    + Cette fonction à valeur de table qui prend plusieurs colonnes comme entrées et génère une table avec plusieurs colonnes de fonctionnalités.

    + L’objectif de cette fonction est de créer de nouvelles fonctionnalités à utiliser pour la création d’un modèle.

2.  Pour vérifier que cette fonction fonctionne, utilisez-la pour calculer la distance géographique pour les voyages où la distance mesurée est égale à 0, alors que les emplacements de sélection et de décollage étaient différents.
  
    ```sql
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,
        trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance
        FROM nyctaxi_sample
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0
        ORDER BY trip_time_in_secs DESC
    ```
  
    Comme vous pouvez le voir, la distance signalée par le compteur ne correspond pas toujours à la distance géographique. C’est pourquoi l’ingénierie des caractéristiques est si importante. Vous pouvez utiliser ces fonctionnalités de données améliorées pour effectuer l’apprentissage d’un modèle de Machine Learning à l’aide de R.

## <a name="next-lesson"></a>Leçon suivante

[Leçon 3 : Former et enregistrer un modèle à l’aide de T-SQL](sqldev-train-and-save-a-model-using-t-sql.md)

## <a name="previous-lesson"></a>Leçon précédente

[Leçon 1 : Explorez et Visualisez les données à l’aide de R et de procédures stockées](sqldev-explore-and-visualize-the-data.md)
