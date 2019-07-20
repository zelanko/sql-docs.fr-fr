---
title: Démarrage rapide pour l’utilisation des entrées et des sorties dans python
description: Dans ce guide de démarrage rapide pour le script Python dans SQL Server, Découvrez comment structurer les entrées et les sorties dans la procédure stockée système sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: a23896f5242e0f1182b2864e426bbb20aeda763f
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344810"
---
# <a name="quickstart-handle-inputs-and-outputs-using-python-in-sql-server"></a>Démarrage rapide : Gérer les entrées et les sorties à l’aide de Python dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Ce guide de démarrage rapide montre comment gérer les entrées et les sorties lors de l’utilisation de Python dans SQL Server Machine Learning Services.

Par défaut, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) accepte un jeu de données d’entrée unique, généralement fourni sous la forme d’une requête SQL valide.

D’autres types d’entrée peuvent être passés en tant que variables SQL: par exemple, vous pouvez passer un modèle formé en tant que variable, à l’aide d’une fonction de sérialisation telle que [Pickle](https://docs.python.org/3.0/library/pickle.html) ou [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) pour écrire le modèle dans un format binaire.

La procédure stockée retourne une trame de données python [pandas](https://pandas.pydata.org/pandas-docs/stable/index.html) unique comme sortie, mais vous pouvez également copier des modèles et des scalaires en tant que variables. Par exemple, vous pouvez générer un modèle formé en tant que variable binaire et le transmettre à une instruction T-SQL INSERT, pour écrire ce modèle dans une table. Vous pouvez également générer des tracés (au format binaire) ou des scalaires (valeurs individuelles, telles que la date et l’heure, le temps écoulé pour l’apprentissage du modèle, etc.).

## <a name="prerequisites"></a>Prérequis

Un démarrage rapide précédent, [Vérifiez que Python existe dans SQL Server](quickstart-python-verify.md), fournit des informations et des liens pour configurer l’environnement python requis pour ce guide de démarrage rapide.

## <a name="create-the-source-data"></a>Créer la source de données

Créez une petite table de données de test en exécutant l’instruction T-SQL suivante:

```sql
CREATE TABLE PythonTestData (col1 INT NOT NULL)
INSERT INTO PythonTestData VALUES (1);
INSERT INTO PythonTestData VALUES (10);
INSERT INTO PythonTestData VALUES (100);
GO
```

Une fois la table créée, utilisez l’instruction suivante pour interroger la table :
  
```sql
SELECT * FROM PythonTestData
```

**Résultats**

![Contenu de la table PythonTestData](./media/select-pythontestdata.png)

## <a name="inputs-and-outputs"></a>Entrées et sorties

Examinons les variables d’entrée et de sortie par défaut de sp_execute_external_script `InputDataSet` : `OutputDataSet`et.

1. Vous pouvez récupérer les données de la table en tant qu’entrée dans votre script Python. Exécutez l’instruction ci-dessous. Il obtient les données de la table, effectue un aller-retour dans le runtime Python et retourne les valeurs avec le nom de colonne *NewColName*.

    Les données retournées par la requête sont passées au runtime Python, qui retourne les données à SQL Database sous la forme d’un tableau pandas. La clause WITH RESULT SETS définit le schéma de la table de données retournée pour SQL Database.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **Résultats**

    ![Sortie d’un script Python qui retourne des données à partir d’une table](./media/python-output-pythontestdata.png)

2. Modifions le nom des variables d’entrée ou de sortie. Le script ci-dessus utilisait les noms de variables d’entrée et de sortie par défaut, _InputDataSet_ et _OutputDataSet_. Pour définir les données d’entrée associées à _InputDataSet_, vous utilisez *@input_data_1* la variable.

    Dans ce script, les noms des variables de sortie et d’entrée de la procédure stockée ont été modifiés en *SQL_out* et *SQL_in*:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'Python'
      , @script = N'SQL_out = SQL_in'
      , @input_data_1 = N' SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    La casse des variables d’entrée et de sortie `@input_data_1_name` dans `@output_data_1_name` et doit correspondre à la casse de celles du code python dans `@script`, car python respecte la casse.

    Vous ne pouvez passer qu’un seul dataset d’entrée comme paramètre, et vous ne pouvez retourner qu’un seul dataset. Toutefois, vous pouvez appeler d’autres jeux de données à partir de votre code Python et vous pouvez retourner des sorties d’autres types en plus du DataSet. Vous pouvez aussi ajouter le mot clé OUTPUT à n’importe quel paramètre pour qu’il soit retourné avec les résultats. 

    L' `WITH RESULT SETS` instruction définit le schéma pour les données utilisées dans SQL Server. Vous devez fournir des types de données compatibles avec SQL pour chaque colonne que vous retournez à partir de Python. Vous pouvez utiliser la définition de schéma pour fournir de nouveaux noms de colonnes, car vous n’avez pas besoin d’utiliser les noms de colonnes du frame python Data.

3. Vous pouvez également générer des valeurs à l’aide du script Python et laisser la chaîne _@input_data_1_ de requête d’entrée vide.

    ```sql
    EXECUTE sp_execute_external_script
    @language = N'Python'
    , @script = N'
    import pandas as pd
    mytextvariable = pandas.Series(["hello", " ", "world"]);
    OutputDataSet = pd.DataFrame(mytextvariable);'
    , @input_data_1 = N''
    WITH RESULT SETS (([Col1] CHAR(20) NOT NULL));
    ```

    **Résultats**

    ![Résultats de la @script requête en tant qu’entrée](./media/python-data-generated-output.png)

## <a name="next-steps"></a>Étapes suivantes

Examinez certains des problèmes que vous pouvez rencontrer lors du passage de données tabulaires entre Python et SQL Server.

> [!div class="nextstepaction"]
> [Démarrage rapide : Structures de données python dans SQL Server](quickstart-python-data-structures.md)
