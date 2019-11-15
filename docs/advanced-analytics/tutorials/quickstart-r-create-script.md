---
title: 'Démarrage rapide : Créer des scripts R'
titleSuffix: SQL Server Machine Learning Services
description: Créez et exécutez des scripts R simples dans une instance SQL Server avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 5a8e2779e930671faa9fa3ab94a7384ab1bdca83
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73726986"
---
# <a name="quickstart-create-and-run-simple-r-scripts-with-sql-server-machine-learning-services"></a>Démarrage rapide : Créer et exécuter des scripts R simples avec SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce démarrage rapide, vous allez créer et exécuter un ensemble de scripts R simples en utilisant [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md). Vous allez découvrir comment encapsuler un script R bien formé dans la procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) et comment exécuter ce script dans une instance SQL Server.

## <a name="prerequisites"></a>Conditions préalables requises

- Ce démarrage rapide nécessite un accès à une instance de SQL Server sur laquelle [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) est installé avec le langage R.

  Votre instance SQL Server peut se trouver sur une machine virtuelle Azure ou être locale. Sachez simplement que la fonctionnalité de script externe est désactivée par défaut. Avant de commencer, vous serez donc peut-être amené à [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifier que le **service SQL Server Launchpad** est en cours d’exécution.

- Vous aurez aussi besoin d’un outil pour exécuter les requêtes SQL qui contiennent des scripts R. Vous pouvez exécuter ces scripts à partir de n’importe quel outil de requête ou de gestion de base de données, pourvu qu’il puisse se connecter à une instance SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="run-a-simple-script"></a>Exécuter un script simple

Pour exécuter un script R, vous devez le transmettre sous forme d’argument à la procédure stockée système, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
Cette procédure stockée système démarre le runtime R dans le contexte de SQL Server, transmet les données à R, gère les sessions utilisateur R de manière sécurisée et retourne les résultats au client.

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

   Le script est transmis via l’argument `@script`. Tout ce qui se trouve dans l’argument `@script` doit être du code R valide.

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

1. Le résultat correct est calculé et la fonction R `print` retourne le résultat dans la fenêtre **Messages**.

   Voici comment il se présente.

    **Résultats**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>Exécuter un script Hello World

Un exemple type de script est celui qui génère simplement la chaîne « Hello World ». Exécutez la commande suivante :

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
| @language | définit l’extension de langage à appeler, dans le cas présent, R |
| @script | définit les commandes transmises au runtime R. Votre script R entier doit être placé dans cet argument en tant que texte Unicode. Vous pouvez aussi ajouter le texte à une variable de type **nvarchar**, puis appeler cette variable |
| @input_data_1 | données retournées par la requête, transmises au runtime R, qui retourne les données à SQL Server sous forme de trame de données |
|WITH RESULT SETS | la clause définit le schéma de la table de données retournée pour SQL Server, ajoutant « Hello World » comme nom de colonne, **int** pour le type de données |

La commande génère le texte suivant :

| Hello World |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>Utiliser des entrées et des sorties

Par défaut, `sp_execute_external_script` accepte un seul jeu de données en entrée, que vous fournissez généralement sous forme de requête SQL valide. Il retourne ensuite une seule trame de données R en sortie.

Pour le moment, utilisons les variables d’entrée et de sortie par défaut de `sp_execute_external_script` : **InputDataSet** et **OutputDataSet**.

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

1. Exécutez le script R suivant. Il récupère les données de la table en utilisant l’instruction `SELECT`, les transmet via le runtime R et retourne les données sous forme de trame de données. La clause `WITH RESULT SETS` définit le schéma de la table de données retournée pour SQL Server, ajoutant le nom de colonne *NewColName*.

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'OutputDataSet <- InputDataSet;'
        , @input_data_1 = N'SELECT * FROM RTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **Résultats**

    ![Sortie du script R qui retourne des données d’une table](./media/r-output-rtestdata.png)

1. À présent, changeons le nom des variables d’entrée et de sortie. Les variables d’entrée et de sortie se nomment par défaut **InputDataSet** et **OutputDataSet** ; ce script remplace ces noms par **SQL_in** et **SQL_out** :

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

1. Vous pouvez aussi générer des valeurs en utilisant simplement le script R sans données d’entrée (`@input_data_1` est vide).

   Le script suivant génère le texte « hello » et « world ».

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

    ![Résultats de la requête en utilisant @script comme entrée](./media/r-data-generated-output.png)

## <a name="check-r-version"></a>Vérifier la version de R

Si vous voulez connaître la version de R qui est installée dans votre instance SQL Server, exécutez le script suivant.

```sql
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(version)';
GO
```

La fonction R `print` retourne la version dans la fenêtre **Messages**. Dans l’exemple de sortie ci-dessous, vous pouvez voir que la version installée de R est dans ce cas la version 3.4.4.

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

## <a name="list-r-packages"></a>Lister les packages R

Microsoft fournit un certain nombre de packages R préinstallés avec SQL Server Machine Learning Services.

Pour afficher la liste des packages R installés, dont la version, les dépendances, la licence et le chemin de la bibliothèque, exécutez le script suivant.

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

La sortie provient de `installed.packages()` dans R et est retournée sous forme de jeu de résultats.

**Résultats**

![Packages installés dans R](./media/rsql-installed-packages.png) 

## <a name="next-steps"></a>Étapes suivantes

Pour savoir comment utiliser des structures de données quand R est utilisé dans SQL Server Machine Learning Services, suivez ce démarrage rapide :

> [!div class="nextstepaction"]
> [Gérer les objets et types de données en utilisant R dans SQL Server Machine Learning Services](quickstart-r-data-types-and-objects.md)

Pour plus d’informations sur l’utilisation de R dans SQL Server Machine Learning Services, consultez les articles suivants :

- [Écrire des fonctions R avancées avec SQL Server Machine Learning Services](quickstart-r-functions.md)
- [Créer et scorer un modèle prédictif dans R avec SQL Server Machine Learning Services](quickstart-r-train-score-model.md)
- [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
