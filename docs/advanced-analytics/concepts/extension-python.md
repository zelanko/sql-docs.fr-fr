---
title: Extension du langage de programmation python
description: En savoir plus sur l’exécution de code Python et les bibliothèques python intégrées dans SQL Server Machine Learning Services 2017.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: f85392f8bfbb7ee89b8387b0f7d27038b9a8303b
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470465"
---
# <a name="python-language-extension-in-sql-server"></a>Extension de langage Python dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L’extension Python fait partie du module complémentaire SQL Server Machine Learning Services au moteur de base de données relationnelle. Il ajoute un environnement d’exécution Python, une distribution Anaconda avec le runtime et l’interpréteur python 3,5, des bibliothèques et des outils standard et les bibliothèques de produits Microsoft pour Python: [revoscalepy](../python/ref-py-revoscalepy.md) pour l’analyse à l’échelle et [microsoftml](../python/ref-py-microsoftml.md) pour Machine Learning des algorithmes. 

L’intégration Python est installée en tant que [SQL Server machine learning services](../what-is-sql-server-machine-learning.md).

L’installation du runtime et de l’interpréteur python 3,5 garantit une compatibilité quasi complète avec les solutions python standard. Python s’exécute dans un processus distinct de SQL Server, pour garantir que les opérations de base de données ne sont pas compromises.

## <a name="python-components"></a>Composants python

SQL Server comprend à la fois des packages Open source et propriétaires. Le runtime python installé par le programme d’installation est Anaconda 4,2 avec Python 3,5. Le runtime Python est installé indépendamment des outils SQL et est exécuté en dehors des processus du moteur de base, dans l’infrastructure d’extensibilité. Dans le cadre de l’installation de Machine Learning Services avec Python, vous devez accepter les termes de la licence publique GNU. 

SQL Server ne modifie pas les exécutables Python, mais vous devez utiliser la version de Python installée par le programme d’installation, car cette version est celle sur laquelle les packages propriétaires sont créés et testés. Pour obtenir la liste des packages pris en charge par la distribution Anaconda, consultez le site d’analyse continuum: [Liste des packages Anaconda](https://docs.continuum.io/anaconda/packages/pkg-docs).

La distribution Anaconda associée à une instance de moteur de base de données spécifique se trouve dans le dossier associé à l’instance. Par exemple, si vous avez installé le moteur de base de données SQL Server 2017 avec Machine Learning Services et Python sur l' `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`instance par défaut, Regardez sous.

Les packages python ajoutés par Microsoft pour les charges de travail distribuées et parallèles incluent les bibliothèques suivantes.

| Bibliothèque | Description |
|---------|-------------|
| [**revoscalepy**](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Prend en charge les objets de source de données et l’exploration, la manipulation, la transformation et la visualisation des données. Il prend en charge la création de contextes de calcul distants, ainsi qu’un certain nombre de modèles de Machine Learning évolutifs, tels que **rxLinMod**. Pour plus d’informations, consultez [module revoscalepy avec SQL Server](../python/ref-py-revoscalepy.md).  |
| [**microsoftml**](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Contient des algorithmes de Machine Learning qui ont été optimisés pour la vitesse et la précision, ainsi que des transformations en ligne pour l’utilisation de texte et d’images. Pour plus d’informations, consultez [module microsoftml avec SQL Server](../python/ref-py-microsoftml.md). |

Microsoftml et revoscalepy sont étroitement couplés; les sources de données utilisées dans microsoftml sont définies en tant qu’objets revoscalepy. Limites de contexte de calcul dans revoscalepy Transfer to microsoftml. À savoir, toutes les fonctionnalités sont disponibles pour les opérations locales, mais le passage à un contexte de calcul distant requiert RxInSqlServer.

## <a name="using-python-in-sql-server"></a>Utilisation de Python dans SQL Server

Vous importez le module **revoscalepy** dans votre code Python, puis vous appelez des fonctions à partir du module, comme n’importe quelle autre fonction Python.

Les sources de données prises en charge incluent les bases de données ODBC, les SQL Server et le format de fichier XDF pour échanger des données avec d’autres sources, ou avec des solutions R. Les données d’entrée pour Python doivent être tabulaires. Tous les résultats de Python doivent être retournés sous  la forme d’une trame de données pandas.

Les contextes de calcul pris en charge incluent un contexte de calcul local ou distant SQL Server. Un contexte de calcul distant fait référence à l’exécution de code qui démarre sur un ordinateur, tel qu’une station de travail, mais bascule l’exécution du script sur un ordinateur distant. Le basculement du contexte de calcul nécessite que les deux systèmes aient la même bibliothèque revoscalepy.

Le contexte de calcul local, comme vous pouvez vous y attendre, comprend l’exécution de code Python sur le même serveur que l’instance du moteur de base de données, avec le code à l’intérieur de T-SQL ou incorporé dans une procédure stockée. Vous pouvez également exécuter le code à partir d’un IDE python local et faire en sorte que le script s’exécute sur l’ordinateur SQL Server, en définissant un contexte de calcul distant.

## <a name="execution-architecture"></a>Architecture d’exécution

Les diagrammes suivants décrivent l’interaction des composants SQL Server avec le runtime python dans chacun des scénarios pris en charge: l’exécution d’un script dans la base de données et l’exécution à distance à partir d’un terminal Python, à l’aide d’un contexte de calcul SQL Server.

### <a name="python-scripts-executed-in-database"></a>Scripts Python exécutés dans la base de données

Lorsque vous exécutez l’SQL Server à l’intérieur de Python, vous devez encapsuler le script Python à l’intérieur d’une procédure stockée spéciale, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Une fois le script incorporé dans la procédure stockée, toute application pouvant effectuer un appel de procédure stockée peut lancer l’exécution du code Python.  Ensuite SQL Server gère l’exécution du code comme décrit dans le diagramme suivant.

![script-in-db-python](../../advanced-analytics/python/media/script-in-db-python2.png)

1. Une demande pour le runtime Python est indiquée par le paramètre `@language='Python'` passé à la procédure stockée. SQL Server envoie cette demande au service launchpad.
2. Le service Launchpad démarre le lanceur approprié; dans ce cas, PythonLauncher.
3. PythonLauncher démarre le processus Python35 externe.
4. BxlServer coordonnées avec le runtime Python pour gérer les échanges de données et le stockage des résultats de travail.
5. SQL satellite gère les communications sur les tâches et les processus connexes avec SQL Server.
6. BxlServer utilise SQL satellite pour communiquer l’État et les résultats à SQL Server.
7. SQL Server obtient les résultats et ferme les tâches et processus associés.

### <a name="python-scripts-executed-from-a-remote-client"></a>Scripts Python exécutés à partir d’un client distant

Vous pouvez exécuter des scripts Python à partir d’un ordinateur distant, tel qu’un ordinateur portable, et les faire exécuter dans le contexte de l’ordinateur SQl Server, si les conditions suivantes sont remplies:

+ Vous concevez les scripts de manière appropriée
+ L’ordinateur distant a installé les bibliothèques d’extensibilité utilisées par Machine Learning Services. Le package [revoscalepy](../python/ref-py-revoscalepy.md) est requis pour utiliser des contextes de calcul distants.

Le diagramme suivant résume le flux de travail global lorsque les scripts sont envoyés à partir d’un ordinateur distant.

![remote-sqlcc-from-python](../../advanced-analytics/python/media/remote-sqlcc-from-python3.png)

1. Pour les fonctions prises en charge dans **revoscalepy**, le runtime python appelle une fonction de liaison, qui à son tour appelle BxlServer.
2. BxlServer est inclus avec Machine Learning Services (dans la base de données) et s’exécute dans un processus distinct du runtime Python.
3. BxlServer détermine la cible de la connexion et établit une connexion à l’aide d’ODBC, en transmettant les informations d’identification fournies dans le cadre de la chaîne de connexion dans le script Python.
4. BxlServer ouvre une connexion à l’instance SQL Server.
5. Lorsqu’un Runtime de script externe est appelé, le service Launchpad est appelé, qui à son tour démarre le lanceur approprié: dans le cas présent, PythonLauncher. dll. Par la suite, le traitement du code Python est géré dans un flux de travail similaire à celui où le code Python est appelé à partir d’une procédure stockée dans T-SQL.
6. PythonLauncher effectue un appel à l’instance de Python qui est installée sur l’ordinateur SQL Server.
7. Les résultats sont retournés à BxlServer.
8. SQL satellite gère la communication avec SQL Server et le nettoyage des objets de traitement associés.
9. SQL Server renvoie les résultats au client.

## <a name="see-also"></a>Voir aussi

+ [module revoscalepy dans SQL Server](../python/ref-py-revoscalepy.md)
+ [Référence des fonctions revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) 
+ [Infrastructure d’extensibilité dans SQL Server](extensibility-framework.md)
+ [Extensions R et Machine Learning dans SQL Server](extension-r.md)