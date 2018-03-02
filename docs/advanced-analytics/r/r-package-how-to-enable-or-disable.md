---
title: "Activer ou désactiver la gestion des packages à distance pour SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e384893-04da-43f9-b100-bfe99888f085
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: feb30d37f9c22d6620a7c6a734172ef43c15e253
ms.sourcegitcommit: c08d665754f274e6a85bb385adf135c9eec702eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>Activer ou désactiver la gestion des packages à distance pour SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit comment activer la gestion de packages R à partir d’une instance distante du serveur de Machine Learning. Après avoir activé la fonctionnalité de gestion de package, vous pouvez utiliser les commandes de RevoScaleR pour installer des packages sur une base de données à partir d’un client distant.

> [!NOTE]
> Gestion des bibliothèques R est actuellement pris en charge ; Cette prise en charge de Python sur la feuille de route.

Par défaut, la fonctionnalité de gestion de package externe pour SQL Server est désactivée, même si les fonctionnalités de machine learning ont été installées. Vous devez exécuter un script distinct pour activer la fonctionnalité comme décrit dans la section suivante.

## <a name="overview-of-process-and-tools"></a>Vue d’ensemble des processus et outils

Pour activer ou désactiver la gestion des packages, utilisez l’utilitaire de ligne de commande **RegisterRExt.exe**, qui est inclus dans le **RevoScaleR** package.

[L’activation de](#bkmk_enable) cette fonctionnalité est un processus en deux étapes, en demandant à un administrateur de base de données : vous activer la gestion de package sur l’instance de SQL Server (une fois par instance de SQL Server) et activer la gestion des packages sur la base de données SQL (une fois par SQL Server base de données).

[La désactivation de](#bkmk_disable) la fonctionnalité de gestion de package requiert également multipel étapes : vous supprimez les packages au niveau de la base de données et les autorisations (une fois par base de données), puis supprimez les rôles du serveur (une fois par instance).

## <a name="bkmk_enable"></a> Activer la gestion des packages

1. Ouvrez une invite de commandes avec élévation de privilèges et accédez au dossier contenant l’utilitaire, RegisterRExt.exe. L’emplacement par défaut est `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`.

2. Exécutez la commande suivante, en fournissant des arguments appropriés pour votre environnement :

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Cette commande crée des objets au niveau de l’instance sur l’ordinateur SQL Server qui sont requis pour la gestion des packages. Il redémarre également le Launchpad pour l’instance.

    Si vous ne spécifiez pas une instance, l’instance par défaut est utilisé. Si vous ne spécifiez pas un utilisateur, le contexte de sécurité actuel est utilisé. Par exemple, la commande suivante active la gestion des packages sur l’instance dans le chemin d’accès de RegisterRExt.exe, les informations d’identification de l’utilisateur qui a ouvert l’invite de commandes :

    `REgisterRExt.exe /installpkgmgmt`

3. Pour ajouter la gestion des packages à une base de données spécifique, exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges :

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Cette commande crée certains artefacts de base de données, y compris les rôles de base de données suivants sont utilisés pour contrôler les autorisations d’utilisateur : `rpkgs-users`, `rpkgs-private`, et `rpkgs-shared`.

    Par exemple, la commande suivante active la gestion des packages sur la base de données sur l’instance où RegisterRExt est exécutée. Si vous ne spécifiez pas un utilisateur, le contexte de sécurité actuel est utilisé.

    `RegisterRExt.exe /installpkgmgmt /database:TestDB`

4. Répétez la commande pour chaque base de données où les packages doivent être installés.

5. Pour vérifier que les nouveaux rôles ont été créés avec succès, dans SQL Server Management Studio, cliquez sur la base de données, développez **sécurité**, développez **des rôles de base de données**.

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

Après avoir activé cette fonctionnalité, vous pouvez utiliser RevoScaleR fonction pour installer ou désinstaller des packages à partir d’un client distant de R.

## <a name="bkmk_disable"></a> Désactiver la gestion des packages

1. À partir d’une invite de commandes avec élévation de privilèges, exécutez à nouveau l’utilitaire RegisterRExt et désactiver la gestion de package au niveau de la base de données :

    `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Cette commande supprime les objets de base de données liées à la gestion de package à partir de la base de données spécifié. Elle supprime également tous les packages qui ont été installés à partir de l’emplacement du système de fichiers sécurisé sur l’ordinateur SQL Server.

2. Répétez cette commande sur chaque base de données où la gestion des packages a été utilisée.

3.  (Facultatif) Une fois que toutes les bases de données ont été effacées de packages à l’aide de l’étape précédente, exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges :

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Cette commande supprime la fonctionnalité de gestion de package à partir de l’instance. Vous devrez peut-être redémarrer manuellement le service Launchpad pour voir les modifications.

