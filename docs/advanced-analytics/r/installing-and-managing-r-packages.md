---
title: Bibliothèques de package pour l’apprentissage sur SQL Server par défaut | Documents Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 64b085c2314e4c97694e91924cb15d43315143e0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="default-package-libraries-for-machine-learning-on-sql-server"></a>Bibliothèques de package par défaut pour l’apprentissage sur SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit les bibliothèques par défaut pour R et Python est installés avec SQL Server. Cet article fournit les emplacements par défaut de ces bibliothèques et explique comment vous pouvez déterminer les packages et la version de R ou Python est installés dans la bibliothèque de chaque instance.

## <a name="using-the-default-instance-library"></a>À l’aide de la bibliothèque d’instance par défaut

Lorsque vous installez un apprentissage avec SQL Server, une bibliothèque de package unique est créée au niveau de l’instance pour chaque langue que vous installez. SQL Server ne peut pas accéder aux packages installés dans d’autres bibliothèques.

Si vous vous connectez au serveur à partir d’un client distant, tout code de R ou Python que vous souhaitez exécuter dans le contexte de calcul du serveur peut utiliser uniquement les packages installés dans la bibliothèque de l’instance.

Pour protéger des ressources du serveur, la bibliothèque d’instance par défaut est installée dans un dossier sécurisé qui est enregistré avec SQL Server et peut être modifié que par un administrateur de l’ordinateur. Si vous n’êtes pas le propriétaire de l’ordinateur, vous devrez peut-être obtenir l’autorisation d’un administrateur pour installer des packages pour cette bibliothèque. 

Même si vous êtes propriétaire de l’ordinateur, vous devez envisager l’utilité de n’importe quel package R ou Python particulier dans un environnement de serveur avant d’ajouter le package à la bibliothèque de l’instance. Prendre en compte des facteurs tels que la taille des fichiers de package et le besoin de plusieurs versions, ainsi que si le package requiert le réseau ou internet access.

### <a name="sql-server"></a>SQL Server

|Version | Nom de l'instance|Chemin d’accès par défaut|
|------|------|------|
| SQL Server 2016 |instance par défaut|`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`|
| SQL Server 2016 |instance nommée |`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES\library`|
| SQL Server 2017 avec R|instance par défaut |`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library` |
| SQL Server 2017 avec R|instance nommée|`C:\Program Files\Microsoft SQL Server\MSSQL14.MyNamedInstance\R_SERVICES\library` |
| SQL Server 2017 avec Python |instance par défaut |`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\library` |
| SQL Server 2017 avec Python|instance nommée|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES\library` |

### <a name="r-server-standalone-or-machine-learning-server-standalone"></a>R Server (autonome) ou Machine Learning Server (autonome)

Ce tableau répertorie les chemins d’accès par défaut des fichiers binaires lorsque le serveur autonome est installé à l’aide du programme d’installation de SQL Server. 

|Version| Installation|Chemin d’accès par défaut|
|------|------|------|
| SQL Server 2016|R Server (autonome)| |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2017|Apprentissage de serveur, avec R |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2017|Apprentissage de serveur, avec Python |`C:\Program Files\Microsoft SQL Server\130\PYTHON_SERVER`|

Si vous installez Microsoft R Server ou serveur d’apprentissage à l’aide du programme d’installation Windows distinct, les chemins d’accès par défaut sont différents : en général, qui ressemble à `C:\Program Files\Microsoft\R Server\R_SERVER`. Pour plus d'informations, consultez :
 
+ [Installer le serveur d’apprentissage pour Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Installer R Server 9.1 pour Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)

## <a name="what-is-included-in-a-default-installation"></a>Ce qui est inclus dans une installation par défaut

Cette section fournit un résumé des fonctionnalités R ou Python qui sont installés par défaut.

### <a name="default-r-installation-for-sql-server"></a>Installation par défaut R pour SQL Server

Par défaut R **base** packages sont installés. Packages de base incluent des fonctionnalités de base fournies par les packages tels que `stats` et `utils`.

Une installation de base de R inclut également de nombreux exemples de datasets et les outils R standard tels que RGui (un éditeur interactif léger) et RTerm (une invite de commandes R).

Installation de R dans SQL Server 2016 ou SQL Server 2017 inclut également le **RevoScaleR** package et les packages améliorés connexes et les fournisseurs, qui prend en charge des contextes de calcul à distance, diffusion en continu, de l’exécution parallèlement fonction rx, et de nombreuses autres fonctionnalités.

Pour mettre à niveau le package RevoScaleR, soit utiliser la liaison pour mettre à niveau uniquement les composants, d’apprentissage automatique ou de correctif logiciel ou mise à niveau de votre instance vers une version plus récente de SQL Server.

+ Pour une vue d’ensemble des fonctionnalités améliorées de R, consultez [sur le serveur Machine Learning](https://docs.microsoft.com/machine-learning-server/what-is-microsoft-r-server)

+ Pour télécharger les bibliothèques RevoScaleR sur un ordinateur client, installez [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

### <a name="default-python-installation-for-sql-server"></a>Installation de Python pour SQL Server par défaut

Si vous sélectionnez les fonctionnalités et l’option de langage Python d’apprentissage automatique, une distribution Anaconda est installée. La version exacte dépend de la version de SQL Server que vous avez installé et si vous avez mis à niveau l’instance à l’aide du programme d’installation du serveur de Machine Learning.

|Version| Version de anaconda| Autres modifications|
|------|------|------|
| SQL Server 2017 RTM| 3.5.2| Nouveau : revoscalepy|
| mettre à jour via un serveur d’apprentissage Machine 9.2.1 septembre 2017| Anaconda 4.2| mises à jour de revoscalepy |
| SQL Server 2017 CU3| Anaconda 4.2| mises à jour de revoscalepy |

En plus des bibliothèques de code Python, l’installation standard inclut des exemples de données, les tests unitaires et les exemples de scripts.

## <a name="restrictions-and-known-issues"></a>Restrictions et les problèmes connus

Toute solution qui s’exécute dans SQL Server peut utiliser **uniquement** packages qui sont installés dans la bibliothèque par défaut associée à l’instance.

Si vous utilisez la liaison pour mettre à niveau les composants de R dans une instance, le chemin d’accès à la bibliothèque de l’instance peut modifier. Veillez à vérifier le chemin d’accès de la bibliothèque actuellement utilisée par SQL Server.

## <a name="administrative-permissions-required-for-package-installation"></a>Autorisations administratives requises pour l’installation du package

Les autorisations requises pour l’installation du package ont été modifiés entre SQL Server 2016 et SQL Server 2017.

+ Dans SQL Server 2016, un accès administrateur est requis pour l’installation de nouveaux packages R.

+ Dans SQL Server 2017, vous pouvez continuer à installer des packages en tant qu’administrateur pour R et Python, et c’est probablement la méthode la plus simple.

    L’instruction DDL, créer une bibliothèque externe, permet à l’administrateur de base de données installer les packages sans utiliser les outils R. 

    Si vous utilisez la fonctionnalité de gestion de package pour l’apprentissage d’ordinateur serveur, vous pouvez utiliser RevoScaleR pour installer des packages R au niveau de la base de données. L’administrateur de base de données doit activer la fonctionnalité et puis accorder aux utilisateurs la possibilité d’installer leurs propres packages sur une base de chaque base de données. Pour plus d’informations, consultez [activer la gestion des packages à l’aide de la DDL](r-package-how-to-enable-or-disable.md).

### <a name="user-libraries-are-not-supported"></a>Bibliothèques utilisateur ne sont pas pris en charge.

Les utilisateurs qui ne peut pas installer un package dans un emplacement sécurisé souvent recours à l’installation d’un package dans une bibliothèque de l’utilisateur. Toutefois, cela n’est pas possible dans l’environnement SQL Server. Au même système de fichiers est souvent restreint sur le serveur.

Même si vous disposez des droits d’administrateur et l’accès à un dossier de documents utilisateur sur le serveur, l’exécution du script externe qui s’exécute dans SQL Server ne peut pas accéder à tous les packages installés à l’extérieur de la bibliothèque d’instance par défaut.

Pour obtenir des conseils sur la façon de résoudre les problèmes liés aux bibliothèques de l’utilisateur, consultez [Package installé dans les bibliothèques utilisateur](packages-installed-in-user-libraries.md).