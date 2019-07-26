---
title: Jeu de données de démonstration des vols aériens pour SQL Server didacticiels Python et R
Description: Créer une base de données contenant le jeu de données de la compagnie aérienne à partir de R et Python. Ce jeu de données est utilisé dans les exercices qui montrent comment encapsuler le code R ou python dans une procédure stockée SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/22/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 38e61bcbf3a5ff5ed44f85d5ad28406550e5a726
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469676"
---
#  <a name="airline-flight-arrival-demo-data-for-sql-server-python-and-r-tutorials"></a>Données de démonstration de l’arrivée d’un avion de transport pour SQL Server les didacticiels Python et R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans cet exercice, créez une base de données SQL Server pour stocker des données importées à partir de jeux de données de démonstration de la compagnie aérienne intégrés R ou python. Les distributions R et Python fournissent des données équivalentes, que vous pouvez importer dans une base de données SQL Server à l’aide de Management Studio.

Pour effectuer cet exercice, vous devez disposer d' [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017) ou d’un autre outil capable d’exécuter des requêtes T-SQL.

Les didacticiels et les guides de démarrage rapide utilisant ce jeu de données sont les suivants:

+  [Créer un modèle Python à l’aide de revoscalepy](use-python-revoscalepy-to-create-model.md)

## <a name="create-the-database"></a>Créer la base de données

1. Démarrez SQL Server Management Studio, connectez-vous à une instance du moteur de base de données qui dispose de l’intégration R ou python.  

2. Dans l’Explorateur d’objets, cliquez avec le bouton droit sur **bases de données** et créez une nouvelle base de données appelée **FlightData**.

3. Cliquez avec le bouton droit sur **FlightData**, cliquez sur **tâches**, puis sur **Importer un fichier plat**.

4. Ouvrez le fichier AirlineDemoData. csv fourni dans la distribution R ou python, selon la langue que vous avez installée.

   Pour R, recherchez **AirlineDemoSmall. csv** dans C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library\RevoScaleR\SampleData
   
   Pour Python, recherchez **AirlineDemoSmall. csv** dans C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\revoscalepy\data\sample_data
  
Lorsque vous sélectionnez le fichier, les valeurs par défaut sont renseignées pour le nom et le schéma de la table.

  ![Assistant importation de fichier plat avec les valeurs par défaut de la démo de la compagnie aérienne](media/import-airlinedemosmall.png)

Cliquez sur les pages restantes, en acceptant les valeurs par défaut, pour importer les données.


## <a name="query-the-data"></a>Interroger les données

En guise d’étape de validation, exécutez une requête pour confirmer que les données ont été téléchargées.

1. Dans l’Explorateur d’objets, sous bases de données, cliquez avec le bouton droit sur la base de données **FlightData** et démarrez une nouvelle requête.

2. Exécuter des requêtes simples:

    ```sql
    SELECT TOP(10) * FROM AirlineDemoSmall;
    SELECT COUNT(*) FROM AirlineDemoSmall;
    ```

## <a name="next-steps"></a>Étapes suivantes

Dans la leçon suivante, vous allez créer un modèle de régression linéaire basé sur ces données.

+ [Créer un modèle Python à l’aide de revoscalepy](use-python-revoscalepy-to-create-model.md)
