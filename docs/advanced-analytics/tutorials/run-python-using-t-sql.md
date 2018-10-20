---
title: Exécutez le code Python à l’aide de T-SQL sur SQL Server | Microsoft Docs
description: Découvrez les principes de base pour l’exécution de code Python à l’aide de T-SQL et des procédures stockées sur une instance du moteur de base de données SQL Server pour laquelle l’intégration de Python est activée.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e22b280c4fea395f8c7cf7c4b559d5ff5a22d6c1
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461915"
---
# <a name="run-python-using-t-sql"></a>Exécuter Python avec T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment vous pouvez exécuter le code Python dans SQL Server 2017. Il vous guide dans les principes fondamentaux de déplacement de données entre SQL Server et Python : configuration requise, les structures de données, les entrées et sorties. Il explique également comment encapsuler le code Python bien formé dans une procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) pour générer, former et utiliser des modèles d’apprentissage automatique dans SQL Server.

## <a name="prerequisites"></a>Prérequis

Pour exécuter l’exemple de code dans ces exercices, vous devez tout d’abord installer SQL Server 2017 et activer les Services Machine Learning sur l’instance, comme décrit dans [installer SQL Server 2017 Machine Learning Services (en base de données)](../install/sql-machine-learning-services-windows-install.md). 

Vous devez également installer [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). Également, vous pouvez utiliser un autre base de données gestion ou requête outil, tant qu’il peut se connecter à un serveur et la base de données et exécuter une requête T-SQL ou une procédure stockée.

Lorsque votre environnement est prêt, revenez à cette page pour savoir comment exécuter du code Python dans le contexte d’une procédure stockée. 

## <a name="verify-python-exists"></a>Vérifiez que Python existe

Les étapes suivantes confirmer que Python est activé et que le service Launchpad de SQL Server est en cours d’exécution.

1. Vérifiez si l’intégration de Python est installée sur l’instance du moteur de base de données. Vous devriez trouver **python.exe** dans un dossier appelé **PYTHON_SERVICES** à C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\. Il s’agit de l’exécutable de Python SQL Server utilise pour exécuter le code Python.

2. Vérifiez si le script externe est activé. Dans Management Studio, exécutez l’instruction suivante :

    ```sql
    sp_configure 'external scripts enabled'
    ```

    Si **run_value** est 1, la fonctionnalité d’apprentissage machine est installé et prêt à utiliser.

    Une cause courante d’erreurs est que le [service SQL Server Launchpad](../concepts/extensibility-framework.md#launchpad), qui gère la communication entre SQL Server et Python, s’est arrêté. Vous pouvez afficher l’état de Launchpad à l’aide de la Windows **Services** panneau, ou en ouvrant le Gestionnaire de Configuration SQL Server. Si le service est arrêté, redémarrez-le.

3. Vérifiez que le runtime Python est fonctionne et communique avec SQL Server. Pour ce faire, ouvrez une nouvelle **requête** fenêtre dans SQL Server Management Studio et connectez-vous à l’instance où Python a été installé.

    ```sql
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'print(3+4)'
    ```

    Si tout va bien, vous devez voir un message de résultat similaire à celle-ci

    ```text
    STDOUT message(s) from external script: 
    7
    ```

3. Si vous obtenez des erreurs, il existe une variété de choses à que faire pour vous assurer que le serveur et Python peut communiquer. 

    Vous devez ajouter le groupe d’utilisateurs Windows `SQLRUserGroup` en tant que connexion sur l’instance, pour vous assurer que Launchpad peut assurer la communication entre Python et SQL Server. (Le même groupe est utilisé pour les deux R et l’exécution de code Python.) Pour plus d’informations, consultez [l’authentification implicite activé](../security/add-sqlrusergroup-to-database.md).
    
    En outre, vous devrez peut-être activer les protocoles réseau qui ont été désactivées, ou ouvrir le pare-feu pour que SQL Server peut communiquer avec des clients externes. Pour plus d’informations, consultez [dépannage de l’installation](../common-issues-external-script-execution.md).

## <a name="basic-python-interaction"></a>Interaction de Python de base

Il existe deux façons d’exécuter le code Python dans SQL Server :

+ Ajouter un script Python en tant qu’argument de la procédure stockée système, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ À partir d’un [à distance client Python](../python/setup-python-client-tools-sql.md), connectez-vous à SQL Server et d’exécuter du code à l’aide de SQL Server comme contexte de calcul. Cela nécessite [revoscalepy](../python/what-is-revoscalepy.md).

L’exercice suivant se concentre sur le premier modèle d’interaction : comment passer de code Python à une procédure stockée.

1. Exécuter du code simple pour voir comment les données sont transmises dans les deux sens entre SQL Server et Python.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

2. En supposant que vous avez tout configuré correctement et que Python et SQL Server sont communiquent entre eux, le résultat correct est calculé et Python `print` fonction retourne le résultat à la **Messages** windows.

    **Résultats**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```
    
    Lors de l’obtention **stdout** messages est pratique lorsque vous testez votre code, plus souvent vous avez besoin retourner les résultats dans un format tabulaire, afin que vous pouvez utiliser dans une application ou écrire dans une table. 

Pour l’instant, n’oubliez pas ces règles :

+ Tous les éléments à l’intérieur de la `@script` argument doit être le code Python valide. 
+ Le code doit respecter toutes les règles proche du langage Python concernant la mise en retrait, les noms de variables et ainsi de suite. Lorsque vous recevez une erreur, vérifiez votre espace blanc et la casse.
+ Si vous utilisez toutes les bibliothèques qui ne sont pas chargés par défaut, vous devez utiliser une instruction d’importation au début de votre script pour les charger. SQL Server ajoute plusieurs bibliothèques spécifiques au produit. Pour plus d’informations, consultez [bibliothèques Python](../python/python-libraries-and-data-types.md).
+ Si la bibliothèque n’est pas déjà installée, arrêter et installer le package Python en dehors de SQL Server, comme indiqué ici : [installer de nouveaux packages de Python sur SQL Server](../python/install-additional-python-packages-on-sql-server.md)

## <a name="inputs-and-outputs"></a>Entrées et sorties

Par défaut, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) accepte un seul dataset d’entrée, vous fournissez en général sous la forme d’une requête SQL valide. 

Autres types d’entrée peuvent être passés en tant que variables SQL : par exemple, vous pouvez passer un modèle formé en tant que variable, à l’aide d’une fonction de sérialisation comme [pickle](https://docs.python.org/3.0/library/pickle.html) ou [rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) pour écrire le modèle un format binaire.

La procédure stockée retourne un seul Python [pandas](http://pandas.pydata.org/pandas-docs/stable/index.html) de trame de données en tant que sortie, mais vous pouvez également générer des valeurs scalaires et des modèles en tant que variables. Vous pouvez par exemple, un modèle formé en tant que binaire variable de sortie et passe à une instruction T-SQL INSERT, pour écrire ce modèle dans une table. Vous pouvez également générer des tracés (au format binaire) ou des valeurs scalaires (les valeurs individuelles, telles que la date et l’heure, la durée pour former le modèle et ainsi de suite).

Pour l’instant, examinons simplement la valeur par défaut des variables d’entrée et de sortie de sp_execute_external_script : `InputDataSet` et `OutputDataSet`. 

1. Exécutez le code suivant pour appliquer quelques formules mathématiques et enregistrer les résultats.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    print(c)
    OutputDataSet = c
    '
    WITH RESULT SETS ((ResultValue float))
    ```

2. Vous devez obtenir une erreur, parce que le code Python génère une valeur scalaire, pas une trame de données.

    **Résultats**

    ```text
    line 43, in transform
        raise TypeError('OutputDataSet should be of type pandas.DataFrame')
    ```

3. Maintenant voir ce qui se passe quand vous passez un jeu de données tabulaire à Python, à l’aide de la variable d’entrée par défaut `InputDataSet`. 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    OutputDataSet = InputDataSet
    ',
    @input_data_1 = N'SELECT 1 as Col1'
    ```

    La procédure stockée retourne une trame de données automatiquement, sans que vous ayez à intervenir dans votre code Python.

    **Résultats**

    | Aucun columnname|
    |------|
    | 1|

    Par défaut, le jeu de données d’entrée sous forme de tableau unique porte le nom, `InputDataSet`. Toutefois, vous pouvez modifier ce nom en ajoutant une ligne comme celle-ci : `@input_data_1_name = N'myResultName'`.

    Noms de colonnes utilisés par Python ne sont jamais conservées dans la sortie. Bien que la requête d’entrée spécifié le nom de colonne `Col1`, ce nom n’est pas retourné, pas plus que les en-têtes de colonne utilisés par votre script Python. Pour spécifier un type de données et le nom de colonne lorsque vous affichez les données de SQL Server, utilisez le code T-SQL `WITH RESULT SETS` clause.

4. Cet exemple fournit de nouveaux noms pour les variables d’entrée et de sortie.

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    MyOutput = MyInput
    ',
    @input_data_1_name = N'MyInput',
    @input_data_1 = N'SELECT 1 as Col1',
    @output_data_1_name = N'MyOutput'
    WITH RESULT SETS ((ResultValue int))
    ```

    La clause WITH RESULT SET définit le schéma pour la sortie, étant donné que les noms de colonnes de Python ne sont jamais retournés avec la trame de données.

    **Résultats**

    | ResultValue|
    |------|
    | 1|

5. Maintenant examinons à présent une erreur de Python standard. Remplacez la ligne dans l’exemple précédent de `@input_data_1_name = N'MyInput'` à `@input_data_1_name = N'myinput'`.

    Erreurs de Python sont passés à vous en tant que messages, par le service de satellite utilisé par SQL Server. Les messages peuvent être longs et inclure des erreurs de SQL Server ou Launchpad en plus des erreurs de Python, par conséquent, soyez patient dans rentrer dans le texte. Le message clé est dans cette ligne :

    ```text
    MyOutput = MyInput
    NameError: name 'MyInput' is not defined
    ```

    Rappelez-vous que Python, tel que R, respecte la casse. Par conséquent, lorsque vous accédez à n’importe quel type d’erreur, veillez à vérifier vos noms de variables et rechercher des problèmes avec les types de données, mise en retrait et l’espacement.

## <a name="python-data-structures"></a>Structures de données Python

SQL Server s’appuie sur les Python **pandas** package, qui est parfaite pour travailler avec des données tabulaires. Toutefois, vous avez déjà vu que vous ne pouvez pas transmettre une valeur scalaire à partir de Python à SQL Server et pensez qu’il fonctionne « tout simplement ». Dans cette section, nous allons examiner certaines définitions de type de base de données, pour vous préparer pour les autres problèmes que vous pouvez rencontrer lors du passage des données tabulaires entre Python et SQL Server.

+ Une trame de données est une table avec _plusieurs_ colonnes.
+ Une seule colonne d’une trame de données est un objet de type liste appelé une série.
+ Une valeur unique est une cellule d’une trame de données et doit être appelée par index.

Par conséquent, comment vous expose le résultat unique d’un calcul comme une trame de données, si une trame de données requiert une structure tabulaire ? Une solution consiste à représenter la valeur scalaire unique sous la forme d’une série, ce qui est facilement convertie en une trame de données. 

1. Cet exemple effectue une simple opération arithmétique simple et convertit une valeur scalaire en une série. Une série requiert un index, vous pouvez affecter manuellement, comme illustré ici, ou par programmation.

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

### <a name="convert-series-to-data-frame"></a>Convertir en série trame de données

Avoir converti nos résultats mathématiques scalaire vers une structure tabulaire, nous devons encore les convertir en un format que SQL Server peut gérer. 

1. Pour convertir une série à une trame de données, appelez les pandas [DataFrame](http://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe) (méthode).

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

2. Notez que les valeurs d’index ne sont pas la sortie, même si vous utilisez l’index pour obtenir des valeurs spécifiques à partir de la trame de données.

    **Résultats**

    |ResultValue|
    |------|
    |0.5|
    |2|

### <a name="output-values-into-dataframe-using-an-index"></a>Valeurs de sortie dans une trame de données à l’aide d’un index

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

Cet exercice a été conçu pour vous donner une idée de la façon de travailler avec des structures de données différentes de Python et de vous assurer de qu'obtenir le résultat correct, comme une trame de données. Vous pouvez ont conclu cette sortie de valeur unique comme une trame de données est plus difficile qu’elle en vaut ! Heureusement, vous pouvez facilement passer tous les types de valeurs dans et hors de la procédure stockée en tant que variables. Cela est traité dans la leçon suivante.

## <a name="tips"></a>Conseils

+ Parmi les langages de programmation Python est un des plus flexible en ce qui concerne les guillemets simples et des guillemets doubles ; ils sont pratiquement interchangeables. 

    Toutefois, T-SQL utilise des guillemets simples pour uniquement certaines choses et le `@script` argument utilise les guillemets simples pour encadrer le code Python sous forme de chaîne Unicode. Par conséquent, vous devrez peut-être vérifier votre code Python et remplacer des guillemets simples par des guillemets doubles.

+ Impossible de trouver la procédure stockée, `sp_execute_external_script`? Cela signifie que vous n’avez pas probablement fini de configurer l’instance pour prendre en charge l’exécution du script externe. Après avoir exécuté le programme d’installation de SQL Server 2017 et sélection de Python comme le langage d’apprentissage, vous devez explicitement activer la fonctionnalité à l’aide `sp_configure`, puis redémarrez l’instance. 

    Pour plus d’informations, consultez [installer SQL Server 2017 Machine Learning Services (en base de données)](../install/sql-machine-learning-services-windows-install.md).

## <a name="next-steps"></a>Étapes suivantes

[Configurer le dataset de démonstration Iris](demo-data-iris-in-sql.md)