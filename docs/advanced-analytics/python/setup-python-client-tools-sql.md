---
title: Configurer un client de science des données pour le développement python
description: Configurez un environnement local Python (Jupyter Notebook ou PyCharm) pour les connexions distantes à SQL Server Machine Learning Services avec Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: b5f406ec4b6cfbd65db7a4ecd3a1ad14dff6d8e1
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470241"
---
# <a name="set-up-a-data-science-client-for-python-development-on-sql-server-machine-learning-services"></a>Configurer un client de science des données pour le développement Python sur SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L’intégration Python est disponible à partir de SQL Server 2017 ou version ultérieure lorsque vous incluez l’option python dans une [installation machine learning services (en base de données)](../install/sql-machine-learning-services-windows-install.md). 

Pour développer et déployer des solutions Python pour SQL Server, installez les [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) et autres bibliothèques python de Microsoft sur votre station de travail de développement. La bibliothèque revoscalepy, qui est également sur l’instance de SQL Server distante, coordonne les demandes de traitement entre les deux systèmes. 

Dans cet article, Découvrez comment configurer une station de travail de développement Python pour pouvoir interagir avec une SQL Server distante activée pour l’intégration de Machine Learning et Python. Après avoir effectué les étapes de cet article, vous aurez les mêmes bibliothèques python que celles sur SQL Server. Vous saurez également comment envoyer (push) des calculs à partir d’une session python locale vers une session python distante sur SQL Server.

![Composants client-serveur](media/sqlmls-python-client-revo.png "Sessions et bibliothèques python locales et") distantes

Pour valider l’installation, vous pouvez utiliser les blocs-notes Jupyter intégrés comme décrit dans cet article, ou [lier les bibliothèques](#install-ide) à PyCharm ou à tout autre IDE que vous utilisez normalement.

> [!Tip]
> Pour obtenir une démonstration vidéo de ces exercices, consultez [exécuter à distance R et Python dans SQL Server à partir de blocs-notes Jupyter](https://youtu.be/D5erljpJDjE).

> [!Note]
> Une alternative à l’installation de la bibliothèque cliente consiste à utiliser un [serveur autonome](../install/sql-machine-learning-standalone-windows-install.md) comme client riche, que certains clients préfèrent pour un travail de scénario plus approfondi. Un serveur autonome est entièrement découplé de SQL Server, mais étant donné qu’il a les mêmes bibliothèques Python, vous pouvez l’utiliser en tant que client pour SQL Server analytique dans la base de données. Vous pouvez également l’utiliser pour du travail non lié à SQL, y compris la possibilité d’importer et de modéliser des données à partir d’autres plateformes de données. Si vous installez un serveur autonome, vous pouvez trouver l’exécutable Python à l’emplacement suivant: `C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`. Pour valider votre installation, [ouvrez un bloc-notes Jupyter](#python-tools) pour exécuter des commandes à l’aide de Python. exe à cet emplacement.

## <a name="commonly-used-tools"></a>Outils couramment utilisés

Que vous soyez un développeur python nouveau dans SQL, ou un développeur SQL nouveau pour Python et l’analytique dans la base de données, vous aurez besoin d’un outil de développement Python et d’un éditeur de requête T-SQL comme [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) pour exercer toutes les fonctionnalités de analytique dans la base de données.

Pour le développement Python, vous pouvez utiliser des blocs-notes Jupyter, qui sont fournis dans la distribution Anaconda installée par SQL Server. Cet article explique comment démarrer des blocs-notes Jupyter pour pouvoir exécuter du code python localement et à distance sur SQL Server.

SSMS est un téléchargement distinct, utile pour créer et exécuter des procédures stockées sur SQL Server, y compris celles contenant du code Python. Presque tout le code python que vous écrivez dans des blocs-notes Jupyter peut être incorporé dans une procédure stockée. Vous pouvez parcourir d’autres guides de démarrage rapide pour en savoir plus sur [SSMS et Embedded python](../tutorials/quickstart-python-verify.md).

## <a name="1---install-python-packages"></a>1-installer les packages python

Les stations de travail locales doivent avoir les mêmes versions de package Python que celles de SQL Server, y compris les 4.2.0 de base Anaconda avec la distribution Python 3.5.2 et les packages spécifiques à Microsoft.

Un script d’installation ajoute trois bibliothèques spécifiques à Microsoft au client python. Le script installe [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package), utilisé pour définir des objets de source de données et le contexte de calcul. Il installe [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) en fournissant des algorithmes de machine learning. Le package [azureml](https://docs.microsoft.com/machine-learning-server/python-reference/azureml-model-management-sdk/azureml-model-management-sdk) est également installé, mais il s’applique aux tâches de fonctionnement associées à un contexte de machine learning Server autonome (non-instance) et peut être d’une utilisation limitée pour l’analyse dans la base de données.

1. Téléchargez un script d’installation.

  + [https://aka.ms/mls-py](https://aka.ms/mls-py)installe la version 9.2.1 des packages Microsoft Python. Cette version correspond à une instance par défaut SQL Server 2017. 

  + [https://aka.ms/mls93-py](https://aka.ms/mls93-py)installe la version 9,3 des packages Microsoft Python. Cette version est un meilleur choix si votre instance distante SQL Server 2017 est [liée à Machine Learning Server 9,3](../install/upgrade-r-and-python.md).

2. Ouvrez une fenêtre PowerShell avec des autorisations d’administrateur élevées (cliquez avec le bouton droit sur **exécuter en tant qu’administrateur**).

3. Accédez au dossier dans lequel vous avez téléchargé le programme d’installation et exécutez le script. Ajoutez l' `-InstallFolder` argument de ligne de commande pour spécifier un emplacement de dossier pour les bibliothèques. Exemple : 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls"
   ```

Si vous omettez le dossier d’installation, la valeur par défaut est C:\Program Files\Microsoft\PyForMLS.

L’installation prend un certain temps. Vous pouvez surveiller la progression dans la fenêtre PowerShell. Une fois l’installation terminée, vous disposez d’un ensemble complet de packages. 

> [!Tip] 
> Nous vous recommandons d’utiliser le [Forum aux questions sur Python pour Windows](https://docs.python.org/3/faq/windows.html) pour obtenir des informations générales sur purppose sur l’exécution de programmes Python sur Windows.

## <a name="2---locate-executables"></a>2-localiser les exécutables

Toujours dans PowerShell, répertoriez le contenu du dossier d’installation pour confirmer que Python. exe, les scripts et les autres packages sont installés. 

1. Entrez `cd \` pour accéder au lecteur racine, puis entrez le chemin d’accès que vous avez `-InstallFolder` spécifié pour à l’étape précédente. Si vous avez omis ce paramètre au cours de l’installation, `cd C:\Program Files\Microsoft\PyForMLS`la valeur par défaut est.

2. Entrez `dir *.exe` pour répertorier les exécutables. Vous devez voir **Python. exe**, **pythonw. exe**et **Uninstall-Anaconda. exe**.

  ![Liste des exécutables python](media/powershell-python-exe.png)
   
Sur les systèmes dotés de plusieurs versions de Python, n’oubliez pas d’utiliser ce fichier Python. exe particulier si vous souhaitez charger **revoscalepy** et d’autres packages Microsoft.

> [!Note] 
> Le script d’installation ne modifie pas la variable d’environnement PATH sur votre ordinateur, ce qui signifie que le nouvel interpréteur Python et les modules que vous venez d’installer ne sont pas automatiquement disponibles pour d’autres outils que vous pouvez avoir. Pour obtenir de l’aide sur la liaison de l’interpréteur et des bibliothèques python aux outils, consultez [installer un IDE](#install-ide).

<a name="python-tools"></a>

## <a name="3---open-jupyter-notebooks"></a>3-ouvrir les blocs-notes Jupyter

Anaconda comprend des blocs-notes Jupyter. À l’étape suivante, créez un bloc-notes et exécutez du code python contenant les bibliothèques que vous venez d’installer.

1. À l’invite PowerShell, toujours dans le répertoire C:\Program Files\Microsoft\PyForMLS, ouvrez les blocs-notes Jupyter à partir du dossier scripts:

  ```powershell
  .\Scripts\jupyter-notebook
  ```

  Un Notebook doit s’ouvrir dans votre navigateur par `https://localhost:8889/tree`défaut à l’adresse.

  Une autre façon de commencer est de double-cliquer sur **jupyter-Notebook. exe**. 

2. Cliquez sur **nouveau** , puis sur **python 3**.

  ![bloc-notes jupyter avec la nouvelle sélection python 3](media/jupyter-notebook-new-p3.png)

3. Entrez `import revoscalepy` et exécutez la commande pour charger l’une des bibliothèques spécifiques à Microsoft.

4. Entrez et exécutez `print(revoscalepy.__version__)` pour retourner les informations sur la version. Vous devez voir 9.2.1 ou 9.3.0. Vous pouvez utiliser l’une de ces versions avec [revoscalepy sur le serveur](../package-management/installed-package-information.md). 

4. Entrez une série plus complexe d’instructions. Cet exemple génère des statistiques de synthèse à l’aide de [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) sur un jeu de données local. D’autres fonctions récupèrent l’emplacement des exemples de données et créent un objet de source de données pour un fichier. XDF local.

  ```python
  import os
  from revoscalepy import rx_summary
  from revoscalepy import RxXdfData
  from revoscalepy import RxOptions
  sample_data_path = RxOptions.get_option("sampleDataDir")
  print(sample_data_path)
  ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
  summary = rx_summary("ArrDelay+DayOfWeek", ds)
  print(summary)
  ```

La capture d’écran suivante montre l’entrée et une partie de la sortie, tronquées par souci de concision.

  ![bloc-notes jupyter avec entrée et sortie revoscalepy](media/jupyter-notebook-local-revo.png)

## <a name="4---get-sql-permissions"></a>4-récupérer les autorisations SQL

Pour vous connecter à une instance de SQL Server pour exécuter des scripts et charger des données, vous devez disposer d’une connexion valide sur le serveur de base de données. Vous pouvez utiliser un compte de connexion SQL ou l’authentification Windows intégrée. Nous vous recommandons généralement d’utiliser l’authentification intégrée de Windows, mais l’utilisation de la connexion SQL est plus simple pour certains scénarios, en particulier lorsque votre script contient des chaînes de connexion à des données externes.

Au minimum, le compte utilisé pour exécuter le code doit avoir l’autorisation de lire dans les bases de données avec lesquelles vous travaillez, et l’autorisation spéciale exécuter n’importe quel SCRIPT externe. La plupart des développeurs requièrent également des autorisations pour créer des procédures stockées et écrire des données dans des tables contenant des données d’apprentissage ou des données notées. 

Demandez à l’administrateur de base de données de [configurer les autorisations suivantes pour votre compte](../security/user-permission.md), dans la base de données où vous utilisez Python:

+ **Exécutez un script externe** pour exécuter Python sur le serveur.
+ privilèges **db_datareader** pour exécuter les requêtes utilisées pour l’apprentissage du modèle.
+ **db_datawriter** pour écrire des données d’apprentissage ou des données notées.
+ **db_owner** pour créer des objets tels que des procédures stockées, des tables et des fonctions. 
  Vous avez également besoin de **db_owner** pour créer des exemples et des bases de données de test. 

Si votre code nécessite des packages qui ne sont pas installés par défaut avec SQL Server, contactez l’administrateur de base de données pour que les packages soient installés avec l’instance. SQL Server est un environnement sécurisé et il existe des restrictions sur l’emplacement d’installation des packages. L’installation ad hoc des packages dans le cadre de votre code n’est pas recommandée, même si vous avez des droits. En outre, examinez toujours attentivement les implications en matière de sécurité avant d’installer de nouveaux packages dans la bibliothèque serveur.


<a name="create-iris-remotely"></a>

## <a name="5---create-test-data"></a>5-créer des données de test

Si vous disposez des autorisations nécessaires pour créer une base de données sur le serveur distant, vous pouvez exécuter le code suivant pour créer la base de données de démonstration Iris utilisée pour les étapes restantes de cet article.

### <a name="1---create-the-irissql-database-remotely"></a>1-créer la base de données irissql à distance

```python
import pyodbc

# creating a new db to load Iris sample in
new_db_name = "irissql"
connection_string = "Driver=SQL Server;Server=localhost;Database={0};Trusted_Connection=Yes;" 
                        # you can also swap Trusted_Connection for UID={your username};PWD={your password}
cnxn = pyodbc.connect(connection_string.format("master"), autocommit=True)
cnxn.cursor().execute("IF EXISTS(SELECT * FROM sys.databases WHERE [name] = '{0}') DROP DATABASE {0}".format(new_db_name))
cnxn.cursor().execute("CREATE DATABASE " + new_db_name)
cnxn.close()

print("Database created")
```

### <a name="2---import-iris-sample-from-sklearn"></a>2-importer l’exemple IRIS à partir de SkLearn

```python
from sklearn import datasets
import pandas as pd

# SkLearn has the Iris sample dataset built in to the package
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
```

### <a name="3---use-revoscalepy-apis-to-create-a-table-and-load-the-iris-data"></a>3-utiliser les API Revoscalepy pour créer une table et charger les données de l’iris

```python
from revoscalepy import RxSqlServerData, rx_data_step

# Example of using RX APIs to load data into SQL table. You can also do this with pyodbc
table_ref = RxSqlServerData(connection_string=connection_string.format(new_db_name), table="iris_data")
rx_data_step(input_data = df, output_file = table_ref, overwrite = True)

print("New Table Created: Iris")
print("Sklearn Iris sample loaded into Iris table")
```

## <a name="6---test-remote-connection"></a>6-tester la connexion à distance

Avant de passer à l’étape suivante, assurez-vous que vous disposez des autorisations sur l’instance de SQL Server et d’une chaîne de connexion à l' [exemple de base de données Iris](../tutorials/demo-data-iris-in-sql.md). Si la base de données n’existe pas et que vous disposez des autorisations suffisantes, vous pouvez [créer une base de données à l’aide de ces instructions Inline](#create-iris-remotely).

Remplacez la chaîne de connexion par des valeurs valides. L’exemple de code `"Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"` utilise, mais votre code doit spécifier un serveur distant, éventuellement avec un nom d’instance, et une option d’informations d’identification qui correspond à la connexion de l’utilisateur de la base de données.

### <a name="define-a-function"></a>Définir une fonction

Le code suivant définit une fonction que vous allez envoyer à SQL Server dans une étape ultérieure. Une fois exécuté, il utilise les données et les bibliothèques (revoscalepy, pandas, matplotlib) sur le serveur distant pour créer des nuages de points du jeu de données IRIS. Elle retourne le ByteStream du. png dans le bloc-notes Jupyter à afficher dans le navigateur.

```python
def send_this_func_to_sql():
    from revoscalepy import RxSqlServerData, rx_import
    from pandas.tools.plotting import scatter_matrix
    import matplotlib.pyplot as plt
    import io
    
    # remember the scope of the variables in this func are within our SQL Server Python Runtime
    connection_string = "Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"
    
    # specify a query and load into pandas dataframe df
    sql_query = RxSqlServerData(connection_string=connection_string, sql_query = "select * from iris_data")
    df = rx_import(sql_query)
    
    scatter_matrix(df)
    
    # return bytestream of image created by scatter_matrix
    buf = io.BytesIO()
    plt.savefig(buf, format="png")
    buf.seek(0)
    
    return buf.getvalue()
```

### <a name="send-the-function-to-sql-server"></a>Envoyer la fonction à SQL Server

Dans cet exemple, créez le contexte de calcul distant, puis envoyez l’exécution de la fonction à SQL Server avec [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec). La fonction **rx_exec** est utile, car elle accepte un contexte de calcul comme argument. Toute fonction que vous souhaitez exécuter à distance doit avoir un argument de contexte de calcul. Certaines fonctions, telles que [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) , prennent en charge cet argument directement. Pour les opérations qui ne le sont pas, vous pouvez utiliser **rx_exec** pour distribuer votre code dans un contexte de calcul distant.

Dans cet exemple, aucune donnée brute ne devait être transférée de SQL Server vers le Jupyter Notebook. Tous les calculs se produisent dans la base de données Iris et seul le fichier image est retourné au client.

```python
from IPython import display
import matplotlib.pyplot as plt 
from revoscalepy import RxInSqlServer, rx_exec

# create a remote compute context with connection to SQL Server
sql_compute_context = RxInSqlServer(connection_string=connection_string.format(new_db_name))

# use rx_exec to send the function execution to SQL Server
image = rx_exec(send_this_func_to_sql, compute_context=sql_compute_context)[0]

# only an image was returned to my jupyter client. All data remained secure and was manipulated in my db.
display.Image(data=image)
```

La capture d’écran suivante montre la sortie du nuage d’entrée et du nuage de points.

  ![bloc-notes jupyter présentant la sortie du nuage de points](media/jupyter-notebook-scatterplot.png)


<a name="install-ide"></a>

## <a name="7---start-python-from-tools"></a>7-démarrer Python à partir d’outils

Étant donné que les développeurs travaillent souvent avec plusieurs versions de Python, le programme d’installation n’ajoute pas python à votre chemin d’accès. Pour utiliser l’exécutable Python et les bibliothèques installées par le programme d’installation, liez votre IDE à **Python. exe** dans le chemin d’accès qui fournit également **revoscalepy** et **microsoftml**. 

### <a name="command-line"></a>Ligne de commande

Lorsque vous exécutez **Python. exe** à partir de C:\Program Files\Microsoft\PyForMLS (ou de l’emplacement que vous avez spécifié pour l’installation de la bibliothèque cliente Python), vous avez accès à la distribution Anaconda complète et aux modules Microsoft Python, **revoscalepy** et **microsoftml**.

1. Accédez à C:\Program Files\Microsoft\PyForMLS et double-cliquez sur **Python. exe**.
2. Ouvrir l’aide interactive:`help()`
3. Tapez le nom d’un module à l’invite d’aide `help> revoscalepy`:. L’aide retourne le nom, le contenu du package, la version et l’emplacement du fichier.
4. Retournez la version et les informations du package à l’invite `revoscalepy`de > de l' **aide** :. Appuyez sur entrée plusieurs fois pour quitter l’aide.
5. Importer un module:`import revoscalepy`


### <a name="jupyter-notebooks"></a>Blocs-notes Jupyter

Cet article utilise des blocs-notes Jupyter intégrés pour illustrer les appels de fonction à **revoscalepy**. Si vous débutez avec cet outil, la capture d’écran suivante illustre la façon dont les éclats s’imbriquent et pourquoi ils sont tout simplement opérationnels. 

Le dossier parent C:\Program Files\Microsoft\PyForMLS contient Anaconda plus les packages Microsoft. Les blocs-notes Jupyter sont inclus dans Anaconda, sous le dossier scripts, et les exécutables Python sont enregistrés automatiquement avec des blocs-notes Jupyter. Packages trouvés sous site-les packages peuvent être importés dans un bloc-notes, y compris les trois packages Microsoft utilisés pour la science des données et les Machine Learning.

  ![Exécutables et bibliothèques](media/jupyter-notebook-python-registration.png)

Si vous utilisez un autre IDE, vous devrez lier les fichiers exécutables et les bibliothèques de fonctions Python à votre outil. Les sections suivantes fournissent des instructions sur les outils couramment utilisés.

### <a name="visual-studio"></a>Visual Studio

Si vous disposez [de Python dans Visual Studio](https://code.visualstudio.com/docs/languages/python), utilisez les options de configuration suivantes pour créer un environnement Python qui comprend les packages Microsoft Python.

| Paramètre de configuration | valeur |
|-----------------------|-------|
| **Chemin du préfixe** | C:\Program Files\Microsoft\PyForMLS |
| **Chemin de l’interpréteur** | C:\Program Files\Microsoft\PyForMLS\python.exe |
| **Interpréteur avec fenêtres** | C:\Program Files\Microsoft\PyForMLS\pythonw.exe |

Pour obtenir de l’aide sur la configuration d’un environnement Python, consultez [gestion des environnements python dans Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

### <a name="pycharm"></a>PyCharm

Dans PyCharm, définissez l’interpréteur sur l’exécutable Python installé par Machine Learning Server.

1. Dans un nouveau projet, dans paramètres, cliquez sur **Ajouter un local**.

2. Entrez `C:\Program Files\Microsoft\PyForMLS\`.

Vous pouvez maintenant importer des modules **revoscalepy**, **microsoftml**ou **azureml** . Vous pouvez également choisir **Outils** > **Console python** pour ouvrir une fenêtre interactive.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous disposez d’outils et d’une connexion de travail à SQL Server, développez vos compétences en exécutant les Démarrages rapides de Python à l’aide de [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

> [!div class="nextstepaction"]
> [Démarrage rapide : Vérifier l’existence de Python dans SQL Server](../tutorials/quickstart-python-verify.md)