---
title: Guide de démarrage rapide pour l’utilisation des structures de données dans Python - SQL Server Machine Learning
description: Dans ce démarrage rapide pour le script Python dans SQL Server, découvrez comment utiliser des structures de données avec la procédure stockée sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 0105cf099bbee30d167c498646778520fcdbd805
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046792"
---
# <a name="quickstart-python-data-structures-in-sql-server"></a>Démarrage rapide : Structures de données de Python dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Ce démarrage rapide montre comment utiliser les structures de données lors de l’utilisation de Python dans SQL Server Machine Learning Services.

SQL Server s’appuie sur les Python **pandas** package, qui est parfaite pour travailler avec des données tabulaires. Toutefois, vous ne pouvez pas transmettre une valeur scalaire à partir de Python à SQL Server et pensez qu’il fonctionne « tout simplement ». Dans ce démarrage rapide, nous allons examiner certaines définitions de type de base de données, pour vous préparer pour les autres problèmes que vous pouvez rencontrer lors du passage des données tabulaires entre Python et SQL Server.

+ Une trame de données est une table avec _plusieurs_ colonnes.
+ Une seule colonne d’une trame de données est un objet de type liste appelé une série.
+ Une valeur unique est une cellule d’une trame de données et doit être appelée par index.

Comment vous expose le résultat unique d’un calcul comme une trame de données, si une trame de données requiert une structure tabulaire ? Une solution consiste à représenter la valeur scalaire unique sous la forme d’une série, ce qui est facilement convertie en une trame de données. 

## <a name="prerequisites"></a>Prérequis

Un guide de démarrage rapide précédent, [Python vérifier existe dans SQL Server](quickstart-python-verify.md), fournit des informations et des liens pour la configuration de l’environnement Python requis pour ce démarrage rapide.

## <a name="scalar-value-as-a-series"></a>Valeur scalaire en tant que série

Cet exemple effectue une simple opération arithmétique simple et convertit une valeur scalaire en une série.

1. Une série requiert un index, vous pouvez affecter manuellement, comme illustré ici, ou par programmation.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    print(c)
    s = pandas.Series(c, index =["simple math example 1"])
    print(s)
    '
    ```

2. Étant donné que la série n’a pas été convertie en une trame de données, les valeurs sont retournées dans la fenêtre de Messages, mais vous pouvez voir que les résultats sont dans un format tabulaire plus.

    **Résultats**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    dtype: float64
    ```

3. Pour augmenter la longueur de la série, vous pouvez ajouter de nouvelles valeurs, à l’aide d’un tableau. 

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    '
    ```

    Si vous ne spécifiez pas un index, qui comporte des valeurs commençant par 0 et se terminant par la longueur du tableau est généré par un index.

    **Résultats**

    ```text
    STDOUT message(s) from external script: 
    0    0.5
    1    2.0
    dtype: float64
    ```

4. Si vous augmentez le nombre de **index** valeurs, mais ne pas ajouter de nouveaux **données** valeurs, les valeurs de données sont répétées pour remplir la série.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
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

## <a name="convert-series-to-data-frame"></a>Convertir en série trame de données

Avoir converti nos résultats mathématiques scalaire vers une structure tabulaire, nous devons encore les convertir en un format que SQL Server peut gérer. 

1. Pour convertir une série à une trame de données, appelez les pandas [DataFrame](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) (méthode).

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
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
    WITH RESULT SETS (( ResultValue float ))
    ```

2. Le résultat est illustré ci-dessous. Même si vous utilisez l’index pour obtenir des valeurs spécifiques à partir de la trame de données, les valeurs d’index ne sont pas partie de la sortie.

    **Résultats**

    |ResultValue|
    |------|
    |0.5|
    |2|

## <a name="output-values-into-dataframe"></a>Valeurs de sortie dans une trame de données

Nous allons voir comment la conversion en une trame de données fonctionne avec nos deux séries contenant les résultats des opérations mathématiques simples. Le premier a un index de valeurs séquentielles générées par Python. La seconde utilise un index arbitraire de valeurs de chaîne.

1. Cet exemple obtient une valeur à partir de la série qui utilise un index d’entiers.

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
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
    WITH RESULT SETS (( ResultValue float ))
    ```

    N’oubliez pas que l’index généré automatiquement commence à 0. Essayez d’utiliser une valeur d’index de plage à l’emploi et observez le résultat.

2. Maintenant nous allons obtenir une valeur unique à partir d’autres trame de données qui possède un index de chaîne. 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    df = pd.DataFrame(s, index=["simple math example 1"])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

    **Résultats**

    |ResultValue|
    |------|
    |0.5|

    Si vous essayez d’utiliser un index numérique pour obtenir une valeur à partir de cette série, vous obtenez une erreur.

## <a name="next-steps"></a>Étapes suivantes

Ensuite, vous allez générer un modèle prédictif à l’aide de Python dans SQL Server.

> [!div class="nextstepaction"]
> [Créer, former et utiliser un modèle Python avec des procédures stockées dans SQL Server](quickstart-python-train-score-in-tsql.md)