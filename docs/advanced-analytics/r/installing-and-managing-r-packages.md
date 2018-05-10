---
title: Bibliothèques de package de R et Python dans SQL Server R et l’apprentissage de configuration de SQL Server par défaut | Documents Microsoft
description: Packages R et Python installés par SQL Server pour R Services, R Server, Machine Learning Services (de-de base de données) et la Machine Learning Server (autonome)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/08/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ee2c8124cf3487ca300c0b08ea113c8e66b114f4
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="default-r-and-python-packages-in-sql-server"></a>Par défaut R et Python packages dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article traite des bibliothèques de package, l’emplacement et les versions des packages R et Python installés avec SQL Server. 

## <a name="using-the-default-instance-library"></a>À l’aide de la bibliothèque d’instance par défaut

Lorsque vous installez un apprentissage avec SQL Server, une bibliothèque de package unique est créée au niveau de l’instance pour chaque langue que vous installez. 

Tout script ou un code que s’exécute dans-base de données sur SQL Server doit charger les fonctions de la bibliothèque de l’instance. SQL Server ne peut pas accéder aux packages installés dans d’autres bibliothèques. Cela vaut pour les clients distants. Lors de la connexion au serveur à partir d’un client distant, tout code R ou Python que vous souhaitez exécuter dans le contexte de calcul de serveur permet uniquement les packages installés dans la bibliothèque de l’instance.

Pour protéger des ressources du serveur, la bibliothèque d’instance par défaut est installée dans un dossier sécurisé qui est enregistré avec SQL Server et peut être modifié que par un administrateur de l’ordinateur. Si vous n’êtes pas le propriétaire de l’ordinateur, vous devrez peut-être obtenir l’autorisation d’un administrateur pour installer des packages pour cette bibliothèque. 

Même si vous êtes propriétaire de l’ordinateur, vous devez envisager l’utilité de n’importe quel package R ou Python particulier dans un environnement de serveur avant d’ajouter le package à la bibliothèque de l’instance. Prendre en compte des facteurs tels que la taille des fichiers de package et le besoin de plusieurs versions, ainsi que si le package requiert le réseau ou internet access.

### <a name="in-database-engine-instance-file-paths"></a>Chemins de fichier d’instance du moteur de la base de données

Le tableau suivant indique l’emplacement du fichier de base de données et la version de R et Python combinaisons d’instance du moteur. 

|Version | Nom de l'instance|Chemin d’accès par défaut|
|--------|--------------|------------|
| SQL Server 2016 |instance par défaut| C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library|
| SQL Server 2016 |instance nommée | C:\Program Files\Microsoft SQL Server\MSSQL13. < nom_instance > \R_SERVICES\library|
| SQL Server 2017 avec R|instance par défaut | C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library |
| SQL Server 2017 avec R|instance nommée| C:\Program Files\Microsoft SQL Server\MSSQL14. MyNamedInstance\R_SERVICES\library |
| SQL Server 2017 avec Python |instance par défaut | C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\library |
| SQL Server 2017 avec Python|instance nommée| C:\Program Files\Microsoft SQL Server\MSSQL14. < nom_instance > \PYTHON_SERVICES\library |

### <a name="standalone-server-file-paths"></a>Chemins d’accès des fichiers de serveur autonome 

Le tableau suivant répertorie les chemins d’accès par défaut des fichiers binaires lors de l’installation de SQL Server 2016 R Server (autonome) ou SQL Server 2017 Machine Learning Server (autonome). 

|Version| Installation|Chemin d’accès par défaut|
|------|------|------|
| SQL Server 2016|R Server (autonome)| C:\Program Files\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Apprentissage de serveur, avec R |C:\Program Files\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Apprentissage de serveur, avec Python |C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Si vous trouvez d’autres dossiers ayant des noms similaires sous-dossier et les fichiers, vous disposez probablement d’une installation autonome de Microsoft R Server ou [serveur Machine Learning](https://docs.microsoft.com/machine-learning-server/). Ces produits de serveur ont des programmes d’installation différents et de chemins d’accès (à savoir, C:\Program Files\Microsoft\R Server\R_SERVER ou C:\Program Files\Microsoft\ML SERVER\R_SERVER). Pour plus d’informations, consultez [installer Machine Learning pour Windows Server](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) ou [installer R Server 9.1 pour Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="what-is-included-in-a-default-installation"></a>Ce qui est inclus dans une installation par défaut

Cette section résume les fonctionnalités de R et Python incluses dans une installation par défaut.

### <a name="r-components"></a>Composants R

Les composants incluent la distribution de Microsoft r open source en tant que [Microsoft R Open](https://mran.microsoft.com/open). Les packages R de base incluent les fonctionnalités principales, tels que **statistiques** et **utils**. Vous pouvez exécuter `installed.packages(priority = "base")` pour retourner une liste de packages. Une installation de base de R inclut également de nombreux exemples de datasets et les outils R standard tels que RGui (un éditeur interactif léger) et RTerm (une invite de commandes R).

Incluent des packages Microsoft [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) pour les contextes de calcul à distance, diffusion en continu, l’exécution des fonctions rx pour l’importation de données et de transformation en parallèle, de modélisation, visualisation et l’analyse. [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package) ajoute l’apprentissage de modélisation dans R. Les autres packages incluent [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) pour écrire des instructions MDX dans R et [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) pour inclure un script R dans les procédures stockées.


|Version             | Version de R       | Packages de Microsoft    |
|--------------------|-----------------|-----------------------|
| SQL Server 2016 R Services | 3.2.2   | RevoScaleR, sqlrutil  |
| SQL Server 2017 Machine Learning Services| 3.4.3 | RevoScaleR, MicrosoftML, olapR, sqlrutil|

Vous pouvez ajouter des packages et des modèles préinstallées à SQL Server 2016 R Services en le liant à la stratégie de prise en charge du cycle de vie moderne. Liaison modifie le modèle de maintenance. Par défaut, après une installation initiale, les packages R sont actualisés via les service packs et mises à jour cumulatives. Autres packages et des mises à niveau de la version complète des composants R sont possibles seulement via les mises à niveau de produit (à partir de SQL Server 2016 à SQL Server 2017) ou par R de liaison prend en charge Microsoft Machine Learning Server. Pour plus d’informations, consultez [des composants R de mise à niveau et Python dans SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="python-components"></a>Composants de Python

SQL Server 2017 ajoute des composants de Python. Lorsque vous sélectionnez l’option de langage Python, une distribution Anaconda est installée. En plus des bibliothèques de code Python, l’installation standard inclut des exemples de données, les tests unitaires et les exemples de scripts. 

Incluent des packages Microsoft [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) sous la forme de Python de RevoScaleR, avec la diffusion en continu, l’exécution des fonctions rx pour l’importation de données et de transformation, de modélisation, de visualisation et d’analyse en parallèle. Un autre package Python est [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) pour l’apprentissage et de transformations, analyse de calcul de score, text et image et d’extraction de fonctionnalité pour dériver les valeurs de données existantes.

SQL Server 2017 Machine Learning est la première version de R et Python prennent en charge.

|Version             | Version de anaconda| Packages de Microsoft    |
|--------------------|-----------------|-----------------------|
| SQL Server 2017 Machine Learning Services  | 4.2 sur Python 3.5 | revoscalepy, microsoftml |

Après l’installation initiale, packages Python sont actualisés via les service packs et mises à jour cumulatives, mais les mises à niveau de la version complète sont uniquement possibles en liaison prise en charge de Python pour Microsoft Machine Learning Server. Pour plus d’informations, consultez [des composants R de mise à niveau et Python dans SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="administrative-permissions-for-package-installation"></a>Autorisations d’administration pour l’installation du package

Les autorisations requises pour l’installation du package ont été modifiés entre SQL Server 2016 et SQL Server 2017.

+ Dans SQL Server 2016, un accès administrateur est requis pour l’installation de nouveaux packages R.
+ Dans SQL Server 2017, vous pouvez continuer à installer des packages en tant qu’administrateur pour R et Python, et c’est probablement la méthode la plus simple. 

    L’instruction DDL, créer une bibliothèque externe, permet à l’administrateur de base de données installer les packages sans utiliser les outils R. 

    Si vous utilisez la fonctionnalité de gestion de package pour l’apprentissage d’ordinateur serveur, vous pouvez utiliser RevoScaleR pour installer des packages R au niveau de la base de données. L’administrateur de base de données doit activer la fonctionnalité et puis accorder aux utilisateurs la possibilité d’installer leurs propres packages sur une base de chaque base de données. Pour plus d’informations, consultez [activer la gestion des packages à l’aide de la DDL](r-package-how-to-enable-or-disable.md).

### <a name="user-libraries-are-not-supported"></a>Bibliothèques utilisateur ne sont pas pris en charge.

Les utilisateurs qui ne peut pas installer un package dans un emplacement sécurisé souvent recours à l’installation d’un package dans une bibliothèque de l’utilisateur. Toutefois, cela n’est pas possible dans l’environnement SQL Server. Accès au système de fichiers est généralement limité sur le serveur, et même si vous disposez des droits d’administrateur et l’accès à un dossier de documents utilisateur sur le serveur, l’exécution du script externe qui s’exécute dans SQL Server ne peut pas accéder à tous les packages installés à l’extérieur de l’instance par défaut bibliothèque. Toutefois, les solutions de contournement sont possibles. Pour obtenir des conseils sur la façon de résoudre les problèmes liés aux bibliothèques de l’utilisateur, consultez [solutions de contournement pour les bibliothèques utilisateur R](packages-installed-in-user-libraries.md).

## <a name="next-steps"></a>Étapes suivantes

+ [Obtenir des informations de package](determine-which-packages-are-installed-on-sql-server.md)
+ [Installation de nouveaux packages R](install-additional-r-packages-on-sql-server.md)
+ [Installation de nouveaux packages Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Activer la gestion à distance des packages R](r-package-how-to-enable-or-disable.md)
+ [Fonctions RevoScaleR pour la gestion des packages R](use-revoscaler-to-manage-r-packages.md)
+ [Synchronisation de package de R](package-install-uninstall-and-sync.md)
+ [miniCRAN pour un référentiel de packages R local](create-a-local-package-repository-using-minicran.md)
