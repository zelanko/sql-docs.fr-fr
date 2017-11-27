---
title: "Activer ou désactiver la gestion des packages R pour SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e384893-04da-43f9-b100-bfe99888f085
caps.latest.revision: "7"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fd19bc25e1e4602a54bf89e18c8959a282552f63
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="enable-or-disable-r-package-management-for-sql-server"></a>Activer ou désactiver la gestion des packages R pour SQL Server

Cet article décrit le processus d’activation ou désactivation de la nouvelle fonctionnalité de gestion de package dans SQL Server 2017. Cette fonctionnalité permet à l’administrateur de base de données contrôler l’installation du package sur l’instance. La fonction s’appuie sur les nouveaux rôles de base de données à accorder aux utilisateurs la possibilité d’installer les packages R que dont ils ont besoin, ou partager les packages avec d’autres utilisateurs.

Par défaut, la fonctionnalité de gestion de package externe pour SQL Server est désactivée, même si les fonctionnalités de machine learning ont été installées.

Pour [activer](#bkmk_enable) cette fonctionnalité est un processus en deux étapes et nécessite d’aide à partir d’un administrateur de base de données :

1.  Activer la gestion des packages sur l’instance de SQL Server (une fois par instance de SQL Server)

2.  Activer la gestion des packages sur la base de données SQL (une fois par base de données SQL Server)

Pour [désactiver](#bkmk_disable) la fonctionnalité de gestion de package, inverser le processus de suppression des packages au niveau de la base de données et les autorisations, puis supprimez les rôles du serveur :

1.  Désactiver la gestion des packages sur chaque base de données (une fois par base de données)

2.  Désactiver la gestion des packages sur l’instance de SQL Server (une fois par instance)

## <a name="bkmk_enable"></a>Activer la gestion des packages

Pour activer ou désactiver la gestion de packages nécessite l’utilitaire de ligne de commande **RegisterRExt.exe**, qui est inclus dans le **RevoScaleR** package.

1. Ouvrez une invite de commandes avec élévation de privilèges et accédez au dossier contenant l’utilitaire, RegisterRExt.exe. L’emplacement par défaut est `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`.

2. Exécutez la commande suivante, en fournissant des arguments approprié pour votre environnement :

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Cette commande crée des objets au niveau de l’instance sur l’ordinateur SQL Server qui sont requis pour la gestion des packages. Il redémarre également le Launchpad pour l’instance.

    Si vous ne spécifiez pas une instance, l’instance par défaut est utilisé.

    Si vous ne spécifiez pas un utilisateur, le contexte de sécurité actuel est utilisé.

2.  Pour ajouter la gestion des packages au niveau de la base de données, exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges :

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Cette commande crée certains artefacts de base de données, y compris les rôles de base de données suivants sont utilisés pour contrôler les autorisations d’utilisateur : `rpkgs-users`, `rpkgs-private`, et `rpkgs-shared`.

    Si vous ne spécifiez pas un utilisateur, le contexte de sécurité actuel est utilisé.

3. Répétez la commande pour chaque base de données où les packages doivent être installés.

4.  Pour vérifier que les nouveaux rôles ont été créés avec succès, dans SQL Server Management Studio, cliquez sur la base de données, développez **sécurité**, développez **des rôles de base de données**.

    Vous pouvez également exécuter une requête sur sys.database_principals tels que les éléments suivants :

    ```SQL
    SELECT pr.principal_id, pr.name, pr.type_desc,   
        pr.authentication_type_desc, pe.state_desc,   
        pe.permission_name, s.name + '.' + o.name AS ObjectName  
    FROM sys.database_principals AS pr  
    JOIN sys.database_permissions AS pe  
        ON pe.grantee_principal_id = pr.principal_id  
    JOIN sys.objects AS o  
        ON pe.major_id = o.object_id  
    JOIN sys.schemas AS s  
        ON o.schema_id = s.schema_id;
    ```

4.  Une fois que la fonctionnalité a été activée, tout utilisateur disposant des autorisations appropriées peut utiliser le [créer une bibliothèque externe](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) instruction T-SQL pour ajouter des packages. Pour obtenir un exemple de fonctionnement, consultez [installer des packages supplémentaires sur SQL Server](install-additional-r-packages-on-sql-server.md).

## <a name="bkmk_disable"></a>Désactiver la gestion des packages

1.  À partir d’une invite de commandes avec élévation de privilèges, exécutez la commande suivante pour désactiver la gestion des packages au niveau de la base de données :

    `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Exécutez cette commande une fois pour chaque base de données où la gestion des packages a été utilisée. Cette commande va supprimer les objets de base de données liées à la gestion de package à partir de la base de données spécifié. Elle supprime également tous les packages qui ont été installés à partir de l’emplacement du système de fichiers sécurisé sur l’ordinateur SQL Server.

2.  (Facultatif) Une fois que toutes les bases de données ont été effacées de packages à l’aide de l’étape précédente, exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges :

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Cette commande supprime la fonctionnalité de gestion de package à partir de l’instance.

## <a name="see-also"></a>Voir aussi

[Gestion des packages R pour SQL Server](r-package-management-for-sql-server-r-services.md)
