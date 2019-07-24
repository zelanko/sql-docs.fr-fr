---
title: Exécuter des travaux Spark avec Spark & les outils Hive pour VS Code sur SQL Server Cluster Big Data
titleSuffix: SQL Server big data clusters
description: Soumettez un travail Spark avec les outils de la & Hive Spark pour Visual Studio Code sur SQL Server Cluster Big Data.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4458666792d7f4629b4e1820e98e2dbb9901c2b6
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425979"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-cluster-in-visual-studio-code"></a>Envoyer des travaux Spark sur SQL Server Cluster Big Data dans Visual Studio Code

Découvrez comment utiliser Spark & les outils Hive pour Visual Studio Code pour créer et envoyer des scripts PySpark pour Apache Spark. nous allons tout d’abord décrire comment installer les outils de la ruche Spark & dans Visual Studio Code. ensuite, nous allons vous montrer comment envoyer des travaux à Spark.  

Spark & les outils Hive peuvent être installés sur les plateformes prises en charge par Visual Studio Code, notamment Windows, Linux et macOS. Les prérequis pour les différentes plateformes sont détaillés ci-dessous.


## <a name="prerequisites"></a>Conditions préalables

Avant de poursuivre cet article, vérifiez que vous avez les éléments nécessaires suivants :

- Un cluster SQL Server Big Data. Consultez [SQL Server des clusters Big Data](https://docs.microsoft.com/sql/big-data-cluster/big-data-cluster-overview?view=sqlallproducts-allversions).
- [Visual Studio Code](https://code.visualstudio.com/).
- [Mono](https://www.mono-project.com/docs/getting-started/install/). Mono est nécessaire uniquement pour les plateformes Linux et MacOS.
- [Définir l’environnement interactif de PySpark pour Visual Studio Code](https://docs.microsoft.com/azure/hdinsight/set-up-pyspark-interactive-environment).
- Un répertoire local nommé **HDexample**.  Cet article utilise **C:\HD\HDexample**.

## <a name="install-spark--hive-tools"></a>Installer Spark & les outils Hive

Une fois que vous avez rempli les conditions préalables, vous pouvez installer Spark & les outils Hive pour Visual Studio Code.  Procédez comme suit pour installer Spark & les outils Hive:

1. Ouvrez Visual Studio Code.

2. À partir de la barre de menus, accédez à **Afficher** > **Extensions**.

3. Dans la zone de recherche, entrez **Spark & Hive**.

4. Sélectionnez **Spark & les outils Hive** dans les résultats de la recherche, puis sélectionnez **installer**.  

   ![Installer l’extension](./media/spark-hive-tools-vscode/extension.png)

5. Rechargez quand cela est nécessaire.

## <a name="open-work-folder"></a>Ouvrir le dossier de travail

Procédez comme suit pour ouvrir un dossier de travail et créer un fichier dans Visual Studio Code :

1. À partir de la barre de menus, accédez à **Fichier** > **Ouvrir le dossier...**  > **C:\HD\HDexample**, puis sélectionnez le bouton **Sélectionner le dossier**. Le dossier s’affiche dans la vue **Explorer** sur la gauche.

2. À partir de la vue **Explorer**, sélectionnez le dossier, **HDexample**, puis l’icône **Nouveau fichier** en regard du dossier de travail.

   ![Nouveau fichier](./media/spark-hive-tools-vscode/new-file.png)

3. Nommez le nouveau fichier avec `.py` l’extension de fichier (script Spark).  Cet exemple utilise **HelloWorld.py**.
4. Copiez et collez le code suivant dans le fichier de script :
   ```python
    import sys
    from operator import add
    from pyspark.sql import SparkSession, Row
    
    spark = SparkSession\
        .builder\
        .appName("PythonWordCount")\
        .getOrCreate()
    
    data = [Row(col1='pyspark and spark', col2=1), Row(col1='pyspark', col2=2), Row(col1='spark vs hadoop', col2=2), Row(col1='spark', col2=2), Row(col1='hadoop', col2=2)]
    df = spark.createDataFrame(data)
    lines = df.rdd.map(lambda r: r[0])

    counters = lines.flatMap(lambda x: x.split(' ')) \
        .map(lambda x: (x, 1)) \
        .reduceByKey(add)
    
    output = counters.collect()
    sortedCollection = sorted(output, key = lambda r: r[1], reverse = True)
    
    for (word, count) in sortedCollection:
        print("%s: %i" % (word, count))
   ```

## <a name="link-a-sql-server-big-data-cluster"></a>Lier un cluster SQL Server Big Data

Avant de pouvoir envoyer des scripts à vos clusters à partir de Visual Studio Code, vous devez lier un SQL Server Big Data cluster.

1. Dans la barre de menus, accédez à **Afficher** > la**palette de commandes...** , puis entrez **Spark/Hive: Lier un cluster**.

   ![commande de lien du cluster](./media/spark-hive-tools-vscode/link-cluster-command.png)

2. Sélectionnez type de cluster lié **SQL Server Big Data**.

3. Entrez SQL Server point de terminaison Big Data.

4. Entrez SQL Server nom d’utilisateur du cluster Big Data.

5. Entrez le mot de passe pour l’administrateur de l’utilisateur.

6. Définissez le nom d’affichage du cluster (facultatif).

7. Répertorier les clusters, consulter la vue **sortie** pour vérification.

## <a name="list-clusters"></a>Énumérer les clusters

1. Dans la barre de menus, accédez à **Afficher** > la**palette de commandes...** , puis entrez **Spark/Hive: Répertorier un cluster**.

2. Passez en revue la vue **OUTPUT**.  La vue affiche vos clusters liés.

    ![Définir la configuration du cluster par défaut](./media/spark-hive-tools-vscode/list-cluster-result.png)

## <a name="set-default-cluster"></a>Définir le cluster par défaut

1. Ouvrez à nouveau le dossier **HDexample** créé [précédemment](#open-work-folder) si vous l’aviez fermé.  

2. Sélectionnez le fichier **HelloWorld.py** créé [précédemment](#open-work-folder) et il s’ouvrira dans l’éditeur de script.

3. Liez un cluster si vous ne l’avez pas encore fait.

4. Cliquez avec le bouton droit sur l’éditeur de **script, puis sélectionnez Spark/Hive: Définir le cluster par défaut**.   

5. Sélectionnez un cluster à utiliser comme cluster par défaut pour le fichier de script actuel. Les outils mettent automatiquement à jour le fichier de configuration **.VSCode\settings.json**. 

   ![Définir la configuration du cluster par défaut](./media/spark-hive-tools-vscode/set-default-cluster-configuration.png)

## <a name="submit-interactive-pyspark-queries"></a>Envoyer des requêtes PySpark interactives

Vous pouvez envoyer des requêtes PySpark interactives en suivant les étapes ci-dessous:

1. Ouvrez à nouveau le dossier **HDexample** créé [précédemment](#open-work-folder) si vous l’aviez fermé.  

2. Sélectionnez le fichier **HelloWorld.py** créé [précédemment](#open-work-folder) et il s’ouvrira dans l’éditeur de script.

3. Liez un cluster si vous ne l’avez pas encore fait.

4. Choisissez tout le code, cliquez avec le bouton droit sur l’éditeur **de script, sélectionnez Spark: PySpark Interactive** pour envoyer la requête, ou utilisez le raccourci **Ctrl+Alt+I**.

   ![menu contextuel interactif pyspark](./media/spark-hive-tools-vscode/pyspark-interactive-right-click.png)

5. Sélectionnez un cluster autre que le cluster par défaut. Après quelques instants, les résultats de **python interactive** s’affichent dans un nouvel onglet. HDInsight Tools vous permet également d’envoyer un bloc de code au lieu du fichier de script entier à partir du menu contextuel. 

   ![fenêtre interactive Python interactive pyspark](./media/spark-hive-tools-vscode/pyspark-interactive-python-interactive-window.png) 

6. Entrez **«%% info»** , puis appuyez sur **MAJ + entrée** pour afficher les informations relatives à la tâche. (facultatif)

   ![afficher les informations sur le travail](./media/spark-hive-tools-vscode/pyspark-interactive-view-job-information.png)

   > [!NOTE] 
   >
   > Lorsque l’option **extension Python activée** est décochée dans les paramètres (le paramètre par défaut est activé), les résultats de l’interaction pyspark envoyés utilisent l’ancienne fenêtre.
   >
   > ![extension Python interactive pyspark désactivée](./media/spark-hive-tools-vscode/pyspark-interactive-python-extension-disabled.png)


## <a name="submit-pyspark-batch-job"></a>Envoi de la tâche de traitement par lots PySpark

1. Ouvrez à nouveau le dossier **HDexample** créé [précédemment](#open-work-folder) si vous l’aviez fermé.  

2. Sélectionnez le fichier **HelloWorld.py** créé [précédemment](#open-work-folder) et il s’ouvrira dans l’éditeur de script.

3. Liez un cluster si vous ne l’avez pas encore fait.

4. Cliquez avec le bouton droit sur l’éditeur de script **, puis sélectionnez Spark: PySpark Batch**, ou utilisez le raccourci **Ctrl+Alt+H**. 

5. Sélectionnez un cluster autre que le cluster par défaut. Une fois que vous avez envoyé un travail Python, les journaux d’activité d’envoi apparaissent dans la fenêtre **OUTPUT** (Sortie) dans Visual Studio Code. **L’URL de l’interface utilisateur Spark** et **l’URL de l’interface utilisateur Yarn** s’affichent également. Vous pouvez ouvrir l’URL dans un navigateur web pour suivre l’état du travail.

   ![Résultat de l’envoi du travail Python](./media/spark-hive-tools-vscode/submit-pythonjob-result.png) 

## <a name="apache-livy-configuration"></a>Configuration d’Apache Livy

La configuration [d’Apache Livy](https://livy.incubator.apache.org/) est prise en charge et peut être définie à l’emplacement **.VSCode\settings.json** dans le dossier de l’espace de travail. Actuellement, la configuration livy prend uniquement en charge le script Python. Pour plus d’informations, consultez [Lisez-moi Livy](https://github.com/cloudera/livy/blob/master/README.rst ).

### <a id="triggerlivyconf"></a>**Comment déclencher la configuration livy**

#### <a name="method-1"></a>Méthode 1

1. À partir de la barre de menus, accédez à **Fichier** > **Préférences** > **Paramètres**.  
2. Dans la zone de texte **Paramètres de recherche**, entrez **Envoi de travail HDInsight : Livy Conf**.  
3. Sélectionnez **Modifier dans settings.json** pour le résultat de recherche pertinent.

#### <a name="method-2"></a>Méthode 2

Envoyer un fichier, Notez que `.vscode` le dossier est ajouté automatiquement au dossier de travail. Vous pouvez trouver la configuration livy en cliquant `.vscode\settings.json`sur.

+ Paramètres du projet :

    ![Configuration de Livy](./media/spark-hive-tools-vscode/hdi-livyconfig.png)

>[!NOTE]
>Pour les paramètres **driverMomory** et **executorMomry**, définissez la valeur en spécifiant l’unité, par exemple 1 g ou 1 024 m. 

### <a name="supported-livy-configurations"></a>Configurations livy prises en charge

#### <a name="post-batches"></a>POSTER/Batches

**Corps de la demande**

| name | description | Type |
| :- | :- | :- |
| file | Fichier contenant l’application à exécuter | chemin (obligatoire) |
| proxyUser | Utilisateur auquel emprunter l’identité lors de l’exécution de la tâche | string |
| className | Classe principale Java/Spark de l’application | string |
| args | Arguments de ligne de commande pour l’application | liste de valeurs string |
| jars | Fichiers JAR à utiliser dans cette session | Liste de chaînes |
| pyFiles | Fichiers Python à utiliser dans cette session | Liste de chaînes |
| fichiers d'entrée | Fichiers à utiliser dans cette session | Liste de chaînes |
| driverMemory | Quantité de mémoire à utiliser pour le processus de pilote | string |
| driverCores | Nombre de cœurs à utiliser pour le processus de pilote | int |
| executorMemory | Quantité de mémoire à utiliser par processus de l’exécuteur | string |
| executorCores | Nombre de cœurs à utiliser pour chaque exécuteur | int |
| numExecutors | Nombre d’exécuteurs à lancer pour cette session | int |
| archives | Archives à utiliser dans cette session | Liste de chaînes |
| queue | Nom de la file d’attente YARN vers laquelle effectuer l’envoi | string |
| name | Nom de cette session | string |
| conf | Propriétés de configuration Spark. | Map of key=val |

#### <a name="response-body"></a>Corps de réponse

Objet de lot créé.

| name | description | Type |
| :- | :- | :- |
| id | ID de la session | int |
| appId | ID d’application de cette session | Chaîne |
| appInfo | Informations détaillées sur l’application | Map of key=val |
| log | Lignes du journal | liste de valeurs string |
| state | État du lot | chaîne |

>[!NOTE]
>La configuration livy assignée s’affiche dans le volet de sortie lors de l’envoi du script.

## <a name="additional-features"></a>Fonctionnalités supplémentaires

La ruche Spark & pour Visual Studio Code prend en charge les fonctionnalités suivantes:

- **Saisie semi-automatique IntelliSense**. Fenêtre contextuelle de suggestions de mots-clés, de méthodes, de variables, etc. Des icônes différentes représentent des types d’objets différents.

    ![Outils de la ruche Spark & pour les types d’objets IntelliSense Visual Studio Code](./media/spark-hive-tools-vscode/hdinsight-for-vscode-auto-complete-objects.png)
- **Marqueur d’erreurs IntelliSense**. Le service de langage souligne les erreurs de saisie dans le script Hive.     
- **Coloration syntaxique**. Le service de langage utilise plusieurs couleurs pour différencier les variables, les mots-clés, le type des données, les fonctions, etc. 

    ![Spark & les outils Hive pour les points de Visual Studio Code syntaxique](./media/spark-hive-tools-vscode/hdinsight-for-vscode-syntax-highlights.png)

## <a name="unlink-cluster"></a>Supprimer le lien du cluster

1. Dans la barre de menus, accédez à **Afficher** > la**palette de commandes...** , puis entrez **Spark/Hive: Supprimer le lien du cluster**.  

2. Sélectionnez le cluster pour lequel supprimer le lien.  

3. Passez en revue la vue **OUTPUT** à des fins de vérification.  

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur SQL Server Cluster Big Data et les scénarios connexes, consultez [SQL Server clusters Big Data](https://docs.microsoft.com/sql/big-data-cluster/big-data-cluster-overview?view=sqlallproducts-allversions).
