---
title: Créer et exécuter des scripts R simples
titleSuffix: SQL Server Machine Learning Services
description: Créez et exécutez des scripts R simples dans une instance de SQL Server avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e49b01d3c3a4ac743d6614d66cc7864aee946460
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72006042"
---
# <a name="quickstart-create-and-run-simple-r-scripts-with-sql-server-machine-learning-services"></a>Démarrage rapide : Créer et exécuter des scripts R simples avec SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce guide de démarrage rapide, vous allez créer et exécuter un ensemble de scripts R simples à l’aide de [SQL Server machine learning services](../what-is-sql-server-machine-learning.md). Vous allez apprendre à inclure dans un wrapper un script R bien formé dans la procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) et à exécuter le script dans une instance SQL Server.

## <a name="prerequisites"></a>Prérequis

- Ce guide de démarrage rapide nécessite l’accès à une instance de SQL Server avec [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md) avec le langage R installé.

  Votre instance de SQL Server peut se trouver dans une machine virtuelle Azure ou en local. N’oubliez pas que la fonctionnalité de script externe est désactivée par défaut. par conséquent, vous devrez peut-être [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifier que **SQL Server Launchpad service** est en cours d’exécution avant de commencer.

- Vous avez également besoin d’un outil pour exécuter des requêtes SQL qui contiennent des scripts R. Vous pouvez exécuter ces scripts à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce guide de démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="run-a-simple-script"></a>Exécuter un script simple

Pour exécuter un script R, vous devez le passer en tant qu’argument à la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
Cette procédure stockée système démarre le runtime R dans le contexte d’SQL Server, passe des données à R, gère les sessions utilisateur R en toute sécurité et retourne les résultats au client.

Dans les étapes suivantes, vous allez exécuter cet exemple de script R dans votre instance SQL Server :

```r
a <- 1
b <- 2
c <- a/b
d <- a*b
print(c(c, d))
```

1. Ouvrez **SQL Server Management Studio** et connectez-vous à votre instance SQL Server.

1. Transmettez le script R complet à la procédure stockée `sp_execute_external_script`.

   Le script passe par l’argument `@script`. Tout ce qui se trouve à l’intérieur de l’argument `@script` doit être un code R valide.

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'
    a <- 1
    b <- 2
    c <- a/b
    d <- a*b
    print(c(c, d))
    '
    ```

1. Le résultat correct est calculé et la fonction R `print` retourne le résultat dans la fenêtre **messages** .

   La valeur doit ressembler à ceci.

    **Résultats**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>Exécuter un script de Hello World

Un exemple de script classique est un exemple qui génère simplement la chaîne « Hello World ». Exécutez la commande suivante :

```sql
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'OutputDataSet<-InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

Les entrées de la procédure stockée `sp_execute_external_script` sont les suivantes :

| | |
|-|-|
| @language | définit l’extension de langage à appeler, dans ce cas, R |
| @script | définit les commandes passées au runtime R. Votre script R entier doit être placé dans cet argument en tant que texte Unicode. Vous pouvez également ajouter le texte à une variable de type **nvarchar** , puis appeler la variable |
| @input_data_1 | données retournées par la requête, passées au runtime R, qui retourne les données à SQL Server sous la forme d’une trame de données |
|WITH RESULT SETS | la clause définit le schéma de la table de données retournée pour SQL Server, en ajoutant « Hello World » comme nom de colonne, **int** pour le type de données. |

La commande génère le texte suivant :

| Salut tout le monde |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>Utiliser les entrées et les sorties

Par défaut, `sp_execute_external_script` accepte un seul jeu de données comme entrée, ce qui est généralement fourni sous la forme d’une requête SQL valide. Elle retourne ensuite une trame de données R unique comme sortie.

Pour le moment, nous allons utiliser les variables d’entrée et de sortie par défaut de `sp_execute_external_script` : **InputDataSet** et **OutputDataSet**.

1. Créez une petite table de données de test.

    ```sql
    CREATE TABLE RTestData (col1 INT NOT NULL)
    
    INSERT INTO RTestData
    VALUES (1);
    
    INSERT INTO RTestData
    VALUES (10);
    
    INSERT INTO RTestData
    VALUES (100);
    GO
    ```

1. Utilisez l’instruction `SELECT` pour interroger la table.
  
    ```sql
    SELECT *
    FROM RTestData
    ```

    **Résultats**

    ![Contenu de la table RTestData](./media/select-rtestdata.png)

1. Exécutez le script R suivant. Il récupère les données de la table à l’aide de l’instruction `SELECT`, les passe via le runtime R et retourne les données sous forme de trame de données. La clause `WITH RESULT SETS` définit le schéma de la table de données retournée pour SQL, en ajoutant le nom de colonne *NewColName*.

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'OutputDataSet <- InputDataSet;'
        , @input_data_1 = N'SELECT * FROM RTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **Résultats**

    ![Sortie à partir d’un script R qui retourne des données à partir d’une table](./media/r-output-rtestdata.png)

1. À présent, nous allons modifier les noms des variables d’entrée et de sortie. Les noms de variable d’entrée et de sortie par défaut sont **InputDataSet** et **OutputDataSet**. ce script modifie les noms en **SQL_in** et **SQL_out**:

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N' SQL_out <- SQL_in;'
        , @input_data_1 = N' SELECT 12 as Col;'
        , @input_data_1_name = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    Notez que R respecte la casse. Les variables d’entrée et de sortie utilisées dans le script R (**SQL_out**, **SQL_in**) doivent correspondre aux noms définis avec `@input_data_1_name` et `@output_data_1_name`, y compris la casse.

   > [!TIP]
   > Vous ne pouvez passer qu’un seul dataset d’entrée comme paramètre, et vous ne pouvez retourner qu’un seul dataset. Toutefois, vous pouvez appeler d’autres datasets à partir de votre code R et retourner des sorties d’autres types en plus du dataset. Vous pouvez aussi ajouter le mot clé OUTPUT à n’importe quel paramètre pour qu’il soit retourné avec les résultats.

1. Vous pouvez également générer des valeurs en utilisant simplement le script R sans données d’entrée (`@input_data_1` est défini sur vide).

   Le script suivant génère le texte « Hello » et « World ».

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'
    mytextvariable <- c("hello", " ", "world");
    OutputDataSet <- as.data.frame(mytextvariable);
    '
        , @input_data_1 = N''
    WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
    ```

    **Résultats**

    ![Résultats de la requête à l’aide de @script comme entrée](./media/r-data-generated-output.png)

## <a name="check-r-version"></a>Vérifier la version de R

Si vous souhaitez connaître la version de R installée dans votre instance de SQL Server, exécutez le script suivant.

```sql
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(version)';
GO
```

La fonction R `print` retourne la version dans la fenêtre **messages** . Dans l’exemple de sortie ci-dessous, vous pouvez voir que dans ce cas, R version 3.4.4 est installé.

**Résultats**

```text
STDOUT message(s) from external script:
                   _
platform       x86_64-w64-mingw32
arch           x86_64
os             mingw32
system         x86_64, mingw32
status
major          3
minor          4.4
year           2018
month          03
day            15
svn rev        74408
language       R
version.string R version 3.4.4 (2018-03-15)
nickname       Someone to Lean On
```

## <a name="list-r-packages"></a>Répertorier les packages R

Microsoft fournit un certain nombre de packages R préinstallés avec SQL Server Machine Learning Services.

Pour afficher la liste des packages R installés, y compris les informations sur la version, les dépendances, la licence et le chemin d’accès de la bibliothèque, exécutez le script suivant.

```SQL
EXEC sp_execute_external_script @language = N'R'
    , @script = N'
OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
WITH result sets((
            Package NVARCHAR(255)
            , Version NVARCHAR(100)
            , Depends NVARCHAR(4000)
            , License NVARCHAR(1000)
            , LibPath NVARCHAR(2000)
            ));
```

La sortie provient de `installed.packages()` dans R et est retournée en tant que jeu de résultats.

**Résultats**

![Packages installés dans R](./media/rsql-installed-packages.png) 

## <a name="next-steps"></a>Étapes suivantes

Pour savoir comment utiliser les structures de données lors de l’utilisation de R dans SQL Server Machine Learning Services, suivez ce guide de démarrage rapide :

> [!div class="nextstepaction"]
> [Gérer les types de données et les objets à l’aide de R dans SQL Server Machine Learning Services](quickstart-r-data-types-and-objects.md)

Pour plus d’informations sur l’utilisation de R dans SQL Server Machine Learning Services, consultez les articles suivants :

- [Écrire des fonctions R avancées avec SQL Server Machine Learning Services](quickstart-r-functions.md)
- [Créer et évaluer un modèle prédictif dans R avec SQL Server Machine Learning Services](quickstart-r-train-score-model.md)
- [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
