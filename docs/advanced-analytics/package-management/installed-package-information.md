---
title: Par défaut des bibliothèques de packages R et Python - SQL Server Machine Learning Services
description: Packages R et Python installées par SQL Server pour R, R Server, Machine Learning Services (en base de données) et Machine Learning Server (autonome)
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 3126872e3333383d0cea53f38b3cfd06be86b704
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141398"
---
# <a name="default-r-and-python-packages-in-sql-server"></a>Packages par défaut R et Python dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article répertorie les packages R et Python installés avec SQL Server et où trouver la bibliothèque de packages.  

## <a name="r-package-list-for-sql-server"></a>Liste des packages R pour SQL Server

Packages R sont installés avec [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) et [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) lorsque vous sélectionnez la fonctionnalité R pendant l’installation. 

|.         | 2016 | 2017 | Description |
|----------------|--------------|--------------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | 9.2 | Utilisée pour les contextes de calcul à distance, de diffusion en continu, l’exécution parallèle des fonctions rx pour importer des données et de transformation, de modélisation, de visualisation et d’analyse. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | 9.2 |Utilisé pour inclure un script R dans les procédures stockées. |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.2 | Ajoute des algorithmes d’apprentissage automatique dans R. | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a.  | 9.2 | Utilisé pour écrire des instructions MDX dans R. |

MicrosoftML et olapR sont disponibles par défaut dans SQL Server 2017 Machine Learning Services. Sur une instance de SQL Server 2016 R Services, vous pouvez ajouter ces packages via un [mise à niveau du composant](../install/upgrade-r-and-python.md). Une mise à niveau du composant obtient également les versions plus récentes des packages (par exemple, des versions plus récentes de RevoScaleR incluent des fonctions de gestion des packages sur SQL Server).

## <a name="python-package-list-for-sql-server"></a>Liste des packages Python pour SQL Server

Packages Python sont uniquement disponibles dans SQL Server 2017 lorsque vous installez [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) et sélectionnez le composant de Python.

| .         | 2017    |  Description |
| -----------------|-------------|------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2 | Utilisée pour les contextes de calcul à distance, de diffusion en continu, l’exécution parallèle des fonctions rx pour importer des données et de transformation, de modélisation, de visualisation et d’analyse. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2 | Ajoute des algorithmes d’apprentissage automatique dans Python. |

## <a name="open-source-r-in-your-installation"></a>R Open source dans votre installation

Prise en charge R inclut open source sont afin que vous pouvez appeler des fonctions base R et installer des packages tiers et open source supplémentaires. Prise en charge du langage R inclut les fonctionnalités principales telles que **base**, **statistiques**, **utils**et d’autres. Une installation de base de R inclut également de nombreux exemples de datasets et les outils R standards, tels que **RGui** (un éditeur interactif léger) et **RTerm** (une invite de commandes R). 

La distribution de R open source inclus dans votre installation est [Microsoft R ouvrir (MRO)](https://mran.microsoft.com/open). MRO enrichit R de base en incluant des packages open source supplémentaires telles que la [Intel Math Kernel Library](https://en.wikipedia.org/wiki/Math_Kernel_Library).

Le tableau suivant récapitule les versions de R fournis par MRO à l’aide du programme d’installation de SQL Server.

|Version             | Version de R       |
|--------------------|-----------------|
| [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) | 3.2.2   | 
| [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) | 3.3.3 |

Vous ne devez jamais manuellement remplacer la version de R est installé par le programme d’installation de SQL Server avec des versions plus récentes sur le web. Packages R de Microsoft sont basées sur des versions spécifiques de la modification de R. votre installation peut déstabiliser il.

## <a name="open-source-python-in-your-installation"></a>Python Open source dans votre installation

SQL Server 2017 ajoute des composants de Python. Lorsque vous sélectionnez l’option de langage Python, Anaconda 4.2 distribution est installée. En plus des bibliothèques de code Python, l’installation standard inclut des exemples de données, des tests unitaires et des exemples de scripts. 

SQL Server 2017 Machine Learning est la première version R et Python prennent en charge.

|Version             | Version de anaconda| Packages Microsoft    |
|--------------------|-----------------|-----------------------|
| SQL Server 2017 Machine Learning Services  | 4.2 sur Python 3.5 | revoscalepy, microsoftml |

Vous ne devez jamais manuellement remplacer la version de Python installées par le programme d’installation de SQL Server avec des versions plus récentes sur le web. Packages Python de Microsoft sont basées sur des versions spécifiques d’Anaconda. Modification de votre installation, il peut déstabiliser.

## <a name="component-upgrades"></a>Mises à niveau du composant

Après une installation initiale, les packages R et Python sont actualisés via les service packs et mises à jour cumulatives, mais les mises à niveau de la version complète ne sont possibles que par *liaison* à la politique de Support de cycle de vie moderne. Liaison modifie le modèle de maintenance. Par défaut, après une installation initiale, les packages R sont actualisés via les service packs et mises à jour cumulatives. Packages supplémentaires et des mises à niveau de la version complète des composants R sont possibles seulement via les mises à niveau de produit (à partir de SQL Server 2016 vers SQL Server 2017) ou en liant R prennent en charge Microsoft Machine Learning Server. Pour plus d’informations, consultez [composants de mise à niveau de R et Python dans SQL Server](../install/upgrade-r-and-python.md).

## <a name="package-library-location"></a>Emplacement de bibliothèque de package

Lorsque vous installez un apprentissage avec SQL Server, une bibliothèque de package unique est créée au niveau de l’instance pour chaque langue que vous installez. Sur Windows, la bibliothèque de l’instance est un dossier sécurisé enregistré avec SQL Server.

Tous les script ou un code que s’exécute dans la base de données sur SQL Server doit charger les fonctions de la bibliothèque de l’instance. SQL Server ne peut pas accéder aux packages installés dans d’autres bibliothèques. Cela vaut pour les clients distants. Lors de la connexion au serveur à partir d’un client distant, tout code R ou Python que vous souhaitez exécuter dans le contexte de calcul de serveur permet uniquement les packages installés dans la bibliothèque de l’instance.

Pour protéger des ressources du serveur, la bibliothèque d’instance par défaut peut être modifiée uniquement par un administrateur de l’ordinateur. Si vous n’êtes pas le propriétaire de l’ordinateur, vous devrez peut-être obtenir l’autorisation d’un administrateur pour installer les packages dans cette bibliothèque. 

#### <a name="file-path-for-in-database-engine-instances"></a>Chemin d’accès pour les instances du moteur de base de données

Le tableau suivant montre l’emplacement du fichier de base de données et de la version de R et Python combinaisons d’instance de moteur. MSSQL13 indique SQL Server 2016 et R uniquement. MSSQL14 indique SQL Server 2017 et contient les dossiers de R et Python. 

Chemins de fichier incluent également les noms d’instance. SQL Server installe [instances du moteur de base de données](../../database-engine/configure-windows/database-engine-instances-sql-server.md) en tant que l’instance par défaut (MSSQLSERVER) ou une instance nommée défini par l’utilisateur. Si SQL Server est installé comme instance nommée, vous verrez ce nom ajouté comme suit : `MSSQL13.<instance_name>`.

|Version et la langue  | Chemin d’accès par défaut|
|----------------------|------------|
| SQL Server 2016 |C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library|
| SQL Server 2017 avec R|C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library |
| SQL Server 2017 avec Python |C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages |


#### <a name="file-path-for-standalone-server-installations"></a>Chemin d’accès de fichier pour les installations de serveur autonome

Le tableau suivant répertorie les chemins d’accès par défaut des fichiers binaires lorsque SQL Server 2016 R Server (autonome) ou serveur de SQL Server 2017 Machine Learning Server (autonome) est installé. 

|Version| Installation|Chemin d’accès par défaut|
|-------|-------------|------------|
| SQL Server 2016|R Server (autonome)| C:\Program Files\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Machine Learning Server, avec R |C:\Program Files\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning Server, avec Python |C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Si vous trouvez d’autres dossiers ayant des noms similaires sous-dossier et fichiers, vous avez probablement une installation autonome de Microsoft R Server ou [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/). Ces produits serveurs ont différents programmes d’installation et les chemins d’accès (à savoir C:\Program Files\Microsoft\R Server\R_SERVER ou C:\Program Files\Microsoft\ML SERVER\R_SERVER). Pour plus d’informations, consultez [installer Machine Learning Server pour Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) ou [installer R Server 9.1 pour Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="next-steps"></a>Étapes suivantes

+ [Obtenir les informations sur le package](installed-package-information.md)
+ [Installer de nouveaux packages R](../r/install-additional-r-packages-on-sql-server.md)
+ [Installer de nouveaux packages Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Activer la gestion de packages R à distance](../r/r-package-how-to-enable-or-disable.md)
+ [Fonctions RevoScaleR pour la gestion de packages R](../r/use-revoscaler-to-manage-r-packages.md)
+ [Synchronisation de package R](../r/package-install-uninstall-and-sync.md)
+ [miniCRAN pour référentiel de packages R local](../r/create-a-local-package-repository-using-minicran.md)
