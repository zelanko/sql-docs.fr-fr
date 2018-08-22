---
title: Configurer les outils de client Python pour une utilisation avec SQL Server Machine Learning | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/21/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6f6823870060992586756dffa93aac6937d27d65
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "40401299"
---
# <a name="set-up-python-client-tools-for-use-with-sql-server-machine-learning"></a>Configurer Python des outils clients pour une utilisation avec SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Intégration de Python est disponible à partir de SQL Server 2017 ou version ultérieure, lorsque vous ajoutez la que prise en charge de Python pour Machine Learning Services (en base de données). Pour plus d’informations, consultez [installer SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md).

Dans cet article, découvrez comment configurer des stations de travail de développement afin que vous pouvez vous connecter à un serveur SQL distant activé pour Python.

### <a name="evaluation-and-independent-development"></a>Évaluation et développement indépendant
 
Si vous avez l’édition développeur et le plan pour travailler localement sur le script Python que vous voulez déplacer vers SQL Server, vous pouvez passer directement à [installer un IDE](#install-ide) et pointez l’outil sur les bibliothèques Python locales utilisés par SQL Server.

> [!Tip]
> Pour une démonstration et une procédure pas à pas vidéo, consultez [exécuter de R et Python à distance dans SQL Server à partir de Jupyter Notebooks ou n’importe quel IDE](https://blogs.msdn.microsoft.com/mlserver/2018/07/10/run-r-and-python-remotely-in-sql-server-from-jupyter-notebooks-or-any-ide/) ou cela [vidéo YouTube](https://youtu.be/D5erljpJDjE).

## <a name="1---install-python-packages"></a>1 - installer les packages Python

Stations de travail locales doivent avoir les mêmes versions de package Python que celles sur SQL Server : revoscalepy et microsftml. Les packages Python supplémentaires sont disponibles, mais sont plus fréquemment utilisées avec les autres scénarios dans un contexte de Machine Learning Server autonome (non-instance). 

1. Télécharger le script de shell d’installation à partir de [ https://aka.ms/mls93-py ](https://aka.ms/mls93-py) (ou utilisez [ https://aka.ms/mls-py ](https://aka.ms/mls-py) pour le 9.2. mise en production). Le script installe Anaconda 4.2.0, qui inclut Python 3.5.2, ainsi que tous les packages répertoriés précédemment.

  Composants de Python sont fournis via [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054&clcid=1033). Si vous avez besoin d’une version différente, consultez [CAB téléchargements](../install/sql-ml-cab-downloads.md)

2. Ouvrez la fenêtre PowerShell avec des autorisations d’administrateur avec élévation de privilèges (avec le bouton droit **exécuter en tant qu’administrateur**).

3. Accédez au dossier dans lequel vous avez téléchargé le programme d’installation et exécutez le script. Ajouter le `-InstallFolder` argument de ligne de commande pour spécifier un emplacement de dossier pour les bibliothèques. Exemple : 

   ```python
   cd {{download-directory}}
   .\Install-PyForMLS.ps1 -InstallFolder "C:\path-to-python-for-mls")
   ```

   Installation prend un certain temps pour terminer. Vous pouvez surveiller la progression dans la fenêtre PowerShell. Lorsque l’installation est terminée, vous avez un ensemble complet des packages. Par exemple, si vous avez spécifié `C:\mspythonlibs` comme nom de dossier, vous trouverez les packages à `C:\mspythonlibs\Lib\site-packages`. Sinon, le dossier par défaut est `C:\Program Files\Microsoft\PyForMLS1`.

Le script d’installation ne modifie pas la variable d’environnement PATH sur votre ordinateur afin du nouvel interpréteur python et vous venez d’installer les modules ne sont pas automatiquement disponibles pour vos outils. Pour obtenir de l’aide sur la liaison de l’interpréteur Python et les bibliothèques à outils, consultez [5 - installer un IDE](#install-ide).

<a name="python-tool"></a>
 
## <a name="2---open-a-python-prompt"></a>2 - ouvrez une invite de Python

Intégration de Python dans Microsoft inclut des outils intégrés et les données en plus les bibliothèques spécifiques au produit comme revoscalepy et microsoftml. Les éléments suivants sont disponibles sur les instances de client et serveur lorsque le programme d’installation est terminée :

+ Exemples de données Python
+ Distribution anaconda 4.2 
+ Pythonw.exe et Python exécutables python.exe

> [!Tip] 
> Nous vous recommandons du [Python pour Windows FAQ](https://docs.python.org/3/faq/windows.html) pour purppose général d’informations sur l’exécution des programmes de Python sur Windows.

### <a name="on-client-workstations"></a>Sur les stations de travail clientes

Pour utiliser l’exécutable Python installé par le script d’installation :

1. Accédez à `C:\Program Files\Microsoft\PyForMLS\python.exe` ou l’emplacement que vous avez choisi pour le chemin d’installation.

2. Avec le bouton droit **Python.exe** et sélectionnez **exécuter en tant qu’administrateur** pour ouvrir une fenêtre de ligne de commande interactive.

### <a name="on-sql-server"></a>Sur SQL Server

Le programme d’installation de SQL Server ajoute des outils Python standards et ressources à une instance de serveur. Si vous utilisez l’édition développeur et que vous souhaitez vérifier la version de Python ou exécuter des commandes ad hoc :

1. Accédez à `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`.

2. Avec le bouton droit **Python.exe** et sélectionnez **exécuter en tant qu’administrateur** pour ouvrir une fenêtre de ligne de commande interactive.

> [!Note]
> En règle générale, pour éviter les conflits de ressources, nous recommandons que vous **ne le faites pas** exécuter Python à partir de la bibliothèque de l’instance sur le serveur, si vous pensez qu’il est possible l’instance SQL Server est en cours d’exécution de code Python. Toutefois, l’utilisation des outils dans la bibliothèque de l’instance peut être utile si vous tentez de déboguer un problème qui se produit uniquement lors de l’exécution dans SQL Server et à afficher des messages d’erreur plus détaillés, ou assurez-vous que tous les packages requis sont installés.

## <a name="3---permissions"></a>3 - autorisations

Pour vous connecter à une instance de SQL Server pour exécuter des scripts et charger des données, vous devez disposer d’une connexion valide sur le serveur de base de données. Vous pouvez utiliser un compte de connexion SQL ou l’authentification Windows intégrée. Nous recommandons généralement que vous utilisez l’authentification intégrée de Windows, mais à l’aide de la connexion SQL est plus simple pour certains scénarios.

Au minimum, le compte utilisé pour exécuter du code doit avoir l’autorisation de lire à partir de bases de données, vous travaillez, ainsi que l’autorisation spéciale exécuter n’importe quel SCRIPT externe. La plupart des développeurs également nécessitent des autorisations pour créer des objets sous la forme de procédures stockées contenant votre script et écrire des données dans des tables contenant des données d’apprentissage ou un score de données. 

Demandez à l’administrateur de base de données pour configurer les autorisations suivantes pour le compte, dans la base de données dans lequel vous utilisez Python :

+ **EXECUTE ANY EXTERNAL SCRIPT** pour exécuter Python sur le serveur.
+ **db_datareader** des privilèges pour exécuter les requêtes utilisées pour l’apprentissage du modèle.
+ **db_datawriter** pour écrire des données d’apprentissage ou de données au score calculé.
+ **db_owner** pour créer des objets tels que des procédures stockées, tables, de fonctions. 
  Vous devez également **db_owner** pour créer des bases de données exemple et de test. 

Si votre code requiert les packages qui ne sont pas installés par défaut avec SQL Server, organiser avec l’administrateur de base de données pour que les packages installés avec l’instance. SQL Server est un environnement sécurisé et il existe des restrictions sur où les packages peuvent être installés. Installation ad hoc des packages dans le cadre de votre code est déconseillée, même si vous disposez des droits. En outre, toujours avec soin les implications de sécurité avant d’installer de nouveaux packages dans la bibliothèque du serveur.

## <a name="4---test-connections"></a>4 - tester les connexions

Après avoir installé tous les outils et bibliothèques, vous devez vous connecter au serveur et vérifiez que vous pouvez créer un contexte de calcul, ou que Python peut communiquer avec SQL Server.

### <a name="verify-that-revoscalepy-works-from-the-python-command-line"></a>Vérifiez que revoscalepy fonctionne à partir de la ligne de commande Python

Pour vérifier que le **revoscalepy** module peut être chargé, exécutez l’exemple de code suivant à partir d’une invite de commandes interactive Python. Le code génère un résumé des données à l’aide de l’exemple de données Python et [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary). 

```Python
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

Le chemin d’accès de données exemple est imprimé afin que vous puissiez déterminer quelle instance de Python est appelée.

### <a name="verify-that-python-can-be-called-from-a-local-sql-server"></a>Vérifiez que Python peut être appelée à partir d’un serveur SQL local

Dans un environnement de développement local, vérifiez que Python communique avec local [instance SQL Server configurée pour le script externe](../install/sql-machine-learning-services-windows-install.md). Utiliser SQL Server Management Studio pour ouvrir une nouvelle **requête** fenêtre et les exécuter n’importe quel Python simple des commandes dans le contexte d’une procédure stockée :

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'print(3+4)'
```

Il peut prendre un certain temps pour lancer le runtime Python pour la première fois, mais s’il n’existe aucune erreur, vous savez que l’utilisation de SQL Server Launchpad et Python peut être démarré à partir de SQL Server.

Pour vérifier que **revoscalepy** est disponible dans la bibliothèque d’instance de SQL Server, exécutez le script selon [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary), avec de légères modifications pour générer des résultats compatible avec SQL Server. 

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'
import os
from pandas import DataFrame
from revoscalepy import rx_summary
from revoscalepy import RxXdfData
from revoscalepy import RxOptions

sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay + DayOfWeek", ds)
print(summary)
dfsummary = summary.summary_data_frame
OutputDataSet = dfsummary
'
WITH RESULT SETS  ((ColName nvarchar(25) , ColMean float, ColStdDev  float, ColMin  float,   ColMax  float, Col_ValidObs  float, Col_MissingObs int))
```

Étant donné que rx_summary retourne un objet de type `class revoscalepy.functions.RxSummary.RxSummaryResults`, qui contient plusieurs éléments, à gérer les résultats dans SQL Server, vous pouvez extraire uniquement la trame de données dans un format tabulaire.

### <a name="verify-python-execution-in-sql-server-as-remote-compute-context"></a>Vérifier l’exécution de Python dans SQL Server comme contexte de calcul à distance

Si vous avez installé **revoscalepy** dans votre environnement de développement Python local, vous devez être en mesure de se connecter à une instance distante de SQL Server 2017 où Python a été activé et exécuter un exemple de code similaire à l’aide du serveur en tant que le contexte de calcul. 

Pour ce script s’exécute, spécifiez un nom de serveur valide et une base de données existante. Ce script particulier n’utilise pas la base de données, mais la chaîne de connexion l’exige.

```Python
import os
from revoscalepy import rx_summary, RxOptions, RxXdfData, RxSqlServerData, RxInSqlServer

# define connection string and compute context
sql_conn_string="Driver=SQL Server;Server=<server-name>;Database=TestDB;Trusted_Connection=True"
sqlcc = RxInSqlServer(
    connection_string = sql_conn_string,
    num_tasks = 1,
    auto_cleanup = False,
    console_output = True,
    execution_timeout_seconds = 0,
    wait = True
    )
rx_set_compute_context(sqlcc)

# get sample data and path
sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

# generate summary
ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay+DayOfWeek", ds)
print(summary)
```

Dans cet exemple, l’objet de synthèse est retourné à la console, plutôt que des données tabulaires bien formées retour à SQL Server. 

En outre, étant donné que [rx_set_compute_context](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-set-compute-context) a été appelé, les exemples de données sont chargés à partir du dossier d’exemples sur l’ordinateur SQL Server et non à partir de votre dossier d’exemples local.


<a name="install-ide"></a>

## <a name="5---install-an-ide"></a>5 - installer un IDE

Si vous déboguez simplement des scripts à partir de la ligne de commande, vous pouvez obtenir en avec les outils Python standards. Toutefois, si vous développez de nouvelles solutions, ou travailler à partir d’un client distant, nous vous recommandons d’utiliser un IDE Python complet. Les options les plus courants sont :

+ [Visual Studio 2017 Community Edition](https://www.visualstudio.com/vs/features/python/) avec Python
+ [Visual Studio tools pour IA](https://docs.microsoft.com/visualstudio/ai/installation)
+ [Python dans Visual Studio Code](https://code.visualstudio.com/docs/languages/python)
+ Outils tiers populaires tels que PyCharm, Spyder et Eclipse

Nous vous recommandons de Visual Studio, car il prend en charge les projets de base de données, ainsi que des projets machine learning. Pour configurer un environnement Python, consultez [gestion des environnements Python dans Visual Studio](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio).

Étant donné que les développeurs travaillent souvent avec plusieurs versions de Python, le programme d’installation n’ajoute pas de Python à votre chemin d’accès. Pour utiliser le fichier exécutable Python et les bibliothèques installées par le programme d’installation, liez votre IDE pour **Python.exe** dans le chemin d’accès qui fournit également revoscalepy et microsoftml. Par exemple, votre environnement personnalisé pour un projet Python dans Visual Studio, spécifiez `C:\Program Files\Microsoft\PyForMLS`, `C:\Program Files\Microsoft\PyForMLS\python.exe` et `C:\Program Files\Microsoft\PyForMLS\pythonw.exe` pour **chemin du préfixe**, **interpretu**et  **Interpréteur fenêtrée**, respectivement.

Pour plus d’informations, consultez [lien Python tools et différents IDE](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). L’article est écrit pour Microsoft Machine Learning Server afin que les chemins d’accès de Python sont différents, mais il vous montre comment lier des bibliothèques de Python à partir de différents outils.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez les outils et une connexion active à SQL Server, suivez un didacticiel pour obtenir une présentation détaillée des fonctions de revoscalepy et le basculement des contextes de calcul.

> [!div class="nextstepaction"]
> [Créer un modèle à l’aide de revoscalepy et un contexte de calcul à distance](../tutorials/use-python-revoscalepy-to-create-model.md)