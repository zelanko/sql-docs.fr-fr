---
title: "Packages R sont installés avec SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 082aea3b1cde3c335dd7fa51b8ef219fc30f7efd
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2018
---
# <a name="r-packages-installed-with-sql-server"></a>Packages R sont installés avec SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit les packages R sont installés avec SQL Server si vous installez et activez les fonctionnalités de machine learning. Cet article décrit également comment gérer et afficher les packages existants ou ajouter de nouveaux packages à une instance de SQL Server.

**S’applique à :** SQL Server 2017 Machine Learning Services (de-de base de données), SQL Server 2016 R Services (de-de base de données)

## <a name="what-is-the-instance-library-and-where-is-it"></a>Quelle est la bibliothèque de l’instance et où il est ?

Une solution R qui s’exécute dans SQL Server peut utiliser uniquement les packages qui sont installés dans la bibliothèque de R par défaut associée à l’instance. Lorsque vous installez des fonctionnalités de R dans SQL Server, la bibliothèque de package de R se trouve sous le dossier de l’instance.

+ Instance par défaut *MSSQLSERVER* 

    SQL Server 2017 :`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library` 
    
    SQL Server 2016 :`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`

+ Instance nommée *MyNamedInstance* 

    SQL Server 2017 :`C:\Program Files\Microsoft SQL Server\MSSQL14.MyNamedInstance\R_SERVICES\library` 
    
    SQL Server 2016 :`C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library`

Vous pouvez exécuter l’instruction suivante pour déterminer la bibliothèque par défaut pour l’instance actuelle de R.

```sql
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Enfin, vous pouvez utiliser la nouvelle [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) de fonction, si l’exécution de sp\_exécuter\_externe\_script directement sur l’ordinateur cible. La fonction ne peut pas retourner des chemins d’accès de bibliothèque pour les connexions distantes.

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
```

> [!NOTE]
> Si vous utilisez la liaison pour mettre à niveau les composants de R dans une instance, le chemin d’accès à la bibliothèque de l’instance peut modifier. Veillez à vérifier la bibliothèque qui est utilisé par SQL Server.

## <a name="r-packages-installed-with-sql-server"></a>Packages R sont installés avec SQL Server

Par défaut R **base** packages sont installés. Packages de base incluent des fonctionnalités de base fournies par les packages tels que `stats` et `utils`.

Installation de R dans SQL Server 2016 ou SQL Server 2017 toujours inclut le **RevoScaleR** package et les packages améliorés connexes et les fournisseurs, qui prend en charge des contextes de calcul à distance, diffusion en continu, de l’exécution parallèlement fonction rx, et de nombreuses autres fonctionnalités. Pour mettre à niveau le package RevoScaleR, soit utiliser la liaison pour mettre à niveau uniquement les composants, d’apprentissage automatique ou de correctif logiciel ou mise à niveau de votre instance vers une version plus récente de SQL Server.

+ Pour une vue d’ensemble des fonctionnalités améliorées de R, consultez [sur le serveur Machine Learning](https://docs.microsoft.com/machine-learning-server/what-is-microsoft-r-server)

+ Pour télécharger les bibliothèques RevoScaleR sur un ordinateur client, installez [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

## <a name="permissions-required-for-installing-r-packages"></a>Autorisations requises pour l’installation des packages R

Dans SQL Server 2016, un administrateur devait installer de nouveaux packages R sur une instance à l’échelle. 

SQL Server 2017 a introduit de nouvelles fonctionnalités de gestion et d’installation du package :

+ Vous pouvez utiliser les commandes de R à partir d’un client distant pour installer des packages à l’aide de la portée privée ou partagée. Cette fonctionnalité nécessite [Microsoft R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install) ou [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), ainsi que des privilèges dbo sur l’instance.
+ Nouvelles fonctionnalités de base de données ont été ajoutées pour prendre en charge la gestion des packages par les administrateurs de base de données sans l’aide de T-SQL. À l’avenir, ces fonctionnalités offrent des bases de données avec la possibilité de déléguer la plupart des facettes de gestion des packages aux utilisateurs privilégiés.

Cette section décrit les autorisations requises pour installer et gérer des packages par version.

+ SQL Server 2016 R Services (de-de base de données)

    Pour installer un nouveau package de R sur un ordinateur qui est en cours d’exécution [!INCLUDE [ssCurrent](..\..\includes\sscurrent-md.md)], vous devez disposer des droits d’administration sur l’ordinateur. Il s’agit de la tâche de l’administrateur de base de données ou un autre administrateur sur le serveur pour vous assurer que tous les packages requis sont installés sur le [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] instance.

    Si vous n’avez pas des privilèges d’administrateur sur l’ordinateur qui héberge le [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] instance, vous pouvez fournir aux informations administrateur sur la façon d’installer des packages R et fournir un accès à un référentiel de packages sécurisé où les packages demandé par les utilisateurs peuvent être obtenues.

+ SQL Server 2017 Machine Learning Services

    Si vous êtes un administrateur sur l’instance de SQL Server, vous pouvez installer de nouveaux packages à volonté. Veillez à utiliser la bibliothèque par défaut qui est associée à l’instance. Impossible d’exécuter les packages installés dans d’autres emplacements lorsqu’elle est appelée à partir d’une procédure stockée. Tout code R qui s’exécute à l’aide de SQL Server en tant que contexte de calcul nécessite également que les packages soient disponibles dans la bibliothèque de l’instance.

    Cette version inclut également de nouvelles fonctionnalités prévues pour prendre en charge la gestion des packages plus facile par les bases de données dans une version ultérieure. Pour l’instant, nous vous conseillons de continuer à installer des packages R sur une instance à l’échelle.

+ R Server (autonome)

    Vous avez besoin des droits d’administration sur l’ordinateur pour installer de nouveaux packages R.

+ Autres environnements de clients

    Si vous installez un nouveau package de R sur un ordinateur qui est utilisé comme une station de travail R et que l’ordinateur n’a **pas** avoir une instance de [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] installé, vous devez toujours des droits d’administration sur l’ordinateur à Installez le package. Après avoir installé le package, vous pouvez l’exécuter localement.

## <a name="managing-or-viewing-installed-packages"></a>Gérer ou afficher les packages installés

Il existe plusieurs méthodes que vous pouvez obtenir une liste complète des packages actuellement installés. Pour plus d’informations, consultez [déterminer les packages installés sur SQL Server](determine-which-packages-are-installed-on-sql-server.md).
