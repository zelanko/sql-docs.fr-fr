---
title: Extension du langage de programmation R
description: Découvrez l’exécution de code R et les bibliothèques R intégrées dans SQL Server R Services ou SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/04/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 802e5d6c5e769d59f255554f4f598d832160bbfa
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532652"
---
# <a name="r-language-extension-in-sql-server"></a>Extension du langage R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

L’extension R fait partie intégrante du module complémentaire SQL Server Machine Learning Services du moteur de base de données relationnelle. Il ajoute un environnement d’exécution R, une distribution R de base avec des bibliothèques et des outils standard ainsi que les bibliothèques Microsoft R : [RevoScaleR](../r/ref-r-revoscaler.md) pour un analytique à la bonne échelle, [MicrosoftML](../r/ref-r-microsoftml.md) pour des algorithmes de Machine Learning et d’autres bibliothèques pour accéder aux données ou au code R dans SQL Server.

L’intégration R est disponible dans [SQL Server R Services](../r/sql-server-r-services.md) et [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md).

## <a name="r-components"></a>Composants R

SQL Server comporte des packages open source et propriétaires. Les bibliothèques R de base sont installées via la distribution de R open source de Microsoft : Microsoft R Open (MRO). Les utilisateurs actuels de R doivent pouvoir porter leur code R et l’exécuter en tant que processus externe dans SQL Server avec peu ou pas de modifications. MRO est installé indépendamment des outils SQL et s’exécute en dehors des processus du moteur de base, dans le framework d’extensibilité. Pendant l’installation, vous devez accepter les termes de la licence open source. Cela vous donne le droit d’exécuter ensuite les packages R standard sans autre modification, comme dans n’importe quelle autre distribution open source de R. 

SQL Server ne modifie pas les exécutables R de base, mais vous devez utiliser la version de R qui est installée par le programme d’installation, car c’est à partir de cette version que les packages propriétaires sont créés et testés. Pour savoir ce qui distingue MRO d’une distribution de base de R que vous pouvez obtenir via CRAN, consultez [Interopérabilité avec le langage R et les produits et fonctionnalités Microsoft R](https://docs.microsoft.com/r-server/what-is-r-server-interoperability).

La distribution de packages de base R qui est installée par le programme d’installation se trouve dans le dossier associé à l’instance. Par exemple, si vous avez installé R Services sur une instance SQL Server par défaut, les bibliothèques R se trouvent par défaut dans le dossier `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`. De la même façon, les outils R associés à l’instance par défaut se trouvent par défaut dans le dossier `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin`.

Les packages R ajoutés par Microsoft pour les charges de travail parallèles et distribuées incluent les bibliothèques suivantes.

| Bibliothèque | Description |
|---------|-------------|
| [**RevoScaleR**](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | Prend en charge les objets de source de données ainsi que l’exploration, la manipulation, la transformation et la visualisation des données. Prend en charge la création de contextes de calcul distants ainsi qu’un certain nombre de modèles de Machine Learning scalables, comme **rxLinMod**. Les API ont été optimisées pour analyser les jeux de données qui sont trop volumineux pour être stockés en mémoire et pour effectuer des calculs distribués entre plusieurs cœurs ou processeurs. Le package RevoScaleR prend aussi en charge le format de fichier XDF pour accélérer le transfert et le stockage des données utilisées pour l’analyse. Le format XDF est un format portable qui utilise le stockage en colonnes. Il permet de charger et manipuler des données de différentes sources, y compris une connexion texte, SPSS ou ODBC. |
| [**MicrosoftML**](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package) | Contient des algorithmes de Machine Learning qui ont été optimisés pour la vitesse et la précision ainsi que des transformations en ligne pour permettre l’utilisation de texte et d’images. Pour plus d’informations, consultez [MicrosoftML dans SQL Server](../r/ref-r-microsoftml.md). | 

## <a name="using-r-in-sql-server"></a>Utilisation de R dans SQL Server

Vous pouvez écrire un script R en utilisant les fonctions de base, mais pour tirer parti du multitraitement, vous devez importer les modules **RevoScaleR** et **MicrosoftML** dans votre code R, puis appeler ses fonctions pour créer des modèles qui s’exécutent en parallèle. 
 
Parmi les sources de données prises en charge figurent les bases de données ODBC, SQL Server et le format de fichier XDF pour l’échange de données avec d’autres sources ou avec des solutions R. Les données d’entrée doivent être tabulaires. Tous les résultats de R doivent être retournés sous forme de trame de données.

Parmi les contextes de calcul pris en charge figurent le contexte de calcul SQL Server local ou distant. Un contexte de calcul distant fait référence à une exécution de code qui commence sur un ordinateur, par exemple une station de travail, avant que l’exécution du script bascule sur un ordinateur distant. Pour que le basculement du contexte de calcul s’opère, les deux systèmes doivent avoir la même bibliothèque RevoScaleR.

Comme vous pouvez le comprendre, le contexte de calcul local exécute notamment le code R sur le même serveur que l’instance du moteur de base de données, avec le code à l’intérieur de T-SQL ou incorporé dans une procédure stockée. Vous pouvez aussi exécuter le code à partir d’un IDE R local et faire en sorte que le script s’exécute sur l’ordinateur SQL Server, en définissant un contexte de calcul distant.

## <a name="execution-architecture"></a>Architecture d’exécution

Les schémas ci-dessous décrivent l’interaction des composants SQL Server avec le runtime R dans chacun des scénarios pris en charge suivants : exécution de script dans la base de données et exécution à distance à partir d’une ligne de commande R, en utilisant un contexte de calcul SQL Server.

### <a name="r-scripts-executed-from-sql-server-in-database"></a>Scripts R exécutés à partir de SQL Server dans la base de données

Le code R lancé de « l’intérieur » de SQL Server est exécuté en appelant une procédure stockée. Par conséquent, toute application qui peut appeler une procédure stockée peut lancer l’exécution du code R.  SQL Server gère ensuite l’exécution du code R comme résumé dans le schéma suivant.

![rsql_indb780-01](../r/media/script_in-db-r.png)

1. Une demande du runtime R est indiquée par le paramètre _@language='R'_ passé à la procédure stockée [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). SQL Server envoie cette demande au service launchpad.
Dans Linux, SQL utilise un service **launchpad** pour communiquer avec un processus launchpad distinct pour chaque utilisateur. Pour plus d’informations, consultez le [schéma de l’architecture d’extensibilité](extensibility-framework.md#architecture-diagram).
2. Le service launchpad démarre le lanceur approprié (en l’occurrence, RLauncher).
3. RLauncher démarre le processus R externe.
4. En coordination avec le runtime R, BxlServer gère les échanges de données avec SQL Server et le stockage des résultats du travail.
5. SQL Satellite gère les communications avec SQL Server sur les tâches et les processus associés.
6. BxlServer utilise SQL Satellite pour communiquer l’état et les résultats à SQL Server.
7. SQL Server obtient les résultats et ferme les tâches et les processus associés.

### <a name="r-scripts-executed-from-a-remote-client"></a>Scripts R exécutés à partir d’un client distant

Si vous vous connectez à partir d’un client de science des données distant qui prend en charge Microsoft R, vous pouvez exécuter des fonctions R dans le contexte de SQL Server en utilisant les fonctions RevoScaleR. Ce flux de travail, qui est différent du précédent, est résumé dans le diagramme suivant.

![rsql_fromR2db-01](../r/media/remote-sqlcc-from-r2.png)

1. Pour les fonctions RevoScaleR, le runtime R appelle une fonction de liaison qui, à son tour, appelle BxlServer.
2. BxlServer est fourni avec Microsoft R et s’exécute dans un processus distinct du runtime R.
3. BxlServer détermine la cible de la connexion et démarre une connexion à l’aide d’ODBC, en passant les informations d’identification fournies dans la chaîne de connexion de l’objet de source de données R.
4. BxlServer ouvre une connexion à l’instance SQL Server.
5. Pour un appel R, le service launchpad est appelé, lequel démarre ad le lanceur approprié, c’est-à-dire RLauncher. Le traitement du code R est ensuite semblable au processus d’exécution du code R à partir de T-SQL.
6. RLauncher effectue un appel à l’instance du runtime R qui est installé sur l’ordinateur SQL Server.
7. Les résultats sont retournés à BxlServer.
8. SQL Satellite gère la communication avec SQL Server et le nettoyage des objets de travail associés.
9. SQL Server transmet en retour les résultats au client.

## <a name="see-also"></a>Voir aussi

+ [Framework d’extensibilité dans SQL Server](extensibility-framework.md)
+ [Extensions Python et de Machine Learning dans SQL Server](extension-python.md)