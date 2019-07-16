---
title: Guide de démarrage rapide pour l’utilisation des entrées et sorties dans Python - SQL Server Machine Learning
description: Dans ce démarrage rapide pour le script Python dans SQL Server, découvrez comment structurer les entrées et sorties pour la procédure stockée système sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 80bb86beedf54c29fbe67e2362a4163cb489c05a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962077"
---
# <a name="quickstart-handle-inputs-and-outputs-using-python-in-sql-server"></a>Démarrage rapide : Gérer les entrées et sorties à l’aide de Python dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Ce démarrage rapide montre comment gérer les entrées et sorties lors de l’utilisation de Python dans SQL Server Machine Learning Services.

Par défaut, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) accepte un seul dataset d’entrée, vous fournissez en général sous la forme d’une requête SQL valide.

Autres types d’entrée peuvent être passés en tant que variables SQL : par exemple, vous pouvez passer un modèle formé en tant que variable, à l’aide d’une fonction de sérialisation comme [pickle](https://docs.python.org/3.0/library/pickle.html) ou [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) pour écrire le modèle un format binaire.

La procédure stockée retourne un seul Python [pandas](https://pandas.pydata.org/pandas-docs/stable/index.html) de trame de données en tant que sortie, mais vous pouvez également générer des valeurs scalaires et des modèles en tant que variables. Vous pouvez par exemple, un modèle formé en tant que binaire variable de sortie et passe à une instruction T-SQL INSERT, pour écrire ce modèle dans une table. Vous pouvez également générer des tracés (au format binaire) ou des valeurs scalaires (les valeurs individuelles, telles que la date et l’heure, la durée pour former le modèle et ainsi de suite).

## <a name="prerequisites"></a>Prérequis

Un guide de démarrage rapide précédent, [Python vérifier existe dans SQL Server](quickstart-python-verify.md), fournit des informations et des liens pour la configuration de l’environnement Python requis pour ce démarrage rapide.

## <a name="create-the-source-data"></a>Créer la source de données

Créer une petite table de données de test en exécutant l’instruction T-SQL suivante :

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

Jetons un œil à la valeur par défaut des variables d’entrée et de sortie de sp_execute_external_script : `InputDataSet` et `OutputDataSet`.

1. Vous pouvez obtenir les données à partir de la table en tant qu’entrée à votre script Python. Exécutez l’instruction ci-dessous. Il obtient les données de la table, effectue un aller-retour via le runtime Python et retourne les valeurs avec le nom de colonne *NewColName*.

    Les données retournées par la requête sont passées à l’exécution de Python, qui retourne les données à base de données SQL sous la forme d’une trame de données pandas. La clause WITH RESULT SETS définit le schéma de la table de données retournées pour la base de données SQL.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **Résultats**

    ![Sortie de script Python qui retourne des données à partir d’une table](./media/python-output-pythontestdata.png)

2. Nous allons modifier le nom des variables d’entrée ou de sortie. Le script ci-dessus utilisé l’entrée par défaut et les noms de variables de sortie _InputDataSet_ et _OutputDataSet_. Pour définir les données d’entrée associées _InputDataSet_, vous utilisez le *@input_data_1* variable.

    Dans ce script, les noms des variables d’entrée et sortie de la procédure stockée ont été modifiés pour *SQL_out* et *SQL_in*:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'Python'
      , @script = N'SQL_out = SQL_in'
      , @input_data_1 = N' SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    Le cas des variables d’entrée et de sortie dans `@input_data_1_name` et `@output_data_1_name` doivent correspondre le cas de ceux mentionnés dans le code Python dans `@script`, comme Python respecte la casse.

    Vous ne pouvez passer qu’un seul dataset d’entrée comme paramètre, et vous ne pouvez retourner qu’un seul dataset. Toutefois, vous pouvez appeler à partir d’autres jeux de données à l’intérieur de votre code Python et vous pouvez retourner des sorties d’autres types en plus du dataset. Vous pouvez aussi ajouter le mot clé OUTPUT à n’importe quel paramètre pour qu’il soit retourné avec les résultats. 

    La `WITH RESULT SETS` instruction définit le schéma pour les données qui sont utilisés dans SQL Server. Vous devez fournir des types de données compatibles SQL pour chaque colonne que vous retournez à partir de Python. Vous pouvez utiliser la définition de schéma pour fournir des nouveaux noms de colonnes trop comme vous n’avez pas besoin d’utiliser les noms de colonnes à partir de la trame de données Python.

3. Vous pouvez également générer des valeurs en utilisant le script Python et laisser la chaîne de requête d’entrée dans _@input_data_1_ vide.

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

    ![Résultats de la requête à l’aide de @script en tant qu’entrée](./media/python-data-generated-output.png)

## <a name="next-steps"></a>Étapes suivantes

Examiner certains des problèmes que vous pouvez rencontrer lors du passage des données tabulaires entre Python et SQL Server.

> [!div class="nextstepaction"]
> [Démarrage rapide : Structures de données de Python dans SQL Server](quickstart-python-data-structures.md)
