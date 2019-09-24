---
title: Créer et exécuter des scripts Python simples
titleSuffix: SQL Server Machine Learning Services
description: Créez et exécutez des scripts Python simples dans une instance de SQL Server avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a6f7fe62f746a8f6e74ebdf9f766b76c0edc720a
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71204296"
---
# <a name="quickstart-create-and-run-simple-python-scripts-with-sql-server-machine-learning-services"></a>Démarrage rapide : Créer et exécuter des scripts Python simples avec SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dans ce guide de démarrage rapide, vous allez créer et exécuter un ensemble de scripts Python simples à l’aide de [SQL Server machine learning services](../what-is-sql-server-machine-learning.md). Vous allez apprendre à inclure dans un wrapper un script Python bien formé dans la procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) et à exécuter le script dans une instance SQL Server.

## <a name="prerequisites"></a>Prérequis

- Ce guide de démarrage rapide nécessite l’accès à une instance de SQL Server avec [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md) avec le langage Python installé.

- Vous avez également besoin d’un outil pour exécuter des requêtes SQL qui contiennent des scripts Python. Vous pouvez exécuter ces scripts à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce guide de démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="run-a-simple-script"></a>Exécuter un script simple

Pour exécuter un script Python, vous devez le passer en tant qu’argument à la procédure stockée système [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).
Cette procédure stockée système démarre le runtime python dans le contexte d’SQL Server, transmet des données à python, gère les sessions utilisateur Python en toute sécurité et retourne les résultats au client.

Dans les étapes suivantes, vous allez exécuter cet exemple de script Python dans votre instance de SQL Server :

```python
a = 1
b = 2
c = a/b
d = a*b
print(c, d)
```

1. Ouvrez une nouvelle fenêtre de requête dans **SQL Server Management Studio** connectée à votre instance SQL Server.

1. Transmettez le script Python complet à `sp_execute_external_script` la procédure stockée.

   Le script est transmis via l' `@script` argument. Tout ce qui `@script` se trouve à l’intérieur de l’argument doit être un code python valide.

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

1. Le résultat correct est calculé et la fonction `print` python retourne le résultat dans la fenêtre **messages** .

   La valeur doit ressembler à ceci.

    **Résultats**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>Exécuter un script de Hello World

Un exemple de script classique est un exemple qui génère simplement la chaîne « Hello World ». Exécutez la commande suivante :

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'OutputDataSet = InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

Les entrées de `sp_execute_external_script` la procédure stockée sont les suivantes :

| | |
|-|-|
| @language | définit l’extension de langage à appeler, dans ce cas python |
| @script | définit les commandes passées au runtime python<br>L’intégralité de votre script Python doit être placée dans cet argument, en tant que texte Unicode. Vous pouvez également ajouter le texte à une variable de type **nvarchar** , puis appeler la variable |
| @input_data_1 | données retournées par la requête, passées au runtime Python, qui retourne les données à SQL Server sous la forme d’une trame de données |
|AVEC JEUX DE RÉSULTATS | la clause définit le schéma de la table de données retournée pour SQL Server, dans le cas présent, en ajoutant « Hello World » comme nom de colonne et **int** pour le type de données. |

La commande génère le texte suivant :

| Salut tout le monde |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>Utiliser les entrées et les sorties

Par défaut, `sp_execute_external_script` accepte un seul jeu de données comme entrée, ce qui est généralement fourni sous la forme d’une requête SQL valide. Elle retourne ensuite une trame de données python unique comme sortie.

Pour le moment, nous allons utiliser les variables d’entrée et de `sp_execute_external_script`sortie par défaut de : **InputDataSet** et **OutputDataSet**.

1. Créez une petite table de données de test.

    ```sql
    CREATE TABLE PythonTestData (col1 INT NOT NULL)
    
    INSERT INTO PythonTestData
    VALUES (1);
    
    INSERT INTO PythonTestData
    VALUES (10);
    
    INSERT INTO PythonTestData
    VALUES (100);
    GO
    ```

1. Utilisez l' `SELECT` instruction pour interroger la table.
  
    ```sql
    SELECT *
    FROM PythonTestData
    ```

    **Résultats**

    ![Contenu de la table PythonTestData](./media/select-pythontestdata.png)

1. Exécutez le script Python suivant. Il récupère les données de la table à l’aide `SELECT` de l’instruction, les passe via le runtime Python et retourne les données sous la forme d’une trame de données. La `WITH RESULT SETS` clause définit le schéma de la table de données retournée pour SQL, en ajoutant le nom de colonne *NewColName*.

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **Résultats**

    ![Sortie d’un script Python qui retourne des données à partir d’une table](./media/python-output-pythontestdata.png)

1. À présent, modifiez les noms des variables d’entrée et de sortie. Les noms des variables d’entrée et de sortie par défaut sont **InputDataSet** et **OutputDataSet**, le script suivant remplace les noms par **SQL_in** et **SQL_out**:

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'SQL_out = SQL_in;'
        , @input_data_1 = N'SELECT 12 as Col;'
        , @input_data_1_name  = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    Notez que Python respecte la casse. Les variables d’entrée et de sortie utilisées dans le script Python (**SQL_out**, **SQL_in**) doivent correspondre aux noms définis `@input_data_1_name` avec `@output_data_1_name`et, y compris la casse.

   > [!TIP]
   > Vous ne pouvez passer qu’un seul dataset d’entrée comme paramètre, et vous ne pouvez retourner qu’un seul dataset. Toutefois, vous pouvez appeler d’autres jeux de données à partir de votre code Python et vous pouvez retourner des sorties d’autres types en plus du DataSet. Vous pouvez aussi ajouter le mot clé OUTPUT à n’importe quel paramètre pour qu’il soit retourné avec les résultats.

1. Vous pouvez également générer des valeurs en utilisant simplement le script Python sans données d'`@input_data_1` entrée (la valeur est vide).

   Le script suivant génère le texte « Hello » et « World ».

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   mytextvariable = pandas.Series(["hello", " ", "world"]);
   OutputDataSet = pd.DataFrame(mytextvariable);
   '
       , @input_data_1 = N''
   WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
   ```

   **Résultats**

   ![Résultats de la @script requête en tant qu’entrée](./media/python-data-generated-output.png)

> [!NOTE]
> Python utilise des espaces à gauche pour regrouper des instructions. Ainsi, lorsque le script Python incorporé s’étend sur plusieurs lignes, comme dans le script précédent, n’essayez pas de mettre en retrait les commandes Python pour qu’elles soient alignées sur les commandes SQL. Par exemple, ce script génère une erreur :

  ```text
  EXECUTE sp_execute_external_script @language = N'Python'
      , @script = N'
      import pandas as pd
      mytextvariable = pandas.Series(["hello", " ", "world"]);
      OutputDataSet = pd.DataFrame(mytextvariable);
      '
      , @input_data_1 = N''
  WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
  ```

## <a name="check-python-version"></a>Vérifier la version de Python

Si vous souhaitez connaître la version de Python installée dans votre instance SQL Server, exécutez le script suivant.

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import sys
print(sys.version)
'
GO
```

La fonction `print` python retourne la version dans la fenêtre **messages** . Dans l’exemple de sortie ci-dessous, vous pouvez voir que, dans ce cas, la version de Python 3.5.2 est installée.

**Résultats**

```text
STDOUT message(s) from external script: 
3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
```

## <a name="list-python-packages"></a>Répertorier les packages python

Microsoft fournit un certain nombre de packages python préinstallés avec SQL Server Machine Learning Services dans votre instance SQL Server.

Pour afficher la liste des packages python installés, y compris la version, exécutez le script suivant.

```SQL
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import pip
for i in pip.get_installed_distributions():
    print(i)
'
GO
```

La sortie provient `pip.get_installed_distributions()` de dans Python et est renvoyée en tant que `STDOUT` messages.

**Résultats**

```text
STDOUT message(s) from external script:
xlwt 1.2.0
XlsxWriter 0.9.6
xlrd 1.0.0
win-unicode-console 0.5
widgetsnbextension 2.0.0
wheel 0.29.0
Werkzeug 0.12.1
wcwidth 0.1.7
unicodecsv 0.14.1
traitlets 4.3.2
tornado 4.4.2
toolz 0.8.2
. . .
```

## <a name="next-steps"></a>Étapes suivantes

Pour créer un modèle de Machine Learning à l’aide de Python dans SQL Server, suivez ce guide de démarrage rapide :

> [!div class="nextstepaction"]
> [Créer et évaluer un modèle prédictif dans Python avec SQL Server Machine Learning Services](quickstart-python-train-score-model.md)

Pour plus d’informations sur SQL Server Machine Learning Services, consultez les articles suivants.

- [Gérer les types de données et les objets à l’aide de Python dans SQL Server Machine Learning Services](quickstart-python-data-structures.md)
- [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
