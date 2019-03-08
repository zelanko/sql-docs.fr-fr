---
title: Guide de démarrage rapide pour la vérification de Python existe dans SQL Server
description: Guide de démarrage rapide pour vérifier que Python et Machine Learning Services existent dans SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 25bf5a7e7d18810c782d1ce2f4986fc433421395
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2019
ms.locfileid: "57577929"
---
# <a name="quickstart-verify-python-exists-in-sql-server"></a>Démarrage rapide : Vérifier que Python existe dans SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server inclut la prise en charge du langage Python pour l’analytique de science des données sur les données de SQL Server résidentes. L’exécution du script est via des procédures stockées, à l’aide d’une des approches suivantes :

+ Intégrés [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) procédure stockée, en passant dans le script Python comme paramètre d’entrée.
+ Encapsuler le script Python dans un [procédure stockée personnalisée](sqldev-in-database-r-for-sql-developers.md) que vous créez.

Dans ce démarrage rapide, vous allez vérifier que [SQL Server 2017 Machine Learning Services](../what-is-sql-server-machine-learning.md) est installé et configuré.

## <a name="prerequisites"></a>Prérequis

Cet exercice requiert l’accès à une instance de SQL Server avec [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) installé.

Votre instance SQL Server peut être dans une machine virtuelle Azure ou en local. Soyez conscient que la fonctionnalité de script externe est désactivée par défaut, vous devrez donc peut-être à [activer les scripts externes](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) et vérifiez que **service SQL Server Launchpad** est en cours d’exécution avant de commencer.

Vous devez également un outil pour l’exécution de requêtes SQL. Vous pouvez exécuter les scripts Python à l’aide d’une gestion de base de données ou interroger l’outil, tant qu’il peut se connecter à une instance de SQL Server et exécuter une requête T-SQL ou une procédure stockée. Ce démarrage rapide utilise [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="verify-python-exists"></a>Vérifiez que Python existe

Vous pouvez vérifier cette Machine Learning Services (est activée pour votre instance de SQL Server et la version de Python est installée. Suivez les étapes ci-dessous.

1. Ouvrez SQL Server Management Studio et connectez-vous à votre instance de SQL Server.

2. Exécutez le code ci-dessous. 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import sys
    print(sys.version)';
    GO
    ```

3. Python `print` fonction retourne la version à la **Messages** fenêtre. Dans l’exemple ci-dessous, vous pouvez voir que SQL Server a dans ce cas Python version 3.5.2 installé.

    **Résultats**

    ```text
    STDOUT message(s) from external script: 
    3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
    ```

Si vous obtenez des erreurs, il existe une variété de choses à que faire pour vous assurer que l’instance et Python peut communiquer.

Tout d’abord, éliminer tout problème d’installation. Configuration de post-installation est nécessaire pour permettre l’utilisation des bibliothèques de code externe. Consultez [installer SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md). De même, assurez-vous que le service Launchpad est en cours d’exécution.

Vous devez également ajouter le groupe d’utilisateurs Windows `SQLRUserGroup` en tant que connexion sur l’instance, pour vous assurer que Launchpad peut assurer la communication entre Python et SQL Server. (Le même groupe est utilisé pour les deux R et l’exécution de code Python.) Pour plus d’informations, consultez [l’authentification implicite activé](../security/add-sqlrusergroup-to-database.md).

En outre, vous devrez peut-être activer les protocoles réseau qui ont été désactivées, ou ouvrir le pare-feu pour que SQL Server peut communiquer avec des clients externes. Pour plus d’informations, consultez [dépannage de l’installation](../common-issues-external-script-execution.md).

## <a name="call-revoscalepy-functions"></a>Appeler des fonctions de revoscalepy

Pour vérifier que **revoscalepy** est disponible, exécutez un exemple de script qui inclut [rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary) qui produit des données de résumé statistiques. Le script ci-dessous montre comment récupérer un exemple de fichier de données .xdf à partir d’exemples intégrés inclus dans revoscalepy. La fonction RxOptions fournit le **sampleDataDir** paramètre qui retourne l’emplacement des exemples de fichiers.

Étant donné que rx_summary retourne un objet de type `class revoscalepy.functions.RxSummary.RxSummaryResults`, qui contient plusieurs éléments, vous pouvez utiliser pandas pour extraire uniquement la trame de données dans un format tabulaire.

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

## <a name="list-python-packages"></a>Répertorier les packages Python

Microsoft fournit un nombre de packages Python préinstallés avec Machine Learning Services dans votre instance de SQL Server. Pour afficher une liste de quelle solution Python packages installés, y compris la version, suivez les étapes ci-dessous.

1. Exécutez le script ci-dessous sur votre instance de SQL Server.

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'Python',
    @script=N'import pip
    for i in pip.get_installed_distributions():
        print(i)';
    GO
    ```

2. La sortie est à partir de `pip.get_installed_distributions()` dans Python et retournés en tant que `STDOUT` messages.

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

Maintenant que vous avez confirmé que votre instance est prête à fonctionner avec Python, examinons plus en détail une interaction Python de base.

> [!div class="nextstepaction"]
> [Démarrage rapide : Script Python « Hello world » dans SQL Server](quickstart-python-run-using-t-sql.md)
