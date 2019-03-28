---
title: Configurer un client de science des données pour le développement Python - SQL Server Machine Learning
description: Configurer un environnement local Python (bloc-notes Jupyter ou PyCharm) pour les connexions à distance à SQL Server Machine Learning Services avec Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/09/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: c0ca592d98f9bb69586c537006fd14d4230b661b
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510686"
---
# <a name="set-up-a-data-science-client-for-python-development-on-sql-server-machine-learning-services"></a>Configurer un client de science des données pour le développement de Python sur SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Intégration de Python est disponible à partir de SQL Server 2017 ou version ultérieure, lorsque vous incluez l’option de Python dans un [installation Machine Learning Services (en base de données)](../install/sql-machine-learning-services-windows-install.md). 

Pour développer et déployer des solutions de Python pour SQL Server, installez Microsoft [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) et d’autres bibliothèques Python votre station de travail de développement. La bibliothèque revoscalepy, qui est également sur l’instance distante de SQL Server, coordonne les demandes entre les deux systèmes informatiques. 

Dans cet article, découvrez comment configurer une station de travail de développement Python afin que vous pouvez interagir avec un serveur SQL distant activé pour l’apprentissage automatique et intégration de Python. Après avoir effectué les étapes décrites dans cet article, vous devez les mêmes bibliothèques Python que celles sur SQL Server. Vous saurez également comment envoyer des calculs à partir d’une session de Python locale une session à distance Python sur SQL Server.

![Composants client-serveur](media/sqlmls-python-client-revo.png "sessions de Python locaux et distantes et les bibliothèques")

Pour valider l’installation, vous pouvez utiliser Jupyter Notebooks intégrés comme décrit dans cet article, ou [lier les bibliothèques](#install-ide) PyCharm ou n’importe quel IDE d’un autre que vous utilisez normalement.

> [!Tip]
> Pour une démonstration vidéo de ces exercices, consultez [exécuter de R et Python à distance dans SQL Server à partir des blocs-notes Jupyter](https://youtu.be/D5erljpJDjE).

> [!Note]
> Une alternative à l’installation de la bibliothèque cliente utilise un [serveur autonome](../install/sql-machine-learning-standalone-windows-install.md) comme client riche, certains clients préfèrent pour le travail de scénario plus approfondie. Un serveur autonome est entièrement dissocié de SQL Server, mais, car il possède les mêmes bibliothèques Python, vous pouvez l’utiliser en tant que client pour l’analytique en base de données de SQL Server. Vous pouvez également l’utiliser pour le travail non liés à SQL, y compris la possibilité d’importer et de modéliser des données à partir d’autres plateformes de données. Si vous installez un serveur autonome, vous pouvez trouver l’exécutable de Python à cet emplacement : `C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`. Pour valider votre installation, [ouvrez un bloc-notes Jupyter](#python-tools) pour exécuter des commandes à l’aide de la Python.exe à cet emplacement.

## <a name="commonly-used-tools"></a>Outils couramment utilisés

Si vous êtes un développeur Python SQL ou SQL développeur Python et de base de données analytique, vous devez à la fois un outil de développement Python et un éditeur de requête T-SQL comme [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) exercer tous les fonctionnalités de la base de données analytique.

Pour le développement Python, vous pouvez utiliser les blocs-notes Jupyter, qui est fourni dans la distribution Anaconda installée par SQL Server. Cet article explique comment démarrer les blocs-notes Jupyter afin que vous puissiez exécuter le code Python localement et à distance sur SQL Server.

SSMS est un téléchargement distinct, utile pour la création et exécution de procédures stockées sur SQL Server, y compris celles contenant le code Python. Presque n’importe quel code Python que vous écrivez dans les blocs-notes Jupyter peut être incorporé dans une procédure stockée. Vous pouvez parcourir d’autres guides de démarrage rapide pour en savoir plus sur [SSMS et Python incorporé](../tutorials/quickstart-python-verify.md).

## <a name="1---install-python-packages"></a>1 - installer les packages Python

Stations de travail locales doivent avoir les mêmes versions de package Python que celles sur SQL Server, y compris la base Anaconda 4.2.0 avec la distribution de Python 3.5.2 et packages spécifiques à Microsoft.

Un script d’installation ajoute les trois bibliothèques spécifiques à Microsoft pour le client Python. Le script installe [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package), utilisé pour définir des objets source de données et le contexte de calcul. Il installe [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) fournissant des algorithmes d’apprentissage automatique. Le [azureml](https://docs.microsoft.com/machine-learning-server/python-reference/azureml-model-management-sdk/azureml-model-management-sdk) package est également installé, mais il s’applique aux tâches d’Opérationnalisation associés à un contexte de Machine Learning Server autonome (non-instance) et peut être d’une utilité limitée pour la base de données analytique.

1. Télécharger un script d’installation.

  + [https://aka.ms/mls-py](https://aka.ms/mls-py) 9.2.1 d’installe les packages Python de Microsoft. Cette version correspond à une instance de SQL Server 2017 par défaut. 

  + [https://aka.ms/mls93-py](https://aka.ms/mls93-py) Installe la version 9.3 des packages Python de Microsoft. Cette version est un meilleur choix si votre instance de SQL Server 2017 à distance est [liés à Machine Learning Server 9.3](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

2. Ouvrez une fenêtre PowerShell avec des autorisations d’administrateur avec élévation de privilèges (avec le bouton droit **exécuter en tant qu’administrateur**).

3. Accédez au dossier dans lequel vous avez téléchargé le programme d’installation et exécutez le script. Ajouter le `-InstallFolder` argument de ligne de commande pour spécifier un emplacement de dossier pour les bibliothèques. Exemple : 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls"
   ```

Si vous omettez le dossier d’installation, la valeur par défaut est C:\Program Files\Microsoft\PyForMLS.

Installation prend un certain temps pour terminer. Vous pouvez surveiller la progression dans la fenêtre PowerShell. Lorsque l’installation est terminée, vous avez un ensemble complet des packages. 

> [!Tip] 
> Nous vous recommandons du [Python pour Windows FAQ](https://docs.python.org/3/faq/windows.html) pour purppose général d’informations sur l’exécution des programmes de Python sur Windows.

## <a name="2---locate-executables"></a>2 - localiser des exécutables

Toujours dans PowerShell, répertorier le contenu du dossier d’installation pour confirmer que Python.exe, scripts et autres packages sont installés. 

1. Entrez `cd \` pour aller sur le lecteur racine, puis entrez le chemin d’accès que vous avez spécifié pour `-InstallFolder` à l’étape précédente. Si vous omettez ce paramètre lors de l’installation, la valeur par défaut est `cd C:\Program Files\Microsoft\PyForMLS`.

2. Entrez `dir *.exe` pour répertorier les fichiers exécutables. Vous devriez voir **python.exe**, **pythonw.exe**, et **anaconda.exe désinstaller**.

  ![Liste des fichiers exécutables de Python](media/powershell-python-exe.png)
   
Sur les systèmes dotés de plusieurs versions de Python, pensez à utiliser cette Python.exe particulier si vous souhaitez charger **revoscalepy** et d’autres packages de Microsoft.

> [!Note] 
> Le script d’installation ne modifie pas la variable d’environnement PATH sur votre ordinateur, ce qui signifie que le nouvel interpréteur python et vous venez d’installer les modules ne sont pas automatiquement disponibles à d’autres outils que vous pouvez avoir. Pour obtenir de l’aide sur la liaison de l’interpréteur Python et les bibliothèques à outils, consultez [installer un IDE](#install-ide).

<a name="python-tools"></a>

## <a name="3---open-jupyter-notebooks"></a>3 - les blocs-notes Jupyter ouvrir

Anaconda inclut des blocs-notes Jupyter. Comme prochaine étape, créez un bloc-notes et exécuter du code Python qui contient les bibliothèques que vous venez d’installer.

1. À l’invite de Powershell, toujours dans le répertoire C:\Program Files\Microsoft\PyForMLS, ouvrez les blocs-notes Jupyter à partir du dossier de Scripts :

  ```powershell
  .\Scripts\jupyter-notebook
  ```

  Un bloc-notes doit s’ouvrir dans votre navigateur par défaut à l’adresse `https://localhost:8889/tree`.

  Une autre façon de commencer est double-cliquez sur **jupyter-notebook.exe**. 

2. Cliquez sur **New** puis cliquez sur **Python 3**.

  ![jupyter notebook avec sélection de nouveau Python 3](media/jupyter-notebook-new-p3.png)

3. Entrez `import revoscalepy` et exécutez la commande pour charger une des bibliothèques spécifiques à Microsoft.

4. Entrez et exécutez `print(revoscalepy.__version__)` pour retourner les informations de version. Vous devriez voir 9.2.1 ou 9.3.0. Vous pouvez utiliser une de ces versions avec [revoscalepy sur le serveur](../r/determine-which-packages-are-installed-on-sql-server.md#get-package-vers). 

4. Entrez une série plus complexe d’instructions. Cet exemple génère des statistiques de synthèse à l’aide [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) sur un jeu de données local. Autres fonctions Obtient l’emplacement des exemples de données et créer un objet de source de données pour un fichier .xdf local.

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

La capture d’écran suivante montre l’entrée et une partie de la sortie, ajustée par souci de concision.

  ![bloc-notes jupyter montrant la sortie et les entrées de revoscalepy](media/jupyter-notebook-local-revo.png)

## <a name="4---get-sql-permissions"></a>4 - obtenir les autorisations SQL

Pour vous connecter à une instance de SQL Server pour exécuter des scripts et charger des données, vous devez disposer d’une connexion valide sur le serveur de base de données. Vous pouvez utiliser un compte de connexion SQL ou l’authentification Windows intégrée. Nous recommandons généralement que vous utilisez l’authentification intégrée de Windows, mais à l’aide de la connexion SQL est plus simple pour certains scénarios, en particulier lorsque votre script contient les chaînes de connexion à des données externes.

Au minimum, le compte utilisé pour exécuter du code doit avoir l’autorisation de lire à partir de bases de données, vous travaillez, ainsi que l’autorisation spéciale exécuter n’importe quel SCRIPT externe. En outre, la plupart des développeurs nécessitent des autorisations pour créer des procédures stockées et d’écrire des données dans des tables contenant des données d’apprentissage ou notées des données. 

Demandez à l’administrateur de base de données [configurer les autorisations suivantes pour votre compte](../security/user-permission.md), dans la base de données dans lequel vous utilisez Python :

+ **EXECUTE ANY EXTERNAL SCRIPT** pour exécuter Python sur le serveur.
+ **db_datareader** des privilèges pour exécuter les requêtes utilisées pour l’apprentissage du modèle.
+ **db_datawriter** pour écrire des données d’apprentissage ou de données au score calculé.
+ **db_owner** pour créer des objets tels que des procédures stockées, tables, de fonctions. 
  Vous devez également **db_owner** pour créer des bases de données exemple et de test. 

Si votre code requiert les packages qui ne sont pas installés par défaut avec SQL Server, organiser avec l’administrateur de base de données pour que les packages installés avec l’instance. SQL Server est un environnement sécurisé et il existe des restrictions sur où les packages peuvent être installés. Installation ad hoc des packages dans le cadre de votre code est déconseillée, même si vous disposez des droits. En outre, toujours avec soin les implications de sécurité avant d’installer de nouveaux packages dans la bibliothèque du serveur.


<a name="create-iris-remotely"></a>

## <a name="5---create-test-data"></a>5 - créer des données de test

Si vous disposez des autorisations pour créer une base de données sur le serveur distant, vous pouvez exécuter le code suivant pour créer la base de données de démonstration Iris utilisé pour les étapes restantes de cet article.

### <a name="1---create-the-irissql-database-remotely"></a>1 - créer la base de données irissql à distance

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

### <a name="2---import-iris-sample-from-sklearn"></a>2 - importer l’exemple Iris à partir de SkLearn

```python
from sklearn import datasets
import pandas as pd

# SkLearn has the Iris sample dataset built in to the package
iris = datasets.load_iris()
df = pd.DataFrame(iris.data, columns=iris.feature_names)
```

### <a name="3---use-revoscalepy-apis-to-create-a-table-and-load-the-iris-data"></a>3 - Utilisez Revoscalepy APIs pour créer une table et charger les données Iris

```python
from revoscalepy import RxSqlServerData, rx_data_step

# Example of using RX APIs to load data into SQL table. You can also do this with pyodbc
table_ref = RxSqlServerData(connection_string=connection_string.format(new_db_name), table="iris_data")
rx_data_step(input_data = df, output_file = table_ref, overwrite = True)

print("New Table Created: Iris")
print("Sklearn Iris sample loaded into Iris table")
```

## <a name="6---test-remote-connection"></a>6 - tester la connexion à distance

Avant de réessayer cette étape, vérifiez que vous disposez des autorisations sur l’instance de SQL Server et une chaîne de connexion à la [base de données exemple Iris](../tutorials/demo-data-iris-in-sql.md). Si la base de données n’existe pas et que vous disposez des autorisations suffisantes, vous pouvez [créer une base de données à l’aide de ces instructions inline](#create-iris-remotely).

Remplacez la chaîne de connexion avec les valeurs valides. L’exemple de code utilise `"Driver=SQL Server;Server=localhost;Database=irissql;Trusted_Connection=Yes;"` mais votre code doit spécifier un serveur distant, éventuellement avec un nom d’instance et une option d’informations d’identification qui est mappé à la connexion d’utilisateur de base de données.

### <a name="define-a-function"></a>Définir une fonction

Le code suivant définit une fonction que vous enverrez à SQL Server dans une étape ultérieure. Lors de l’exécution, il utilise les bibliothèques (revoscalepy, pandas, matplotlib) et les données sur le serveur distant pour créer des nuages de points du jeu de données iris. Elle retourne le flux d’octets de la .png vers les blocs-notes Jupyter pour effectuer le rendu dans le navigateur.

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

### <a name="send-the-function-to-sql-server"></a>La fonction d’envoi vers SQL Server

Dans cet exemple, créer le contexte de calcul à distance et l’exécution de la fonction dans SQL Server avec [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec). Le **rx_exec** fonction est utile, car il accepte un contexte de calcul en tant qu’argument. N’importe quelle fonction que vous souhaitez exécuter à distance doit avoir un argument de contexte de calcul. Certaines fonctions, telles que [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) prend directement en charge cet argument. Pour les opérations qui ne le font, vous pouvez utiliser **rx_exec** à fournir votre code dans un contexte de calcul à distance.

Dans cet exemple, aucune des données brutes ne devaient être transférés à partir de SQL Server dans le bloc-notes Jupyter. Tous les calculs se produisent au sein de la base de données Iris et seul le fichier image est retourné au client.

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

La capture d’écran suivante montre la sortie de traçage d’entrée et à nuages de points.

  ![bloc-notes jupyter montrant la sortie de traçage à nuages de points](media/jupyter-notebook-scatterplot.png)


<a name="install-ide"></a>

## <a name="7---start-python-from-tools"></a>7 - démarrer Python à partir des outils

Étant donné que les développeurs travaillent souvent avec plusieurs versions de Python, le programme d’installation n’ajoute pas de Python à votre chemin d’accès. Pour utiliser le fichier exécutable Python et les bibliothèques installées par le programme d’installation, liez votre IDE pour **Python.exe** dans le chemin d’accès qui fournit également **revoscalepy** et **microsoftml**. 

### <a name="command-line"></a>Ligne de commande

Lorsque vous exécutez **Python.exe** à partir de C:\Program Files\Microsoft\PyForMLS (ou l’emplacement que vous avez spécifié pour l’installation de la bibliothèque cliente Python), vous avez accès à la distribution Anaconda complète ainsi que les Python Microsoft modules, **revoscalepy** et **microsoftml**.

1. Accédez à C:\Program Files\Microsoft\PyForMLS et double-cliquez sur **Python.exe**.
2. Ouvrir l’aide interactive : `help()`
3. Tapez le nom d’un module à l’invite de l’aide : `help> revoscalepy`. Aide retourne le nom, le contenu du package, version et emplacement du fichier.
4. Retourner des informations de version et le package à le **aide >** invite : `revoscalepy`. Appuyez sur entrée plusieurs fois pour quitter l’aide.
5. Importer un module : `import revoscalepy`


### <a name="jupyter-notebooks"></a>Blocs-notes Jupyter

Cet article utilise Jupyter Notebooks intégrés pour illustrer les appels de fonction **revoscalepy**. Si vous ne connaissez pas cet outil, la capture d’écran suivante illustre les éléments s’imbriquent et finalité de tout « ça fonctionne ». 

Le dossier parent C:\Program Files\Microsoft\PyForMLS contient Anaconda, ainsi que les packages de Microsoft. Les blocs-notes Jupyter est inclus dans Anaconda, sous le dossier Scripts, et les exécutables de Python sont enregistrés automatiquement avec les blocs-notes Jupyter. Packages qui que se trouvent sous le site-packages peuvent être importés dans un bloc-notes, y compris les trois packages Microsoft utilisés pour la science des données et l’apprentissage.

  ![Fichiers exécutables et des bibliothèques](media/jupyter-notebook-python-registration.png)

Si vous utilisez un autre IDE, vous devez lier les bibliothèques d’exécutables et de la fonction Python à votre outil. Les sections suivantes fournissent des instructions pour les outils couramment utilisés.

### <a name="visual-studio"></a>Visual Studio

Si vous avez [Python dans Visual Studio](https://code.visualstudio.com/docs/languages/python), utilisez les options de configuration suivantes pour créer un environnement Python qui inclut les packages Python de Microsoft.

| Paramètre de configuration | valeur |
|-----------------------|-------|
| **Chemin d’accès du préfixe** | C:\Program Files\Microsoft\PyForMLS |
| **Chemin d’accès de l’interpréteur** | C:\Program Files\Microsoft\PyForMLS\python.exe |
| **Interpréteur fenêtrée** | C:\Program Files\Microsoft\PyForMLS\pythonw.exe |

Pour configurer un environnement Python, consultez [gestion des environnements Python dans Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

### <a name="pycharm"></a>PyCharm

Dans PyCharm, définissez l’interpréteur Python exécutable installé par Machine Learning Server.

1. Dans un nouveau projet, dans Paramètres, cliquez sur **ajouter Local**.

2. Entrez `C:\Program Files\Microsoft\PyForMLS\`.

Vous pouvez maintenant importer **revoscalepy**, **microsoftml**, ou **azureml** modules. Vous pouvez également choisir **outils** > **Python Console** pour ouvrir une fenêtre interactive.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez les outils et une connexion active à SQL Server, développez vos compétences en exécutant via les guides de démarrage rapide de Python à l’aide [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

> [!div class="nextstepaction"]
> [Démarrage rapide : Vérifiez que Python existe dans SQL Server](../tutorials/quickstart-python-verify.md)