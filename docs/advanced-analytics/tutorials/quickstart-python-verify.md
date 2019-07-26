---
title: Démarrage rapide pour vérifier l’existence de Python dans SQL Server
description: Démarrage rapide pour vérifier que Python et Machine Learning Services existent dans SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0dd5714f47c90c0091daacbd792b80c05ec68675
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469701"
---
# <a name="quickstart-verify-python-exists-in-sql-server"></a>Démarrage rapide : Vérifier que Python existe dans SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server prend en charge le langage Python pour l’analyse de la science des données sur les données résidentes SQL Server. L’exécution du script s’effectue via des procédures stockées, à l’aide de l’une des approches suivantes:

+ Procédure stockée [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) intégrée, transmettant le script Python dans en tant que paramètre d’entrée.
+ Encapsulez le script Python dans une [procédure stockée personnalisée](sqldev-in-database-r-for-sql-developers.md) que vous créez.

Dans ce guide de démarrage rapide, vous allez vérifier que [SQL Server 2017 machine learning services](../what-is-sql-server-machine-learning.md) est installé et configuré.

## <a name="prerequisites"></a>Prérequis

Cet exercice requiert l’accès à une instance de SQL Server avec [SQL Server 2017 machine learning services](../install/sql-machine-learning-services-windows-install.md) installée.

Votre instance de SQL Server peut se trouver dans une machine virtuelle Azure ou en local. N’oubliez pas que la fonctionnalité de script externe est désactivée par défaut. par conséquent, vous devrez peut-être [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifier que **SQL Server Launchpad service** est en cours d’exécution avant de commencer.

Vous avez également besoin d’un outil pour exécuter des requêtes SQL. Vous pouvez exécuter les scripts Python à l’aide de n’importe quel outil de gestion de base de données ou de requête, à condition qu’il puisse se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce guide de démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="verify-python-exists"></a>Vérifier l’existence de Python

Vous pouvez vérifier que Machine Learning Services (est activé pour votre instance SQL Server et quelle version de Python est installée. Suivez les étapes ci-dessous.

1. Ouvrez SQL Server Management Studio et connectez-vous à votre instance SQL Server.

2. Exécutez le code ci-dessous. 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import sys
    print(sys.version)';
    GO
    ```

3. La fonction `print` python retourne la version dans la fenêtre **messages** . Dans l’exemple de sortie ci-dessous, vous pouvez voir que SQL Server dans ce cas, Python version 3.5.2 est installé.

    **Résultats**

    ```text
    STDOUT message(s) from external script: 
    3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
    ```

Si vous recevez des erreurs, vous pouvez effectuer diverses opérations pour vous assurer que l’instance et Python peuvent communiquer.

Tout d’abord, éliminez les problèmes d’installation. La configuration après installation est requise pour permettre l’utilisation de bibliothèques de code externes. Voir [Install SQL Server 2017 machine learning services](../install/sql-machine-learning-services-windows-install.md). De même, assurez-vous que le service Launchpad est en cours d’exécution.

Vous devez également ajouter le groupe `SQLRUserGroup` d’utilisateurs Windows en tant que connexion sur l’instance, pour vous assurer que Launchpad peut fournir la communication entre Python et SQL Server. (Le même groupe est utilisé pour l’exécution de code R et Python.) Pour plus d’informations, consultez [créer une connexion pour SQLRUserGroup](../security/create-a-login-for-sqlrusergroup.md).

En outre, vous devrez peut-être activer les protocoles réseau qui ont été désactivés ou ouvrir le pare-feu afin que les SQL Server puissent communiquer avec les clients externes. Pour plus d’informations, consultez [résolution des problèmes d’installation](../common-issues-external-script-execution.md).

## <a name="call-revoscalepy-functions"></a>Appeler des fonctions revoscalepy

Pour vérifier que **revoscalepy** est disponible, exécutez un exemple de script qui comprend [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) qui produit des données de synthèse statistiques. Le script ci-dessous montre comment récupérer un exemple de fichier de données. XDF à partir d’exemples intégrés inclus dans revoscalepy. La fonction RxOptions fournit le paramètre **sampleDataDir** qui retourne l’emplacement des fichiers d’exemple.

Comme rx_summary retourne un objet de type `class revoscalepy.functions.RxSummary.RxSummaryResults`, qui contient plusieurs éléments, vous pouvez utiliser pandas pour extraire uniquement la trame de données dans un format tabulaire.

```sql
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

## <a name="list-python-packages"></a>Répertorier les packages python

Microsoft fournit un certain nombre de packages python préinstallés avec Machine Learning Services dans votre instance SQL Server. Pour afficher la liste des packages python installés, y compris la version, suivez les étapes ci-dessous.

1. Exécutez le script ci-dessous sur votre instance SQL Server.

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import pip
    for i in pip.get_installed_distributions():
        print(i)';
    GO
    ```

2. La sortie provient `pip.get_installed_distributions()` de dans Python et est renvoyée en tant que `STDOUT` messages.

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
    testpath 0.3
    tables 3.2.2
    sympy 1.0
    statsmodels 0.8.0
    sqlparse 0.1.19
    SQLAlchemy 1.1.9
    snowballstemmer 1.2.1
    six 1.10.0
    simplegeneric 0.8.1
    seaborn 0.7.1
    scipy 0.19.0
    scikit-learn 0.18.1
    ...
    ```

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez confirmé que votre instance est prête à fonctionner avec Python, examinez plus en détail une interaction python de base.

> [!div class="nextstepaction"]
> [Démarrage rapide : Script Python «Hello World» dans SQL Server](quickstart-python-run-using-t-sql.md)
