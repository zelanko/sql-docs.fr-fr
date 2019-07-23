---
title: Activer ou désactiver la gestion des packages R distants
description: Activer la gestion des packages R distants sur SQL Server 2016 R services ou SQL Server 2017 Machine Learning Services (en base de données)
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 245358dcdc6bb166e49f963f67754f864e1a96b6
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344920"
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>Activer ou désactiver la gestion des packages à distance pour SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article explique comment activer la gestion à distance des packages R à partir d’une station de travail cliente ou d’un autre Machine Learning Server. Une fois la fonctionnalité de gestion des packages activée sur SQL Server, vous pouvez utiliser les commandes RevoScaleR sur un client pour installer des packages sur SQL Server.

> [!NOTE]
> La gestion des bibliothèques R est actuellement prise en charge; la prise en charge de Python se trouve dans la feuille de route.

Par défaut, la fonctionnalité de gestion des packages externes pour SQL Server est désactivée. Vous devez exécuter un script distinct pour activer la fonctionnalité, comme décrit dans la section suivante.

## <a name="overview-of-process-and-tools"></a>Vue d’ensemble du processus et des outils

Pour activer ou désactiver la gestion des packages sur SQL Server, utilisez l’utilitaire de ligne de commande **RegisterRExt. exe**, qui est inclus dans le package **RevoScaleR** .

[L’activation](#bkmk_enable) de cette fonctionnalité est un processus en deux étapes qui requiert un administrateur de base de données: vous activez la gestion des packages sur l’instance de SQL Server (une fois par instance de SQL Server), puis vous activez la gestion des packages sur la base de données SQL (une fois par base de données SQL Server ).

La [désactivation](#bkmk_disable) de la fonctionnalité de gestion des packages requiert également des étapes multipel: vous supprimez des packages et des autorisations au niveau de la base de données (une fois par base de données), puis supprimez les rôles du serveur (une fois par instance).

## <a name="bkmk_enable"></a>Activer la gestion des packages

1. Sur SQL Server, ouvrez une invite de commandes avec élévation de privilèges et accédez au dossier contenant l’utilitaire, RegisterRExt. exe. L’emplacement par défaut `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`est.

2. Exécutez la commande suivante, en fournissant les arguments appropriés pour votre environnement:

    `RegisterRExt.exe /install pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Cette commande crée des objets au niveau de l’instance sur l’ordinateur SQL Server requis pour la gestion des packages. Il redémarre également Launchpad pour l’instance.

    Si vous ne spécifiez pas d’instance, l’instance par défaut est utilisée. Si vous ne spécifiez pas d’utilisateur, le contexte de sécurité actuel est utilisé. Par exemple, la commande suivante active la gestion des packages sur l’instance dans le chemin d’accès de RegisterRExt. exe, à l’aide des informations d’identification de l’utilisateur qui a ouvert l’invite de commandes:

    `REgisterRExt.exe /install pkgmgmt`

3. Pour ajouter la gestion des packages à une base de données spécifique, exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges:

    `RegisterRExt.exe /install pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Cette commande crée des artefacts de base de données, y compris les rôles de base de données suivants utilisés `rpkgs-users`pour `rpkgs-private`le contrôle `rpkgs-shared`des autorisations utilisateur:, et.

    Par exemple, la commande suivante active la gestion des packages sur la base de données, sur l’instance où RegisterRExt est exécuté. Si vous ne spécifiez pas d’utilisateur, le contexte de sécurité actuel est utilisé.

    `RegisterRExt.exe /install pkgmgmt /database:TestDB`

4. Répétez la commande pour chaque base de données sur laquelle les packages doivent être installés.

5. Pour vérifier que les nouveaux rôles ont été créés avec succès, dans SQL Server Management Studio, cliquez sur la base de données, développez **sécurité**, puis développez **rôles de base de données**.

    Vous pouvez également exécuter une requête sur sys. database_principals, comme suit:

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

Une fois cette fonctionnalité activée, vous pouvez utiliser la fonction RevoScaleR pour installer ou désinstaller des packages à partir d’un client R distant.

## <a name="bkmk_disable"></a>Désactiver la gestion des packages

1. À partir d’une invite de commandes avec élévation de privilèges, réexécutez l’utilitaire RegisterRExt et désactivez la gestion des packages au niveau de la base de données:

    `RegisterRExt.exe /uninstall pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Cette commande supprime les objets de base de données liés à la gestion des packages de la base de données spécifiée. Elle supprime également tous les packages qui ont été installés à partir de l’emplacement du système de fichiers sécurisé sur l’ordinateur SQL Server.

2. Répétez cette commande sur chaque base de données où la gestion des packages a été utilisée.

3.  Facultatif Une fois que toutes les bases de données ont été effacées des packages à l’aide de l’étape précédente, exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges:

    `RegisterRExt.exe /uninstall pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Cette commande supprime la fonctionnalité de gestion des packages de l’instance. Vous devrez peut-être redémarrer manuellement le service Launchpad pour voir les modifications.

## <a name="next-steps"></a>Étapes suivantes

+ [Utiliser RevoScaleR pour installer de nouveaux packages R](use-revoscaler-to-manage-r-packages.md)
+ [Conseils pour l’installation de packages R](packages-installed-in-user-libraries.md)
+ [Packages par défaut](../package-management/default-packages.md)
