---
title: "Packages R sont installés avec SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6fa079ca7cb13a3fcae98c768f5961f59e5ec37f
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="r-packages-installed-with-sql-server"></a>Packages R sont installés avec SQL Server

Cet article décrit les packages R installés avec SQL Server et fournit des informations sur la façon de gérer et afficher les packages existants.

Cet article fournit également des liens vers des informations sur la façon d’ajouter de nouveaux packages pour une utilisation avec SQL Server.

**S’applique à :** SQL Server 2017 Machine Learning Services (de-de base de données), SQL Server 2016 R Services (de-de base de données)

## <a name="what-is-the-instance-library-and-where-is-it"></a>Quelle est la bibliothèque de l’instance et où il est ?

Une solution R qui s’exécute dans SQL Server peut utiliser uniquement les packages qui sont installés dans la bibliothèque de R par défaut associée à l’instance.

Lorsque vous installez des fonctionnalités de R dans SQL Server, la bibliothèque de package de R se trouve sous le dossier de l’instance.

+ Instance par défaut *MSSQLSERVER* 

    SQL Server 2017 :`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library` 
    
    SQL Server 2016 :`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`

+ Instance nommée *MyNamedInstance* 

    SQL Server 2017 :`C:\Program Files\Microsoft SQL Server\MSSQL14.MyNamedInstance\R_SERVICES\library` 
    
    SQL Server 2016 :`C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library`

Vous pouvez exécuter l’instruction suivante pour déterminer la bibliothèque par défaut pour l’instance actuelle de R.

```SQL
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```
## <a name="r-packages-installed-with-sql-server"></a>Packages R sont installés avec SQL Server

Lorsque vous installez le langage R dans SQL Server, par défaut R **base** packages sont installés. Packages de base incluent des fonctionnalités de base fournies par les packages tels que `stats` et `utils`.

Installation de R dans SQL Server 2016 et SQL Server 2017 inclut également le **RevoScaleR** package et les packages améliorés connexes et les fournisseurs, qui prend en charge des contextes de calcul à distance, diffusion en continu, de l’exécution parallèlement fonction rx, et de nombreuses autres fonctionnalités.

+ Pour une vue d’ensemble des fonctionnalités améliorées de R, consultez [sur le serveur Machine Learning](https://docs.microsoft.com/r-server/what-is-microsoft-r-server)

+ Pour télécharger les bibliothèques RevoScaleR sur un ordinateur client, installez [Microsoft R Client](https://docs.microsoft.com/r-server/r-client/what-is-microsoft-r-client)

## <a name="permissions-required-for-installing-r-packages"></a>Autorisations requises pour l’installation des packages R

Dans SQL Server 2016, un administrateur devait installer de nouveaux packages R sur une instance à l’échelle. Dans SQL Server 2017, les nouvelles fonctionnalités de base de données ont été ajoutées qui donner la possibilité de déléguer la gestion des packages aux utilisateurs sélectionnés à l’administrateur de base de données.

Cette section décrit les autorisations requises pour installer et gérer des packages par version.

+ SQL Server 2016 R Services (de-de base de données)

    Pour installer un nouveau package de R sur un ordinateur qui est en cours d’exécution [!INCLUDE [ssCurrent](..\..\includes\sscurrent-md.md)], vous devez disposer des droits d’administration sur l’ordinateur. Il s’agit de la tâche de l’administrateur de base de données ou un autre administrateur sur le serveur pour vous assurer que tous les packages requis sont installés sur le [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] instance.

    Si vous n’avez pas des privilèges d’administrateur sur l’ordinateur qui héberge le [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] instance, vous pouvez fournir aux informations administrateur sur la façon d’installer des packages R et fournir un accès à un référentiel de packages sécurisé où les packages demandé par les utilisateurs peuvent être obtenues.

+ SQL Server 2017 Machine Learning Services

    Cette version inclut des fonctions de gestion de package qui permettent de déléguer les droits d’installation de package aux utilisateurs sélectionnés administrateur de base de données. Si cette fonctionnalité a été activée, demander que votre administrateur de base de données vous ajouter à un des nouveaux rôles de package. Pour plus d’informations, consultez [gestion des packages R pour SQL Server](r-package-management-for-sql-server-r-services.md).

    Si vous êtes un administrateur sur l’instance de SQL Server, vous pouvez installer de nouveaux packages à volonté. Veillez à utiliser la bibliothèque par défaut qui est associée à l’instance. Impossible d’exécuter les packages installés dans d’autres emplacements lorsqu’elle est appelée à partir d’une procédure stockée. Tout code R qui s’exécute à l’aide de SQL Server en tant que contexte de calcul nécessite également que les packages soient disponibles dans la bibliothèque de l’instance.

+ R Server (autonome)

    Vous avez besoin des droits d’administration sur l’ordinateur pour installer de nouveaux packages R.

+ Autres environnements de clients

    Si vous installez un nouveau package de R sur un ordinateur qui est utilisé comme une station de travail R et que l’ordinateur n’a **pas** avoir une instance de [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)] installé, vous devez toujours des droits d’administration sur l’ordinateur à Installez le package. Après avoir installé le package, vous pouvez l’exécuter localement.

## <a name="managing-or-viewing-installed-packages"></a>Gérer ou afficher les packages installés

Il existe plusieurs méthodes que vous pouvez obtenir une liste complète des packages actuellement installés. Pour plus d’informations, consultez [déterminer les packages installés sur SQL Server](determine-which-packages-are-installed-on-sql-server.md).
