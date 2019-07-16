---
title: Guide de démarrage rapide pour l’utilisation des entrées et sorties dans R - SQL Server Machine Learning
description: Dans ce démarrage rapide pour le script R dans SQL Server, découvrez comment structurer les entrées et sorties pour la procédure stockée système sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 1672cdeb59dfe35e313c999549e46f3fd76b688e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962000"
---
# <a name="quickstart-handle-inputs-and-outputs-using-r-in-sql-server"></a>Démarrage rapide : Gérer les entrées et sorties à l’aide de R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Ce démarrage rapide montre comment gérer les entrées et sorties lors de l’utilisation de R dans SQL Server Machine Learning Services ou R Services.

Lorsque vous souhaitez exécuter le code R dans SQL Server, vous devez encapsuler le script R dans une procédure stockée. Vous pouvez écrire une, ou passer à un script R [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Ce système de procédure stockée est utilisée pour démarrer le runtime R dans le contexte de SQL Server, qui transmet les données à R, gère les sessions utilisateur R en toute sécurité et retourne les résultats au client.

Par défaut, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) accepte un seul dataset d’entrée, vous fournissez en général sous la forme d’une requête SQL valide. Autres types d’entrée peuvent être passés en tant que variables SQL.

La procédure stockée retourne une trame de données R unique en tant que sortie, mais vous pouvez également générer des valeurs scalaires et des modèles en tant que variables. Vous pouvez par exemple, un modèle formé en tant que binaire variable de sortie et passe à une instruction T-SQL INSERT, pour écrire ce modèle dans une table. Vous pouvez également générer des tracés (au format binaire) ou des valeurs scalaires (les valeurs individuelles, telles que la date et l’heure, la durée pour former le modèle et ainsi de suite).

## <a name="prerequisites"></a>Prérequis

Un guide de démarrage rapide précédent, [R vérifier existe dans SQL Server](quickstart-r-verify.md), fournit des informations et des liens pour la configuration de l’environnement R requis pour ce démarrage rapide.

## <a name="create-the-source-data"></a>Créer la source de données

Créer une petite table de données de test en exécutant l’instruction T-SQL suivante :

```sql
CREATE TABLE RTestData (col1 INT NOT NULL)
INSERT INTO RTestData VALUES (1);
INSERT INTO RTestData VALUES (10);
INSERT INTO RTestData VALUES (100);
GO
```

Une fois la table créée, utilisez l’instruction suivante pour interroger la table :
  
```sql
SELECT * FROM RTestData
```

**Résultats**

![Contenu de la table RTestData](./media/select-rtestdata.png)

## <a name="inputs-and-outputs"></a>Entrées et sorties

Jetons un œil à la valeur par défaut des variables d’entrée et de sortie de sp_execute_external_script : `InputDataSet` et `OutputDataSet`.

1. Vous pouvez obtenir les données à partir de la table en tant qu’entrée pour votre script R. Exécutez l’instruction ci-dessous. Il obtient les données de la table, effectue un aller-retour via le runtime R et retourne les valeurs avec le nom de colonne *NewColName*.

    Les données retournées par la requête sont transmises au runtime R, qui retourne les données à la base de données SQL comme une trame de données. La clause WITH RESULT SETS définit le schéma de la table de données retournées pour la base de données SQL.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'R'
        , @script = N'OutputDataSet <- InputDataSet;'
        , @input_data_1 = N'SELECT * FROM RTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **Résultats**

    ![Sortie de script R qui retourne des données à partir d’une table](./media/r-output-rtestdata.png)

2. Nous allons modifier le nom des variables d’entrée ou de sortie. Le script ci-dessus utilisé l’entrée par défaut et les noms de variables de sortie _InputDataSet_ et _OutputDataSet_. Pour définir les données d’entrée associées _InputDatSet_, vous utilisez le *@input_data_1* variable.

    Dans ce script, les noms des variables d’entrée et sortie de la procédure stockée ont été modifiés pour *SQL_out* et *SQL_in*:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'R'
      , @script = N' SQL_out <- SQL_in;'
      , @input_data_1 = N'SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    Notez que R respecte la casse, par conséquent, le cas des variables d’entrée et de sortie dans `@input_data_1_name` et `@output_data_1_name` doivent correspondre celles figurant dans le code R dans `@script`. 

    Vous ne pouvez passer qu’un seul dataset d’entrée comme paramètre, et vous ne pouvez retourner qu’un seul dataset. Toutefois, vous pouvez appeler d’autres datasets à partir de votre code R et retourner des sorties d’autres types en plus du dataset. Vous pouvez aussi ajouter le mot clé OUTPUT à n’importe quel paramètre pour qu’il soit retourné avec les résultats. 

    La `WITH RESULT SETS` instruction définit le schéma pour les données qui sont utilisés dans SQL Server. Vous devez fournir des types de données compatibles SQL pour chaque colonne que vous retournez à partir de R. Vous pouvez utiliser la définition de schéma pour fournir des nouveaux noms de colonnes trop comme vous n’avez pas besoin d’utiliser les noms de colonnes à partir de la trame de données R.

3. Vous pouvez également générer des valeurs en utilisant le script R et laissez la chaîne de requête d’entrée dans _@input_data_1_ vide.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'R'
        , @script = N' mytextvariable <- c("hello", " ", "world");
            OutputDataSet <- as.data.frame(mytextvariable);'
        , @input_data_1 = N''
    WITH RESULT SETS (([Col1] CHAR(20) NOT NULL));
    ```

    **Résultats**

    ![Résultats de la requête à l’aide de @script en tant qu’entrée](./media/r-data-generated-output.png)

## <a name="next-steps"></a>Étapes suivantes

Examiner certains des problèmes que vous pouvez rencontrer lors du passage des données entre R et SQL Server, telles que les conversions implicites et les différences dans les données tabulaires entre R et SQL.

> [!div class="nextstepaction"]
> [Démarrage rapide : Gérer des objets et des types de données](quickstart-r-data-types-and-objects.md)