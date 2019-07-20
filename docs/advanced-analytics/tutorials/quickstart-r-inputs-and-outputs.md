---
title: Démarrage rapide pour l’utilisation des entrées et des sorties dans R
description: Dans ce guide de démarrage rapide pour le script R dans SQL Server, Découvrez comment structurer les entrées et les sorties dans la procédure stockée système sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 1ccdf5206f2564ead2ca66f40143aee1b4ab1fad
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344618"
---
# <a name="quickstart-handle-inputs-and-outputs-using-r-in-sql-server"></a>Démarrage rapide : Gérer les entrées et les sorties à l’aide de R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Ce guide de démarrage rapide montre comment gérer les entrées et les sorties lors de l’utilisation de R dans SQL Server Machine Learning Services ou R services.

Lorsque vous souhaitez exécuter du code R dans SQL Server, vous devez encapsuler le script R dans une procédure stockée. Vous pouvez écrire un script R ou passer à [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Cette procédure stockée système est utilisée pour démarrer le runtime R dans le contexte d’SQL Server, qui transmet les données à R, gère les sessions utilisateur R en toute sécurité et retourne les résultats au client.

Par défaut, [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) accepte un jeu de données d’entrée unique, généralement fourni sous la forme d’une requête SQL valide. D’autres types d’entrée peuvent être passés en tant que variables SQL.

La procédure stockée retourne une trame de données R unique comme sortie, mais vous pouvez également copier des modèles et des scalaires en tant que variables. Par exemple, vous pouvez générer un modèle formé en tant que variable binaire et le transmettre à une instruction T-SQL INSERT, pour écrire ce modèle dans une table. Vous pouvez également générer des tracés (au format binaire) ou des scalaires (valeurs individuelles, telles que la date et l’heure, le temps écoulé pour l’apprentissage du modèle, etc.).

## <a name="prerequisites"></a>Prérequis

Un démarrage rapide précédent, [Vérifiez que R existe dans SQL Server](quickstart-r-verify.md), fournit des informations et des liens pour configurer l’environnement r requis pour ce guide de démarrage rapide.

## <a name="create-the-source-data"></a>Créer la source de données

Créez une petite table de données de test en exécutant l’instruction T-SQL suivante:

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

Examinons les variables d’entrée et de sortie par défaut de sp_execute_external_script `InputDataSet` : `OutputDataSet`et.

1. Vous pouvez récupérer les données de la table en tant qu’entrée dans votre script R. Exécutez l’instruction ci-dessous. Il obtient les données de la table, effectue un aller-retour dans le runtime R et retourne les valeurs avec le nom de colonne *NewColName*.

    Les données retournées par la requête sont passées au runtime R, qui retourne les données à SQL Database sous la forme d’une trame de données. La clause WITH RESULT SETS définit le schéma de la table de données retournée pour SQL Database.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'R'
        , @script = N'OutputDataSet <- InputDataSet;'
        , @input_data_1 = N'SELECT * FROM RTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **Résultats**

    ![Sortie à partir d’un script R qui retourne des données à partir d’une table](./media/r-output-rtestdata.png)

2. Modifions le nom des variables d’entrée ou de sortie. Le script ci-dessus utilisait les noms de variables d’entrée et de sortie par défaut, _InputDataSet_ et _OutputDataSet_. Pour définir les données d’entrée associées à _InputDatSet_, vous utilisez *@input_data_1* la variable.

    Dans ce script, les noms des variables de sortie et d’entrée de la procédure stockée ont été modifiés en *SQL_out* et *SQL_in*:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'R'
      , @script = N' SQL_out <- SQL_in;'
      , @input_data_1 = N'SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    Notez que R respecte la casse, donc la casse des variables d’entrée et de sortie dans `@input_data_1_name` et `@output_data_1_name` doit correspondre à celles du code R dans `@script`. 

    Vous ne pouvez passer qu’un seul dataset d’entrée comme paramètre, et vous ne pouvez retourner qu’un seul dataset. Toutefois, vous pouvez appeler d’autres datasets à partir de votre code R et retourner des sorties d’autres types en plus du dataset. Vous pouvez aussi ajouter le mot clé OUTPUT à n’importe quel paramètre pour qu’il soit retourné avec les résultats. 

    L' `WITH RESULT SETS` instruction définit le schéma pour les données utilisées dans SQL Server. Vous devez fournir des types de données compatibles avec SQL pour chaque colonne que vous retournez à partir de R. Vous pouvez utiliser la définition de schéma pour fournir de nouveaux noms de colonnes, car vous n’avez pas besoin d’utiliser les noms de colonnes de la trame de données R.

3. Vous pouvez également générer des valeurs à l’aide du script R et laisser la chaîne _@input_data_1_ de requête d’entrée vide.

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'R'
        , @script = N' mytextvariable <- c("hello", " ", "world");
            OutputDataSet <- as.data.frame(mytextvariable);'
        , @input_data_1 = N''
    WITH RESULT SETS (([Col1] CHAR(20) NOT NULL));
    ```

    **Résultats**

    ![Résultats de la @script requête en tant qu’entrée](./media/r-data-generated-output.png)

## <a name="next-steps"></a>Étapes suivantes

Examinez certains des problèmes que vous pouvez rencontrer lors du passage de données entre R et SQL Server, telles que les conversions implicites et les différences dans les données tabulaires entre R et SQL.

> [!div class="nextstepaction"]
> [Démarrage rapide : Gérer les types de données et les objets](quickstart-r-data-types-and-objects.md)