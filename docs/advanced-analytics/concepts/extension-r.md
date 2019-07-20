---
title: Extension du langage de programmation R
description: En savoir plus sur l’exécution de code R et les bibliothèques R intégrées dans SQL Server 2016 R services ou SQL Server 2017 Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 3bf8e77cec92cde0e5a8adf4d3e1e36f1689b917
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68343413"
---
# <a name="r-language-extension-in-sql-server"></a>Extension de langage R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L’extension R fait partie du module complémentaire SQL Server Machine Learning Services au moteur de base de données relationnelle. Il ajoute un environnement d’exécution R, une distribution de base R avec des bibliothèques et des outils standard, ainsi que les bibliothèques Microsoft R: [RevoScaleR](../r/ref-r-revoscaler.md) pour l’analyse à l’échelle, [MicrosoftML](../r/ref-r-microsoftml.md) pour les algorithmes de machine learning et d’autres bibliothèques pour accéder aux données ou au code R dans SQL Server.

L’intégration de r est disponible en SQL Server à partir de SQL Server 2016, avec [R services](../r/sql-server-r-services.md), et par progression dans le cadre de [SQL Server machine learning services](../what-is-sql-server-machine-learning.md).

## <a name="r-components"></a>Composants R

SQL Server comprend à la fois des packages Open source et propriétaires. Les bibliothèques R de base sont installées par le biais de la distribution de R Open source de Microsoft: Microsoft R Open (MRO). Les utilisateurs actuels de R doivent être en mesure de déplacer leur code R et de l’exécuter en tant que processus externe sur SQL Server avec peu ou pas de modifications. MRO est installé indépendamment des outils SQL et est exécuté en dehors des processus du moteur de base, dans l’infrastructure d’extensibilité. Pendant l’installation, vous devez accepter les termes de la licence Open source. Par la suite, vous pouvez exécuter des packages R standard sans autre modification, comme vous le feriez pour toute autre distribution Open source de R. 

SQL Server ne modifie pas les fichiers exécutables R de base, mais vous devez utiliser la version de R installée par le programme d’installation, car cette version est celle sur laquelle les packages propriétaires sont créés et testés. Pour plus d’informations sur la façon dont MRO diffère d’une distribution de base de R que vous pouvez obtenir de CRAN, consultez [interopérabilité avec le langage r et les produits et fonctionnalités Microsoft r](https://docs.microsoft.com/r-server/what-is-r-server-interoperability).

La distribution du package R de base installée par le programme d’installation se trouve dans le dossier associé à l’instance. Par exemple, si vous avez installé R services sur une instance SQL Server 2016 par défaut, les bibliothèques R se trouvent dans ce dossier par `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`défaut:. De même, les outils R associés à l’instance par défaut se trouvent dans ce dossier par défaut: `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin`.

Les packages R ajoutés par Microsoft pour les charges de travail distribuées et parallèles incluent les bibliothèques suivantes.

| Bibliothèque | Description |
|---------|-------------|
| [**RevoScaleR**](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | Prend en charge les objets de source de données et l’exploration, la manipulation, la transformation et la visualisation des données. Il prend en charge la création de contextes de calcul distants, ainsi qu’un certain nombre de modèles de Machine Learning évolutifs, tels que **rxLinMod**. Les API ont été optimisées pour analyser les jeux de données qui sont trop volumineux pour être stockés en mémoire et pour effectuer des calculs distribués entre plusieurs cœurs ou processeurs. Le package RevoScaleR prend également en charge le format de fichier XDF pour accélérer le déplacement et le stockage des données utilisées pour l’analyse. Le format XDF est un format portable qui utilise le stockage en colonnes. Il permet de charger et manipuler des données de différentes sources, y compris une connexion texte, SPSS ou ODBC. |
| [**MicrosoftML**](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package) | Contient des algorithmes de Machine Learning qui ont été optimisés pour la vitesse et la précision, ainsi que des transformations en ligne pour l’utilisation de texte et d’images. Pour plus d’informations, consultez [MicrosoftML dans SQL Server](../r/ref-r-microsoftml.md). | 

## <a name="using-r-in-sql-server"></a>Utilisation de R dans SQL Server

Vous pouvez écrire un script R à l’aide de fonctions de base, mais pour tirer parti du traitement multiprocesseur, vous devez importer les modules **RevoScaleR** et **MicrosoftML** dans votre code R, puis appeler ses fonctions pour créer des modèles qui s’exécutent en parallèle. 
 
Les sources de données prises en charge incluent les bases de données ODBC, les SQL Server et le format de fichier XDF pour échanger des données avec d’autres sources, ou avec des solutions R. Les données d’entrée doivent être tabulaires. Tous les résultats R doivent être retournés sous la forme d’une trame de données.

Les contextes de calcul pris en charge incluent un contexte de calcul local ou distant SQL Server. Un contexte de calcul distant fait référence à l’exécution de code qui démarre sur un ordinateur, tel qu’une station de travail, mais bascule l’exécution du script sur un ordinateur distant. Le basculement du contexte de calcul nécessite que les deux systèmes aient la même bibliothèque RevoScaleR.

Le contexte de calcul local, comme vous pouvez vous y attendre, comprend l’exécution de code R sur le même serveur que l’instance du moteur de base de données, avec le code à l’intérieur de T-SQL ou incorporé dans une procédure stockée. Vous pouvez également exécuter le code à partir d’un IDE R local et faire en sorte que le script s’exécute sur l’ordinateur SQL Server, en définissant un contexte de calcul distant.

## <a name="execution-architecture"></a>Architecture d’exécution

Les diagrammes suivants décrivent l’interaction des composants SQL Server avec le runtime R dans chacun des scénarios pris en charge: exécution du script dans la base de données et exécution à distance à partir d’une ligne de commande R à l’aide d’un contexte de calcul SQL Server.

### <a name="r-scripts-executed-from-sql-server-in-database"></a>Scripts R exécutés à partir de SQL Server dans la base de données

Le code R exécuté à partir de «Inside» SQL Server est exécuté en appelant une procédure stockée. Par conséquent, toute application qui peut appeler une procédure stockée peut lancer l’exécution du code R.  Ensuite SQL Server gère l’exécution du code R comme résumé dans le diagramme suivant.

![rsql_indb780-01](../r/media/script_in-db-r.png)

1. Une demande du runtime R est indiquée par le paramètre _@language='R'_ passé à la procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). SQL Server envoie cette demande au service launchpad.
2. Le service Launchpad démarre le lanceur approprié, RLauncher dans ce cas.
3. RLauncher démarre le processus R externe.
4. BxlServer coordonne avec le runtime R pour gérer les échanges de données avec SQL Server et le stockage des résultats de travail.
5. SQL satellite gère les communications sur les tâches et les processus connexes avec SQL Server.
6. BxlServer utilise SQL satellite pour communiquer l’État et les résultats à SQL Server.
7. SQL Server obtient les résultats et ferme les tâches et processus associés.

### <a name="r-scripts-executed-from-a-remote-client"></a>Scripts R exécutés à partir d’un client distant

Lors de la connexion à partir d’un client de science des données distant qui prend en charge Microsoft R, vous pouvez exécuter des fonctions R dans le contexte d’SQL Server à l’aide des fonctions RevoScaleR. Ce flux de travail, qui est différent du précédent, est résumé dans le diagramme suivant.

![rsql_fromR2db-01](../r/media/remote-sqlcc-from-r2.png)

1. Pour les fonctions RevoScaleR, le runtime R appelle une fonction de liaison qui à son tour appelle BxlServer.
2. BxlServer est fourni avec Microsoft R et s’exécute dans un processus distinct du runtime R.
3. BxlServer détermine la cible de la connexion et démarre une connexion à l’aide d’ODBC, en passant les informations d’identification fournies dans la chaîne de connexion de l’objet de source de données R.
4. BxlServer ouvre une connexion à l’instance SQL Server.
5. Pour un appel R, le service Launchpad est appelé, ce qui a pour conséquence de démarrer le lanceur approprié, RLauncher. Le traitement du code R est ensuite semblable au processus d’exécution du code R à partir de T-SQL.
6. RLauncher effectue un appel à l’instance du runtime R qui est installée sur l’ordinateur SQL Server.
7. Les résultats sont retournés à BxlServer.
8. SQL satellite gère la communication avec SQL Server et le nettoyage des objets de traitement associés.
9. SQL Server renvoie les résultats au client.

## <a name="see-also"></a>Voir aussi

+ [Infrastructure d’extensibilité dans SQL Server](extensibility-framework.md)
+ [Python et les extensions de Machine Learning dans SQL Server](extension-python.md)