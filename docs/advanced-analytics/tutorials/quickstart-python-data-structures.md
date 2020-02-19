---
title: 'Démarrage rapide : Structures de données Python'
description: Dans ce démarrage rapide, vous allez apprendre à utiliser des structures de données et des objets de données dans Python et SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2020
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 0f04e021664a92241c8c029d296a298b10c142d2
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "76831899"
---
# <a name="quickstart-data-structures-and-objects-using-python-in-sql-server-machine-learning-services"></a>Démarrage rapide : Structures de données et objets en utilisant Python dans SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Suivez ce guide de démarrage rapide pour savoir comment utiliser des structures de données quand Python est utilisé dans SQL Server Machine Learning Services.

SQL Server s’appuie sur le package **pandas** Python, qui est idéal pour travailler avec des données tabulaires. Toutefois, vous ne pouvez pas transmettre un scalaire de Python à SQL Server et vous attendre à ce qu’il fonctionne. Dans ce démarrage rapide, vous allez passer en revue certaines définitions de structure de données de base afin de vous préparer à d’autres problèmes que vous pourriez rencontrer lors de la transmission de données tabulaires entre Python et SQL Server.

Voici les concepts à connaître :

- Une trame de données est une table avec _plusieurs_ colonnes.
- Une colonne d’une trame de données est un objet de type liste appelé « série ».
- Une valeur d’une trame de données est appelée une cellule et est accessible par index.

Comment exposeriez-vous le résultat d’un calcul en tant que trame de données, si un élément data.frame requiert une structure tabulaire ? Une solution pourrait être de représenter la valeur scalaire en tant que série, qui est facilement convertible en trame de données. 

> [!NOTE]
> Lorsque les dates sont renvoyées, Python dans SQL utilise DATETIME qui a une plage de dates limitée de 1753-01-01(-53690) à 9999-12-31(2958463). 

## <a name="prerequisites"></a>Conditions préalables requises

- Ce démarrage rapide nécessite l’accès à une instance de SQL Server avec [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), ainsi que l’installation du langage Python.

- Vous avez également besoin d’un outil pour exécuter des requêtes SQL qui contiennent des scripts Python. Vous pouvez exécuter ces scripts à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="scalar-value-as-a-series"></a>Valeur scalaire en tant que série

Cet exemple effectue une simple opération mathématique et convertit un scalaire en une série.

1. Une série requiert un index, que vous pouvez assigner manuellement, comme illustré ici, ou par programmation.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   a = 1
   b = 2
   c = a/b
   print(c)
   s = pandas.Series(c, index =["simple math example 1"])
   print(s)
   '
   ```

   Étant donné que la série n’a pas été convertie en élément data.frame, les valeurs sont renvoyées dans la fenêtre Messages, mais vous pouvez voir que les résultats sont dans un format tabulaire plus grand.

   **Résultats**

   ```text
   STDOUT message(s) from external script: 
   0.5
   simple math example 1    0.5
   dtype: float64
   ```

1. Pour augmenter la longueur de la série, vous pouvez ajouter de nouvelles valeurs à l’aide d’un tableau. 

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   a = 1
   b = 2
   c = a/b
   d = a*b
   s = pandas.Series([c,d])
   print(s)
   '
   ```

   Si vous ne spécifiez pas d’index, un index avec des valeurs comprises entre 0 et la longueur du tableau est généré.

   **Résultats**

   ```text
   STDOUT message(s) from external script: 
   0    0.5
   1    2.0
   dtype: float64
   ```

1. Si vous augmentez le nombre de valeurs de **l’index**, mais que vous n’ajoutez pas de nouvelles valeurs de **données**, les valeurs de données sont répétées pour remplir la série.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   a = 1
   b = 2
   c = a/b
   s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
   print(s)
   '
   ```

   **Résultats**

   ```text
   STDOUT message(s) from external script: 
   0.5
   simple math example 1    0.5
   simple math example 2    0.5
   dtype: float64
   ```

## <a name="convert-series-to-data-frame"></a>Convertir une série en trame de données

La conversion du scalaire permet d’obtenir une structure tabulaire. Vous devez toutefois la convertir en un format pouvant être traité par SQL Server.

1. Pour convertir une série en élément data.frame, appelez la méthode [DataFrame](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) pandas.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   a = 1
   b = 2
   c = a/b
   d = a*b
   s = pandas.Series([c,d])
   print(s)
   df = pd.DataFrame(s)
   OutputDataSet = df
   '
   WITH RESULT SETS((ResultValue FLOAT))
   ```

   Le résultat est illustré ci-dessous. Même si vous utilisez l’index pour récupérer des valeurs spécifiques à partir de l’élément data.frame, les valeurs d’index ne font pas partie de la sortie.

   **Résultats**

   |ResultValue|
   |------|
   |0.5|
   |2|

## <a name="output-values-into-dataframe"></a>Valeurs de sortie dans l’élément data.frame

À présent, vous allez générer des valeurs spécifiques à partir de deux séries de résultats mathématiques dans un élément data.frame. La première a un index de valeurs séquentielles générées par Python. La seconde utilise un index arbitraire de valeurs de chaîne.

1. L’exemple suivant obtient une valeur de la série à l’aide d’un index d’entiers.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   a = 1
   b = 2
   c = a/b
   d = a*b
   s = pandas.Series([c,d])
   print(s)
   df = pd.DataFrame(s, index=[1])
   OutputDataSet = df
   '
   WITH RESULT SETS((ResultValue FLOAT))
   ```

   **Résultats**

   |ResultValue|
   |------|
   |2|

   N’oubliez pas que l’index généré automatiquement commence à 0. Essayez d’utiliser une valeur d’index hors de la plage pour voir ce qui se passe.

1. À présent, récupérez une valeur de l’autre trame de données à l’aide d’un index de chaîne.

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   a = 1
   b = 2
   c = a/b
   s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
   print(s)
   df = pd.DataFrame(s, index=["simple math example 1"])
   OutputDataSet = df
   '
   WITH RESULT SETS((ResultValue FLOAT))
   ```

   **Résultats**

   |ResultValue|
   |------|
   |0.5|

   Si vous essayez d’utiliser un index numérique pour obtenir une valeur de cette série, vous recevez une erreur.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur l’écriture de fonctions Python avancées dans SQL Server, suivez ce démarrage rapide :

> [!div class="nextstepaction"]
> [Écrire des fonctions Python avancées avec SQL Server Machine Learning Services](quickstart-python-functions.md)

Pour plus d’informations sur l’utilisation de Python dans SQL Server Machine Learning Services, consultez les articles suivants :

- [Créer et scorer un modèle prédictif dans Python](quickstart-python-train-score-model.md)
- [Qu’est-ce que SQL Server Machine Learning Services (Python et R) ?](../what-is-sql-server-machine-learning.md)
