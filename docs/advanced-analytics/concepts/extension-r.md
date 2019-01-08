---
title: SQL Server Machine Learning - extension du langage de programmation R
description: En savoir plus sur l’exécution de code R et les bibliothèques R intégrés dans SQL Server 2016 R Services ou SQL Server 2017 Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: cb9b710ca5ec06e05a93dbee5f22ee0860f7f4ca
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432762"
---
# <a name="r-language-extension-in-sql-server"></a>Extension du langage R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L’extension de R est la partie du complément SQL Server Machine Learning Services au moteur de base de données relationnelle. Il ajoute un environnement d’exécution de R, la distribution R de base avec les bibliothèques standards et des outils, ainsi que les bibliothèques Microsoft R : [RevoScaleR](../r/ref-r-revoscaler.md) pour analytique à grande échelle, [MicrosoftML](../r/ref-r-microsoftml.md) pour les algorithmes d’apprentissage automatique et d’autres bibliothèques pour accéder aux données ou le code R dans SQL Server.

Intégration de R est disponible dans SQL Server à partir de SQL Server 2016, [R Services](../r/sql-server-r-services.md)et en continuant vers l’avant dans le cadre de [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md).

## <a name="r-components"></a>Composants R

SQL Server inclut les packages open source et propriétaires. Les bibliothèques R de base sont installés via la distribution Microsoft de r : open source Microsoft R Open (MRO). Les utilisateurs actuels de R doivent être en mesure de déplacer leur code R et de l’exécuter comme un processus externe sur SQL Server avec peu ou pas de modifications. MRO est installé indépendamment des outils SQL et il est exécuté en dehors du processus de moteur de base, dans l’infrastructure d’extensibilité. Pendant l’installation, vous devez accepter les termes du contrat de licence open source. Par la suite, vous pouvez exécuter des packages R standard sans modification supplémentaire comme vous le feriez dans n’importe quel autre distribution open source de R. 

SQL Server ne modifie pas les exécutables R de base, mais vous devez utiliser la version de R est installé par le programme d’installation, car cette version est celle que les packages propriétaires sont conçus et testés sur. Pour plus d’informations sur comment MRO diffère d’une distribution de base de R que vous pouvez obtenir à partir de CRAN, voir [l’interopérabilité avec le langage R et des produits Microsoft R et des fonctionnalités](https://docs.microsoft.com/r-server/what-is-r-server-interoperability).

Vous trouverez la distribution de package de base R installée par le programme d’installation dans le dossier associé à l’instance. Par exemple, si vous avez installé R Services sur une instance par défaut de SQL Server 2016, les bibliothèques R se trouvent dans ce dossier par défaut : `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`. De même, les outils R associés à l’instance par défaut se trouvent dans ce dossier par défaut : `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin`.

Packages R ajoutés par Microsoft pour les charges de travail parallèles et distribuées incluent les bibliothèques suivantes.

| Bibliothèque | Description |
|---------|-------------|
| [**RevoScaleR**](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | Prend en charge les objets source de données et de l’exploration de données, de manipulation, de transformation et de visualisation. Il prend en charge la création de contextes de calcul distants, mais aussi un différents évolutive modèles d’apprentissage automatique, tel que **rxLinMod**. Les API ont été optimisées pour analyser les jeux de données qui sont trop volumineux pour être stockés en mémoire et pour effectuer des calculs distribués entre plusieurs cœurs ou processeurs. Le package RevoScaleR prend également en charge le format de fichier XDF pour accélérer le transfert et stockage des données utilisées pour l’analyse. Le format XDF est un format portable qui utilise le stockage en colonnes. Il permet de charger et manipuler des données de différentes sources, y compris une connexion texte, SPSS ou ODBC. |
| [**MicrosoftML**](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package) | Contient des algorithmes d’apprentissage automatique qui ont été optimisés pour la vitesse et la précision, ainsient que les transformations pour travailler avec le texte et des images en ligne. Pour plus d’informations, consultez [MicrosoftML dans SQL Server](../r/ref-r-microsoftml.md). | 

## <a name="using-r-in-sql-server"></a>À l’aide de R dans SQL Server

Vous pouvez utiliser un script R à l’aide des fonctions de base, mais pour tirer parti de multitraitement, vous devez importer le **RevoScaleR** et **MicrosoftML** modules dans votre code R, puis appelez ses fonctions pour créer des modèles exécuter en parallèle. 
 
Sources de données pris en charge incluent des bases de données ODBC, SQL Server et format de fichier XDF pour échanger des données avec d’autres sources, ou avec des solutions R. Les données d’entrée doivent être sous forme de tableau. Tous les résultats de R doivent être retournés sous la forme d’une trame de données.

Contextes de calcul pris en charge incluent le contexte de calcul SQL Server local ou distant. Un contexte de calcul à distance fait référence à l’exécution de code qui démarre sur un ordinateur comme une station de travail, mais les commutateurs, le script d’exécution à un ordinateur distant. Basculement du contexte de calcul nécessite que les deux systèmes ont la même bibliothèque RevoScaleR.

Contexte de calcul local, comme vous pouvez l’imaginer, inclut l’exécution du code R sur le même serveur que l’instance du moteur de base de données avec le code à l’intérieur de T-SQL ou incorporé dans une procédure stockée. Vous pouvez également exécuter le code à partir d’un IDE R local et que le script s’exécutent sur l’ordinateur SQL Server, en définissant à distance le contexte de calcul.

## <a name="execution-architecture"></a>Architecture de l’exécution

Les diagrammes suivants décrivent l’interaction des composants SQL Server avec le runtime R dans chacun des scénarios pris en charge : l’exécution du script de base de données et à distance en cours d’exécution sur une ligne de commande R, à l’aide d’un contexte de calcul de SQL Server.

### <a name="r-scripts-executed-from-sql-server-in-database"></a>Scripts R exécutés à partir de SQL Server dans la base de données

Code R qui est exécuté à partir de « inside » SQL Server est exécutée en appelant une procédure stockée. Par conséquent, toute application qui peut appeler une procédure stockée peut lancer l’exécution du code R.  Par la suite, SQL Server gère l’exécution du code R comme résumé dans le diagramme suivant.

![rsql_indb780-01](../r/media/script_in-db-r.png)

1. Une demande du runtime R est indiquée par le paramètre _@language='R'_ passé à la procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). SQL Server envoie cette demande au service Launchpad.
2. Le service Launchpad démarre le lanceur approprié, RLauncher dans ce cas.
3. RLauncher démarre le processus R externe.
4. BxlServer se coordonne avec le runtime R pour gérer les échanges de données avec SQL Server et le stockage des résultats du travail.
5. SQL Satellite gère les communications sur les tâches et les processus avec SQL Server.
6. BxlServer utilise SQL Satellite pour communiquer l’état et les résultats vers SQL Server.
7. SQL Server obtient les résultats et ferme les processus et les tâches associées.

### <a name="r-scripts-executed-from-a-remote-client"></a>Scripts R exécutés à partir d’un client distant

Lors de la connexion à partir d’un client de science des données distantes qui prend en charge de Microsoft R, vous pouvez exécuter des fonctions R dans le contexte de SQL Server en utilisant les fonctions RevoScaleR. Ce flux de travail, qui est différent du précédent, est résumé dans le diagramme suivant.

![rsql_fromR2db-01](../r/media/remote-sqlcc-from-r2.png)

1. Pour les fonctions RevoScaleR, le runtime R appelle une fonction de liaison qui à son tour, appelle BxlServer.
2. BxlServer est fourni avec Microsoft R et s’exécute dans un processus distinct du runtime R.
3. BxlServer détermine la cible de la connexion et démarre une connexion à l’aide d’ODBC, en passant les informations d’identification fournies dans la chaîne de connexion de l’objet de source de données R.
4. BxlServer ouvre une connexion à l’instance de SQL Server.
5. Pour un appel R, le service Launchpad est appelé, ce qui est le tour démarre le Lanceur approprié, RLauncher. Le traitement du code R est ensuite semblable au processus d’exécution du code R à partir de T-SQL.
6. RLauncher effectue un appel à l’instance du runtime R qui est installé sur l’ordinateur SQL Server.
7. Les résultats sont retournés à BxlServer.
8. SQL Satellite gère la communication avec SQL Server et le nettoyage des objets de travail associés.
9. SQL Server transmet les résultats au client.

## <a name="see-also"></a>Voir aussi

+ [Infrastructure d’extensibilité dans SQL Server](extensibility-framework.md)
+ [Python et l’apprentissage des extensions dans SQL Server](extension-python.md)