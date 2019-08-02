---
title: Bibliothèques de packages R et Python par défaut
description: Packages r et Python installés par SQL Server pour R services, R Server, Machine Learning Services (dans la base de données) et Machine Learning Server (autonome)
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e49b843b0b32969bd440177cf445916487ad2670
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715200"
---
# <a name="default-r-and-python-packages-in-sql-server"></a>Packages R et Python par défaut dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article répertorie les packages R et Python installés avec SQL Server et où trouver la bibliothèque de packages.  

## <a name="r-package-list-for-sql-server"></a>Liste des packages R pour SQL Server

Les packages r sont installés avec [SQL Server 2016 R services](../install/sql-r-services-windows-install.md) et [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md) lorsque vous sélectionnez la fonctionnalité r lors de l’installation. 

|.         | 2016 | 2017 | Description |
|----------------|--------------|--------------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | 9,2 | Utilisé pour les contextes de calcul distants, la diffusion en continu et l’exécution parallèle des fonctions RX pour l’importation et la transformation des données, la modélisation, la visualisation et l’analyse. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | 9,2 |Utilisé pour inclure le script R dans les procédures stockées. |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9,2 | Ajoute des algorithmes de Machine Learning dans R. | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a.  | 9,2 | Utilisé pour écrire des instructions MDX dans R. |

MicrosoftML et OLAP sont disponibles par défaut dans SQL Server Machine Learning Services. Sur une instance SQL Server 2016 R services, vous pouvez ajouter ces packages par le biais d’une [mise à niveau de composant](../install/upgrade-r-and-python.md). Une mise à niveau de composant vous fournit également des versions plus récentes des packages (par exemple, les versions plus récentes de RevoScaleR incluent des fonctions de gestion des packages sur SQL Server).

## <a name="python-package-list-for-sql-server"></a>Liste des packages Python pour SQL Server

Les packages Python sont disponibles uniquement dans SQL Server 2017 lorsque vous installez [SQL Server machine learning services](../install/sql-machine-learning-services-windows-install.md) et sélectionnez la fonctionnalité Python.

| .         | 2017    |  Description |
| -----------------|-------------|------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9,2 | Utilisé pour les contextes de calcul distants, la diffusion en continu et l’exécution parallèle des fonctions RX pour l’importation et la transformation des données, la modélisation, la visualisation et l’analyse. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9,2 | Ajoute des algorithmes de Machine Learning dans Python. |

## <a name="open-source-r-in-your-installation"></a>R Open source dans votre installation

La prise en charge de r comprend Open-source afin que vous puissiez appeler des fonctions R de base et installer des packages Open source et tiers supplémentaires. La prise en charge du langage R comprend des fonctionnalités principales telles que la **base**, les **statistiques**, les **utils**et d’autres. Une installation de base de R comprend également de nombreux exemples de jeux de données, ainsi que des outils R standard tels que **RGui** (un éditeur interactif léger) et **RTerm** (une invite de commandes r). 

La distribution du R Open source inclus dans votre installation est [Microsoft R Open (MRO)](https://mran.microsoft.com/open). MRO ajoute de la valeur à base R en incluant des packages Open source supplémentaires, tels que la [bibliothèque de noyaux mathématiques Intel](https://en.wikipedia.org/wiki/Math_Kernel_Library).

Le tableau suivant récapitule les versions de R fournies par MRO à l’aide du programme d’installation de SQL Server.

|Libérer             | Version R       |
|--------------------|-----------------|
| [SQL Server 2016 R services](../install/sql-r-services-windows-install.md) | 3.2.2   | 
| [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) | 3.3.3 |

Vous ne devez jamais remplacer manuellement la version de R installée par SQL Server installation avec des versions plus récentes sur le Web. Les packages Microsoft R sont basés sur des versions spécifiques de R. la modification de votre installation pourrait le déstabiliser.

## <a name="open-source-python-in-your-installation"></a>Python Open source dans votre installation

SQL Server 2017 ajoute des composants Python. Lorsque vous sélectionnez l’option de langage Python, la distribution Anaconda 4,2 est installée. En plus des bibliothèques de code Python, l’installation standard comprend des exemples de données, des tests unitaires et des exemples de scripts. 

SQL Server 2017 Machine Learning est la première version à avoir la prise en charge de R et de Python.

|Libérer             | Version de Anaconda| Packages Microsoft    |
|--------------------|-----------------|-----------------------|
| SQL Server Machine Learning Services  | 4,2 sur Python 3,5 | revoscalepy, microsoftml |

Vous ne devez jamais remplacer manuellement la version de Python installée par SQL Server installation avec des versions plus récentes sur le Web. Les packages Microsoft Python sont basés sur des versions spécifiques de Anaconda. La modification de votre installation pourrait le déstabiliser.

## <a name="component-upgrades"></a>Mises à niveau de composants

Après une installation initiale, les packages R et Python sont actualisés par le biais des service packs et des mises à jour cumulatives, mais la mise à niveau complète de la version n’est possible qu’en *liant* la stratégie de support du cycle de vie moderne. La liaison modifie le modèle de maintenance. Par défaut, après une installation initiale, les packages R sont actualisés par le biais des service packs et des mises à jour cumulatives. Les packages supplémentaires et les mises à niveau de version complète des composants de base de R sont uniquement possibles par le biais de mises à niveau de produit (de SQL Server 2016 à SQL Server 2017) ou par liaison de la prise en charge de R à Microsoft Machine Learning Server. Pour plus d’informations, consultez [mettre à niveau les composants R et Python dans SQL Server](../install/upgrade-r-and-python.md).

## <a name="package-library-location"></a>Emplacement de la bibliothèque de packages

Lorsque vous installez Machine Learning avec SQL Server, une seule bibliothèque de packages est créée au niveau de l’instance pour chaque langue que vous installez. Sur Windows, la bibliothèque d’instances est un dossier sécurisé enregistré avec SQL Server.

Tout script ou code qui s’exécute dans la base de données sur SQL Server doit charger des fonctions à partir de la bibliothèque d’instances. SQL Server ne peut pas accéder aux packages installés dans d’autres bibliothèques. Cela s’applique également aux clients distants. Lors de la connexion au serveur à partir d’un client distant, tout code R ou python que vous souhaitez exécuter dans le contexte de calcul du serveur ne peut utiliser que les packages installés dans la bibliothèque d’instances.

Pour protéger les ressources du serveur, la bibliothèque d’instances par défaut ne peut être modifiée que par un administrateur de l’ordinateur. Si vous n’êtes pas le propriétaire de l’ordinateur, vous devrez peut-être demander à un administrateur d’installer des packages sur cette bibliothèque. 

#### <a name="file-path-for-in-database-engine-instances"></a>Chemin d’accès de fichier pour les instances de moteur dans la base de données

Le tableau suivant montre l’emplacement du fichier R et Python pour les combinaisons de version et d’instance du moteur de base de données. MSSQL13 indique SQL Server 2016 et est R uniquement. MSSQL14 indique SQL Server 2017 et contient des dossiers R et Python. 

Les chemins d’accès aux fichiers incluent également des noms d’instance. SQL Server installe les [instances du moteur de base de données](../../database-engine/configure-windows/database-engine-instances-sql-server.md) en tant qu’instance par défaut (MSSQLSERVER) ou en tant qu’instance nommée définie par l’utilisateur. Si SQL Server est installé en tant qu’instance nommée, vous verrez que ce nom est ajouté comme `MSSQL13.<instance_name>`suit:.

|Version et langue  | Chemin d’accès par défaut|
|----------------------|------------|
| SQL Server 2016 |C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library|
| SQL Server 2017 avec R|C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library |
| SQL Server 2017 avec Python |C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages |


#### <a name="file-path-for-standalone-server-installations"></a>Chemin d’accès de fichier pour les installations de serveurs autonomes

Le tableau suivant répertorie les chemins d’accès par défaut des fichiers binaires lorsque SQL Server 2016 R Server (autonome) ou SQL Server 2017 Machine Learning Server serveur (autonome) est installé. 

|Version| Installation|Chemin d’accès par défaut|
|-------|-------------|------------|
| SQL Server 2016|R Server (autonome)| C:\Program Files\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Machine Learning Server, avec R |C:\Program Files\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning Server, avec Python |C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Si vous trouvez d’autres dossiers possédant des noms de sous-dossiers et des fichiers similaires, vous disposez probablement d’une installation autonome de Microsoft R Server ou [machine learning Server](https://docs.microsoft.com/machine-learning-server/). Ces produits serveur ont des programmes d’installation et des chemins d’accès différents (à savoir C:\Program Files\Microsoft\R Server\R_SERVER ou C:\Program Files\Microsoft\ML SERVER\R_SERVER). Pour plus d’informations, consultez [installer machine learning Server pour Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) ou [installer R Server 9,1 pour Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="next-steps"></a>Étapes suivantes

+ [Obtenir les informations sur le package](installed-package-information.md)
+ [Installer de nouveaux packages R](../r/install-additional-r-packages-on-sql-server.md)
+ [Installer de nouveaux packages Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Activer la gestion de packages R à distance](../r/r-package-how-to-enable-or-disable.md)
+ [Fonctions RevoScaleR pour la gestion de packages R](../r/use-revoscaler-to-manage-r-packages.md)
+ [Synchronisation de package R](../r/package-install-uninstall-and-sync.md)
+ [miniCRAN pour référentiel de packages R local](../r/create-a-local-package-repository-using-minicran.md)
