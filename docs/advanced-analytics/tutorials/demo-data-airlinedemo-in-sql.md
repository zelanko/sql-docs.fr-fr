---
title: Jeu de données de démonstration de flight compagnies aériennes pour les didacticiels SQL Server Python et R - SQL Server Machine Learning
Description: Créer une base de données contenant le jeu de données de compagnies aériennes à partir de R et Python. Ce jeu de données est utilisé dans les exercices montrant comment encapsuler le langage R ou Python code dans une procédure stockée SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/22/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 69f95876a880684ee09b83ad32341a781bc4f5cf
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510186"
---
#  <a name="airline-flight-arrival-demo-data-for-sql-server-python-and-r-tutorials"></a>Données de démonstration de d’arrivée de vol compagnies aériennes pour les didacticiels de SQL Server Python et R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans cet exercice, créez une base de données SQL Server pour stocker les données importées à partir de R ou Python intégrées Airline demo jeux de données. Distributions de R et Python fournissent des données équivalentes, que vous pouvez importer une base de données SQL Server à l’aide de Management Studio.

Pour effectuer cet exercice, vous devez disposer [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) ou un autre outil qui peut exécuter des requêtes T-SQL.

Didacticiels et guides de démarrage rapide à l’aide de ce jeu de données sont les suivantes :

+  [Créer un modèle de Python à l’aide de revoscalepy](use-python-revoscalepy-to-create-model.md)

## <a name="create-the-database"></a>Créer la base de données

1. Démarrez SQL Server Management Studio, connectez-vous à une instance du moteur de base de données qui a l’intégration de R ou Python.  

2. Dans l’Explorateur d’objets, cliquez sur **bases de données** et créer une base de données appelée **flightdata**.

3. Avec le bouton droit **flightdata**, cliquez sur **tâches**, cliquez sur **importer un fichier plat**.

4. Ouvrez le fichier AirlineDemoData.csv fourni dans la distribution de R ou Python, selon la langue que vous avez installé.

   Pour R, recherchez **AirlineDemoSmall.csv** à C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library\RevoScaleR\SampleData
   
   Pour Python, recherchez **AirlineDemoSmall.csv** à C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\revoscalepy\data\sample_data
  
Lorsque vous sélectionnez le fichier, les valeurs par défaut sont renseignés pour le schéma et le nom de la table.

  ![Assistant Importation de fichier plat montrant les valeurs par défaut de démonstration de compagnies aériennes](media/import-airlinedemosmall.png)

Parcourez les pages restantes, en acceptant les valeurs par défaut, pour importer les données.


## <a name="query-the-data"></a>Interroger les données

Comme une étape de validation, exécutez une requête pour confirmer que le téléchargement de données.

1. Dans l’Explorateur d’objets, des bases de données, cliquez sur le **flightdata** de base de données et démarrer une nouvelle requête.

2. Exécutez des requêtes simples :

    ```sql
    SELECT TOP(10) * FROM AirlineDemoSmall;
    SELECT COUNT(*) FROM AirlineDemoSmall;
    ```

## <a name="next-steps"></a>Étapes suivantes

Dans la leçon suivante, vous allez créer un modèle de régression linéaire basé sur ces données.

+ [Créer un modèle de Python à l’aide de revoscalepy](use-python-revoscalepy-to-create-model.md)
