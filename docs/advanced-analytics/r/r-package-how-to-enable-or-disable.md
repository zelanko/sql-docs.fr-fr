---
title: Activer ou désactiver la gestion des packages R à distance - SQL Server Machine Learning Services
description: Activer la gestion à distance des packages R sur SQL Server 2016 R Services ou SQL Server 2017 Machine Learning Services (en base de données)
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: ea567d8fbe3f6bbd9b51133ec015768cd4c6e893
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962528"
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>Activer ou désactiver la gestion des packages à distance pour SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit comment activer la gestion à distance des packages R à partir d’une station de travail cliente ou une autre Machine Learning Server. Après l’activation de la fonctionnalité de gestion de packages sur SQL Server, vous pouvez utiliser les commandes de RevoScaleR sur un client pour installer des packages sur SQL Server.

> [!NOTE]
> Gestion des bibliothèques de R est actuellement pris en charge ; prise en charge Python est sur la feuille de route.

Par défaut, la fonctionnalité de gestion de packages externes pour SQL Server est désactivée. Vous devez exécuter un script distinct pour activer la fonctionnalité comme décrit dans la section suivante.

## <a name="overview-of-process-and-tools"></a>Vue d’ensemble des processus et outils

Pour activer ou désactiver la gestion des packages sur SQL Server, utilisez l’utilitaire de ligne de commande **RegisterRExt.exe**, qui est inclus dans le **RevoScaleR** package.

[L’activation](#bkmk_enable) cette fonctionnalité est un processus en deux étapes, nécessitant un administrateur de base de données : vous activez la gestion des packages sur l’instance de SQL Server (une fois par instance de SQL Server) et activer la gestion des packages sur la base de données SQL (une fois par SQL Server base de données).

[La désactivation de](#bkmk_disable) la fonctionnalité de gestion de packages nécessite également multipel d’étapes : vous supprimer des packages au niveau de la base de données et les autorisations (une fois par base de données), puis supprimez les rôles à partir du serveur (une fois par instance).

## <a name="bkmk_enable"></a> Activer la gestion des packages

1. Sur SQL Server, ouvrez une invite de commandes avec élévation de privilèges et accédez au dossier contenant l’utilitaire, RegisterRExt.exe. L’emplacement par défaut est `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`.

2. Exécutez la commande suivante, en fournissant des arguments appropriés pour votre environnement :

    `RegisterRExt.exe /install pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Cette commande crée des objets au niveau de l’instance sur l’ordinateur SQL Server qui sont requis pour la gestion des packages. Il redémarre également le Launchpad pour l’instance.

    Si vous ne spécifiez pas une instance, l’instance par défaut est utilisé. Si vous ne spécifiez pas un utilisateur, le contexte de sécurité actuel est utilisé. Par exemple, la commande suivante active la gestion des packages sur l’instance dans le chemin d’accès de RegisterRExt.exe, les informations d’identification de l’utilisateur qui a ouvert l’invite de commandes :

    `REgisterRExt.exe /install pkgmgmt`

3. Pour ajouter la gestion des packages à une base de données spécifique, exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges :

    `RegisterRExt.exe /install pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Cette commande crée certains artefacts de base de données, y compris les rôles de base de données suivants sont utilisés pour contrôler les autorisations utilisateur : `rpkgs-users`, `rpkgs-private`, et `rpkgs-shared`.

    Par exemple, la commande suivante active la gestion des packages sur la base de données sur l’instance sur laquelle RegisterRExt est exécuté. Si vous ne spécifiez pas un utilisateur, le contexte de sécurité actuel est utilisé.

    `RegisterRExt.exe /install pkgmgmt /database:TestDB`

4. Répétez la commande pour chaque base de données où les packages doivent être installés.

5. Pour vérifier que les nouveaux rôles ont été correctement créées, dans SQL Server Management Studio, cliquez sur la base de données, développez **sécurité**et développez **les rôles de base de données**.

    Vous pouvez également exécuter une requête sur sys.database_principals tels que les éléments suivants :

    ```sql
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

Une fois que vous avez activé cette fonctionnalité, vous pouvez utiliser la fonction RevoScaleR pour installer ou désinstaller des packages à partir d’un client de R à distance.

## <a name="bkmk_disable"></a> Désactiver la gestion des packages

1. À partir d’une invite de commandes avec élévation de privilèges, exécutez l’utilitaire RegisterRExt à nouveau et désactiver la gestion des packages au niveau de la base de données :

    `RegisterRExt.exe /uninstall pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Cette commande supprime les objets de base de données liés à la gestion de package à partir de la base de données spécifié. Elle supprime également tous les packages qui ont été installés à partir de l’emplacement du système de fichiers sécurisé sur l’ordinateur SQL Server.

2. Répétez cette commande sur chaque base de données où la gestion des packages a été utilisée.

3.  (Facultatif) Une fois que toutes les bases de données ont été effacées de packages à l’aide de l’étape précédente, exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges :

    `RegisterRExt.exe /uninstall pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Cette commande supprime la fonctionnalité de gestion de packages à partir de l’instance. Vous devrez peut-être redémarrer manuellement le service Launchpad une fois de plus pour voir les modifications.

## <a name="next-steps"></a>Étapes suivantes

+ [RevoScaleR permet d’installer de nouveaux packages R](use-revoscaler-to-manage-r-packages.md)
+ [Conseils pour l’installation des packages R](packages-installed-in-user-libraries.md)
+ [Packages par défaut](../package-management/default-packages.md)
