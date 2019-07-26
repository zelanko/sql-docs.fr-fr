---
title: Démarrage rapide pour travailler avec des structures de données dans python
description: Dans ce guide de démarrage rapide pour le script Python dans SQL Server, Découvrez comment utiliser les structures de données avec la procédure stockée système sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 17b2c150368b32960907d6fdd2e31b109f51d771
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469638"
---
# <a name="quickstart-python-data-structures-in-sql-server"></a>Démarrage rapide : Structures de données python dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Ce guide de démarrage rapide montre comment utiliser des structures de données lors de l’utilisation de Python dans SQL Server Machine Learning Services.

SQL Server s’appuie sur le package  python pandas, qui est parfait pour travailler avec des données tabulaires. Toutefois, vous ne pouvez pas passer un scalaire de Python à SQL Server et vous attendre à ce qu’il «fonctionne» simplement. Dans ce guide de démarrage rapide, nous allons passer en revue certaines définitions de type de données de base afin de vous préparer à d’autres problèmes que vous pouvez rencontrer lors du passage de données tabulaires entre Python et SQL Server.

+ Une trame de données est une table avec _plusieurs_ colonnes.
+ Une seule colonne d’un tableau est un objet de type liste appelé une série.
+ Une valeur unique est une cellule d’une trame de données et doit être appelée par index.

Comment exposeriez-vous le résultat unique d’un calcul en tant que trame de données, si un frame Data. Frame requiert une structure tabulaire? Une réponse consiste à représenter la valeur scalaire unique sous la forme d’une série, qui est facilement convertie en une trame de données. 

## <a name="prerequisites"></a>Prérequis

Un démarrage rapide précédent, [Vérifiez que Python existe dans SQL Server](quickstart-python-verify.md), fournit des informations et des liens pour configurer l’environnement python requis pour ce guide de démarrage rapide.

## <a name="scalar-value-as-a-series"></a>Valeur scalaire en tant que série

Cet exemple effectue une simple mathématique et convertit un scalaire en une série.

1. Une série requiert un index, que vous pouvez assigner manuellement, comme illustré ici, ou par programmation.

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

2. Étant donné que la série n’a pas été convertie en Data. Frame, les valeurs sont retournées dans la fenêtre messages, mais vous pouvez voir que les résultats sont dans un format tabulaire plus grand.

    **Résultats**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    dtype: float64
    ```

3. Pour augmenter la longueur de la série, vous pouvez ajouter de nouvelles valeurs à l’aide d’un tableau. 

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

    Si vous ne spécifiez pas d’index, un index dont les valeurs commencent par 0 et qui se terminent par la longueur du tableau est généré.

    **Résultats**

    ```text
    STDOUT message(s) from external script: 
    0    0.5
    1    2.0
    dtype: float64
    ```

4. Si vous augmentez le nombre de valeurs d' **index** , mais que vous n’ajoutez pas de nouvelles valeurs de **données** , les valeurs de données sont répétées pour remplir la série.

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

## <a name="convert-series-to-data-frame"></a>Convertir une série en trame de données

Après avoir converti nos résultats scalaires scalaires en une structure tabulaire, nous devons toujours les convertir dans un format que SQL Server pouvez gérer. 

1. Pour convertir une série en Data. Frame, appelez la méthode pandas [tableau](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) .

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

2. Le résultat est indiqué ci-dessous. Même si vous utilisez l’index pour récupérer des valeurs spécifiques à partir de Data. Frame, les valeurs d’index ne font pas partie de la sortie.

    **Résultats**

    |ResultValue|
    |------|
    |0.5|
    |2|

## <a name="output-values-into-dataframe"></a>Valeurs de sortie dans Data. Frame

Voyons comment la conversion en Data. Frame fonctionne avec nos deux séries contenant les résultats d’opérations mathématiques simples. Le premier a un index de valeurs séquentielles générées par python. La seconde utilise un index arbitraire de valeurs de chaîne.

1. Cet exemple obtient une valeur de la série qui utilise un index d’entiers.

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

    N’oubliez pas que l’index généré automatiquement commence à 0. Essayez d’utiliser une valeur d’index hors limites pour voir ce qui se passe.

2. À présent, nous allons obtenir une valeur unique à partir de l’autre trame de données qui possède un index de chaîne. 

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

    Si vous essayez d’utiliser un index numérique pour obtenir une valeur de cette série, vous recevez une erreur.

## <a name="next-steps"></a>Étapes suivantes

Ensuite, vous allez créer un modèle prédictif à l’aide de Python dans SQL Server.

> [!div class="nextstepaction"]
> [Créer, former et utiliser un modèle Python avec des procédures stockées dans SQL Server](quickstart-python-train-score-in-tsql.md)