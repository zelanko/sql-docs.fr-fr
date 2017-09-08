---
title: "Guide pratique pour activer ou désactiver la gestion des packages R | Microsoft Docs"
ms.custom: 
ms.date: 12/21/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e384893-04da-43f9-b100-bfe99888f085
caps.latest.revision: 7
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aac055d9a2337f1278d648fbcd17435afe1bd3b3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="r-package---how-to-enable-or-disable"></a>Guide pratique pour activer ou désactiver la gestion des packages R

Par défaut, la gestion des packages est désactivée sur une instance de SQL Server, même si R Services est installé. Pour activer cette fonctionnalité, un administrateur de base de données doit effectuer un processus en deux étapes : 

1. Activer la gestion des packages sur l’instance de SQL Server (une fois par instance de SQL Server) 
2. Activer la gestion des packages sur la base de données SQL (une fois par base de données SQL Server) 


Pour désactiver la fonctionnalité de gestion des packages, procédez de manière inverse pour supprimer les autorisations et les packages au niveau de la base de données, puis supprimer les rôles du serveur :
 
1. Désactiver la gestion des packages sur chaque base de données (une fois par base de données) 
2. Désactiver la gestion des packages sur l’instance de SQL Server (une fois par instance) 

> [!IMPORTANT]
> Cette fonctionnalité est en cours de développement. La syntaxe ou les fonctionnalités peuvent changer dans les versions ultérieures. 

### <a name="to-enable-package-management"></a>Pour activer la gestion des packages

L’activation ou la désactivation de la gestion des packages nécessite l’utilitaire de ligne de commande **RegisterRExt.exe**, qui est inclus dans le package **RevoScaleR** installé avec SQL Server R Services. L’emplacement par défaut est :

`<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe` 
    
1. Ouvrez une invite de commandes avec élévation de privilèges et exécutez la commande suivante :

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Cette commande crée sur l’ordinateur SQL Server des artefacts au niveau de l’instance qui sont nécessaires pour la gestion des packages. 

2. Pour ajouter la gestion des packages au niveau de la base de données, pour chaque base de données où des packages doivent être installés, exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges : 

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]` 

    Cette commande crée certains artefacts de base de données, notamment les rôles de base de données suivants nécessaires pour le contrôle des autorisations d’utilisateur : **rpkgs-users**, **rpkgs-private**et **rpkgs-shared** 

### <a name="to-disable-package-management"></a>Pour désactiver la gestion des packages 

1. À partir d’une invite de commandes avec élévation de privilèges, exécutez la commande suivante pour désactiver la gestion des packages au niveau de la base de données :

   `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]` 

    Cette commande supprime de la base de données spécifiée les artefacts de base de données liés à la gestion des packages.  Elle supprime également de l’emplacement du système de fichiers sécurisé sur l’ordinateur SQL Server tous les packages qui ont été installés sur chaque base de données.
    
    Vous devez l’exécuter une seule fois sur chaque base de données où la gestion des packages a été utilisée.
 
2. (Facultatif) Pour supprimer entièrement la fonctionnalité de gestion des packages de l’instance, une fois que les packages ont été effacés de toutes les bases de données lors de l’étape précédente, exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges :

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Cette commande supprime de l’instance de SQL Server les artefacts au niveau de l’instance utilisés par la gestion des packages. 


## <a name="see-also"></a>Voir aussi
[Gestion des packages R pour SQL Server R Services](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md)

