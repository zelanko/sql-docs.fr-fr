---
title: SQL Server Machine Learning - extension du langage de programmation Python
description: En savoir plus sur l’exécution de code Python et les bibliothèques Python intégrées dans SQL Server 2017 Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: c0284577d8e30871b354607cf9af978e6d53df63
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58512216"
---
# <a name="python-language-extension-in-sql-server"></a>Extension de langage Python dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L’extension Python fait partie du module complémentaire de SQL Server Machine Learning Services au moteur de base de données relationnelle. Il ajoute un environnement d’exécution de Python, distribution Anaconda avec le runtime Python 3.5 et interpréteur, bibliothèques standard et les outils et les bibliothèques de produit Microsoft pour Python : [revoscalepy](../python/ref-py-revoscalepy.md) pour analytique à échelle et [microsoftml](../python/ref-py-microsoftml.md) pour les algorithmes d’apprentissage automatique. 

Intégration de Python est installée en tant que [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md).

Installation du runtime Python 3.5 et interpréteur garantit une compatibilité avec les solutions Python standards. Python s’exécute dans un processus séparé à partir de SQL Server, afin de garantir que les opérations de base de données ne sont pas compromises.

## <a name="python-components"></a>Composants de Python

SQL Server inclut les packages open source et propriétaires. Le runtime Python installé par le programme d’installation est 4.2 Anaconda Python 3.5. Le runtime Python est installé indépendamment des outils SQL et il est exécuté en dehors du processus de moteur de base, dans l’infrastructure d’extensibilité. Dans le cadre de l’installation des Services Machine Learning avec Python, vous devez accepter les termes du contrat de la licence publique GNU. 

SQL Server ne modifie pas les exécutables de Python, mais vous devez utiliser la version de Python installées par le programme d’installation, car cette version est celle que les packages propriétaires sont conçus et testés sur. Pour obtenir la liste des packages pris en charge par la distribution Anaconda, consultez le site d’analytique Continuum : [Liste des packages anaconda](https://docs.continuum.io/anaconda/packages/pkg-docs).

Vous trouverez la distribution Anaconda associée à une instance du moteur de base de données spécifique dans le dossier associé à l’instance. Par exemple, si vous avez installé le moteur de base de données SQL Server 2017 avec les Services Machine Learning et Python sur l’instance par défaut, regardez sous `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`.

Les packages Python ajoutés par Microsoft pour les charges de travail parallèles et distribuées incluent les bibliothèques suivantes.

| Bibliothèque | Description |
|---------|-------------|
| [**revoscalepy**](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Prend en charge les objets source de données et de l’exploration de données, de manipulation, de transformation et de visualisation. Il prend en charge la création de contextes de calcul distants, mais aussi un différents évolutive modèles d’apprentissage automatique, tel que **rxLinMod**. Pour plus d’informations, consultez [module revoscalepy avec SQL Server](../python/ref-py-revoscalepy.md).  |
| [**microsoftml**](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Contient des algorithmes d’apprentissage automatique qui ont été optimisés pour la vitesse et la précision, ainsient que les transformations pour travailler avec le texte et des images en ligne. Pour plus d’informations, consultez [module microsoftml avec SQL Server](../python/ref-py-microsoftml.md). |

Microsoftml et revoscalepy sont étroitement couplés ; sources de données utilisées dans microsoftml sont définies en tant qu’objets de revoscalepy. Limitations de contexte dans le transfert de revoscalepy de microsoftml de calcul. À savoir, toutes les fonctionnalités sont disponibles pour les opérations locales, mais basculer vers un contexte de calcul à distance requiert RxInSqlServer.

## <a name="using-python-in-sql-server"></a>À l’aide de Python dans SQL Server

Vous importez le **revoscalepy** module dans votre code Python et appellent les fonctions du module, comme toutes les autres fonctions de Python.

Sources de données pris en charge incluent des bases de données ODBC, SQL Server et format de fichier XDF pour échanger des données avec d’autres sources, ou avec des solutions R. Les données d’entrée pour Python doivent être sous forme de tableau. Tous les résultats de Python doivent être retournés sous la forme d’un **pandas** trame de données.

Contextes de calcul pris en charge incluent le contexte de calcul SQL Server local ou distant. Un contexte de calcul à distance fait référence à l’exécution de code qui démarre sur un ordinateur comme une station de travail, mais les commutateurs, le script d’exécution à un ordinateur distant. Basculement du contexte de calcul nécessite que les deux systèmes ont la même bibliothèque revoscalepy.

Contexte de calcul local, comme vous pouvez l’imaginer, inclut l’exécution de code Python sur le même serveur que l’instance du moteur de base de données avec le code à l’intérieur de T-SQL ou incorporé dans une procédure stockée. Vous pouvez également exécuter le code à partir d’un IDE Python local et que le script s’exécutent sur l’ordinateur SQL Server, en définissant à distance le contexte de calcul.

## <a name="execution-architecture"></a>Architecture de l’exécution

Les diagrammes suivants décrivent l’interaction des composants SQL Server avec le runtime Python dans chacun des scénarios pris en charge : l’exécution du script de base de données et à distance en cours d’exécution à partir d’un terminal de Python, à l’aide d’un contexte de calcul de SQL Server.

### <a name="python-scripts-executed-in-database"></a>Python scripts exécutés dans la base de données

Lorsque vous exécutez Python « à l’intérieur » de SQL Server, vous devez encapsuler le script Python à l’intérieur d’une procédure stockée spéciale, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Une fois que le script a été intégré dans la procédure stockée, n’importe quelle application qui peut appeler une procédure stockée peut lancer l’exécution du code Python.  Par la suite, SQL Server gère l’exécution de code comme résumé dans le diagramme suivant.

![script-in-db-python](../../advanced-analytics/python/media/script-in-db-python2.png)

1. Une demande pour le runtime Python est indiquée par le paramètre `@language='Python'` passé à la procédure stockée. SQL Server envoie cette demande au service Launchpad.
2. Le service Launchpad démarre le Lanceur approprié ; Dans ce cas, il s’agit de PythonLauncher.
3. PythonLauncher démarre le processus de Python35 externe.
4. BxlServer se coordonne avec le runtime Python pour gérer les échanges de données et stockage des résultats du travail.
5. SQL Satellite gère les communications sur les tâches et les processus avec SQL Server.
6. BxlServer utilise SQL Satellite pour communiquer l’état et les résultats vers SQL Server.
7. SQL Server obtient les résultats et ferme les processus et les tâches associées.

### <a name="python-scripts-executed-from-a-remote-client"></a>Scripts Python exécutés à partir d’un client distant

Vous pouvez exécuter des scripts Python à partir d’un ordinateur distant, comme un ordinateur portable et qu’ils s’exécutent dans le contexte de l’ordinateur SQl Server, si ces conditions sont remplies :

+ Vous concevez les scripts de manière appropriée
+ L’ordinateur distant a installé les bibliothèques d’extensibilité qui sont utilisés par les Services Machine Learning. Le [revoscalepy](../python/ref-py-revoscalepy.md) package est nécessaire pour utiliser des contextes de calcul à distance.

Le diagramme suivant récapitule le flux de travail global lorsque les scripts sont envoyées à partir d’un ordinateur distant.

![remote-sqlcc-from-python](../../advanced-analytics/python/media/remote-sqlcc-from-python3.png)

1. Pour les fonctions qui sont prises en charge dans **revoscalepy**, le runtime Python appelle une fonction de liaison, qui à son tour, appelle BxlServer.
2. BxlServer est fourni à Machine Learning Services (en base de données) et s’exécute dans un processus distinct du runtime Python.
3. BxlServer détermine la cible de la connexion et initie une connexion à l’aide d’ODBC, en passant les informations d’identification fournies dans le cadre de la chaîne de connexion dans le script Python.
4. BxlServer ouvre une connexion à l’instance de SQL Server.
5. Quand un runtime de script externe est appelé, le service Launchpad est appelé, qui démarre à son tour le Lanceur approprié : dans ce cas, PythonLauncher.dll. Par la suite, traitement de code Python est géré dans un flux de travail similaire à celle lorsque le code Python est appelé à partir d’une procédure stockée T-SQL.
6. PythonLauncher effectue un appel à l’instance de Python qui est installé sur l’ordinateur SQL Server.
7. Les résultats sont retournés à BxlServer.
8. SQL Satellite gère la communication avec SQL Server et le nettoyage des objets de travail associés.
9. SQL Server transmet les résultats au client.

## <a name="see-also"></a>Voir aussi

+ [module de revoscalepy dans SQL Server](../python/ref-py-revoscalepy.md)
+ [référence des fonctions revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) 
+ [Infrastructure d’extensibilité dans SQL Server](extensibility-framework.md)
+ [R et l’apprentissage des extensions dans SQL Server](extension-r.md)