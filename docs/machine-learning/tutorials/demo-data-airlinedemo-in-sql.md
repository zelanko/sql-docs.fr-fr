---
description: Données de démonstration d’arrivée de vols Airline pour les didacticiels R et Python SQL Server
title: Données de démonstration de vols Airline pour les didacticiels
Description: Créez une base de données contenant le jeu de données Airline à partir de R et Python. Ce jeu de données est utilisé dans les didacticiels R et Python pour SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 10/22/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7ec47525a79738eafc2746808a669ee50df0363a
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92194487"
---
#  <a name="airline-flight-arrival-demo-data-for-sql-server-python-and-r-tutorials"></a>Données de démonstration d’arrivée de vols Airline pour les didacticiels R et Python SQL Server
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Dans cet exercice, créez une base de données SQL Server pour stocker des données importées à partir des jeux de données de démonstration Airline intégrés de R ou Python. Les distributions R et Python fournissent des données équivalentes, que vous pouvez importer dans une base de données SQL Server à l’aide de Management Studio.

Pour effectuer cet exercice, vous devez avoir [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md?view=sql-server-2017) ou un autre outil capable d’exécuter des requêtes T-SQL.

Voici les tutoriels et les démarrages rapides qui utilisant ce jeu de données :

+  [Créer un modèle Python à l’aide de revoscalepy](use-python-revoscalepy-to-create-model.md)

## <a name="create-the-database"></a>Créer la base de données

1. Démarrez SQL Server Management Studio et connectez-vous à une instance du moteur de base de données qui dispose de l’intégration R ou Python.  

2. Dans l’Explorateur d’objets, cliquez avec le bouton droit sur **Bases de données** et créez une nouvelle base de données appelée **flightdata**.

3. Cliquez avec le bouton droit sur **flightdata**, cliquez sur **Tâches**, puis sur **Importer un fichier plat**.

4. Ouvrez le fichier AirlineDemoData.csv fourni dans la distribution R ou Python, selon le langage que vous avez installé.

   Pour R, recherchez **AirlineDemoSmall.csv** dans C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR\SampleData
   
   Pour Python, recherchez **AirlineDemoSmall.csv** dans C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\revoscalepy\data\sample_data
  
Lorsque vous sélectionnez le fichier, les valeurs par défaut sont renseignées pour le nom et le schéma de la table.

  ![Assistant Importation de fichier plat présentant les valeurs par défaut de la démonstration Airline](media/import-airlinedemosmall.png)

Parcourez les pages restantes, en acceptant les valeurs par défaut, pour importer les données.


## <a name="query-the-data"></a>Interroger les données

En guise d’étape de validation, exécutez une requête pour confirmer que les données ont été chargées.

1. Dans l’Explorateur d’objets, sous Bases de données, cliquez avec le bouton droit sur la base de données **flightdata**, puis démarrez une nouvelle requête.

2. Exécutez des requêtes simples :

    ```sql
    SELECT TOP(10) * FROM AirlineDemoSmall;
    SELECT COUNT(*) FROM AirlineDemoSmall;
    ```

## <a name="next-steps"></a>Étapes suivantes

Dans la leçon suivante, vous allez créer un modèle de régression linéaire basé sur ces données.

+ [Créer un modèle Python à l’aide de revoscalepy](use-python-revoscalepy-to-create-model.md)