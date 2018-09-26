---
title: Extraire, transformer et charger des données sur Linux avec SSIS | Microsoft Docs
description: Cet article décrit les services SQL Server Integration Services (SSIS) pour les ordinateurs Linux
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 01/09/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: d01a53524bf03e0ea8318c41b05b9cc59499de33
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713221"
---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Extraire, transformer et charger des données sur Linux avec SSIS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article décrit comment exécuter les packages SQL Server Integration Services (SSIS) sur Linux. SSIS permet de résoudre les problèmes d’intégration des données complexes en extrayant les données provenant de plusieurs sources et les formats, transformer et de nettoyage des données et de charger les données dans plusieurs destinations. 

Les packages SSIS en cours d’exécution sur Linux peuvent se connecter à Microsoft SQL Server s’exécutant sur Windows en local ou dans le cloud, sur Linux, ou dans Docker. Ils peuvent également vous connecter à la base de données SQL Azure, Azure SQL Data Warehouse, sources de données ODBC, fichiers plats et autres sources de données, y compris les sources de ADO.NET, les fichiers XML et les services OData.

Pour plus d’informations sur les fonctionnalités de SSIS, consultez [SQL Server Integration Services](../integration-services/sql-server-integration-services.md).

## <a name="prerequisites"></a>Prérequis

Pour exécuter des packages SSIS sur un ordinateur Linux, vous devez d’abord installer SQL Server Integration Services. SSIS n’est pas inclus dans l’installation de SQL Server pour les ordinateurs Linux. Pour obtenir des instructions d’installation, consultez [installer SQL Server Integration Services](sql-server-linux-setup-ssis.md).

Vous devez également disposer d’un ordinateur Windows pour créer et gérer des packages. Les outils de conception et de gestion de SSIS sont des applications Windows qui ne sont pas actuellement disponibles pour les ordinateurs Linux. 

## <a name="run-an-ssis-package"></a>Exécuter un package SSIS

Pour exécuter un package SSIS sur un ordinateur Linux, procédez comme suit :

1.  Copiez le package SSIS sur l’ordinateur Linux.
2.  Exécutez la commande suivante :
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="run-an-encrypted-password-protected-package"></a>Exécuter un package chiffré (protégé par mot de passe)
Il existe trois manières d’exécuter un package SSIS qui est chiffré avec un mot de passe :

1.  Définissez la valeur de la variable d’environnement `SSIS_PACKAGE_DECRYPT`, comme illustré dans l’exemple suivant :

    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  Spécifiez le `/de[crypt]` possibilité d’entrer le mot de passe de manière interactive, comme indiqué dans l’exemple suivant :

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de
    
    Enter decryption password:
    ```

3.  Spécifiez le `/de` option pour fournir le mot de passe sur la ligne de commande, comme illustré dans l’exemple suivant. Cette méthode n’est pas recommandée, car elle stocke le mot de passe de déchiffrement avec la commande dans l’historique des commandes.

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test
    
    Warning: Using /De[crypt] <password> may store decryption password in command history.
    
    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

## <a name="design-packages"></a>Concevoir des packages

**Se connecter aux sources de données ODBC**. Avec SSIS lors de l’actualisation de Linux CTP 2.1 et versions ultérieures, les packages SSIS peuvent utiliser des connexions ODBC sur Linux. Cette fonctionnalité a été testée avec le serveur SQL Server et les pilotes ODBC MySQL, mais il est également prévue pour fonctionner avec n’importe quel pilote ODBC Unicode qui observe la spécification ODBC. Au moment du design, vous pouvez fournir une source de données ou une chaîne de connexion pour se connecter aux données ODBC ; Vous pouvez également utiliser l’authentification Windows. Pour plus d’informations, consultez le [billet de blog annonçant prise en charge ODBC sur Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

**Chemins d’accès**. Fournir des chemins d’accès de style de Windows dans vos packages SSIS. SSIS sur Linux ne prend pas en charge les chemins d’accès Linux-style, mais mappe les chemins de style Windows aux chemins d’accès de style de Linux en cours d’exécution. Ensuite, par exemple, SSIS sur Linux mappe le chemin d’accès Windows-style `C:\test` pour le chemin d’accès Linux-style `/test`.

## <a name="deploy-packages"></a>Déployer des packages
Vous pouvez stocker uniquement des packages dans le système de fichiers sur Linux dans cette version. La base de données du catalogue SSIS et le service SSIS hérité ne sont pas disponibles sur Linux pour le déploiement de package et de stockage.

## <a name="schedule-packages"></a>Planifier les packages
Vous pouvez utiliser le système de Linux telles que les outils de planification `cron` pour planifier les packages. Vous ne pouvez pas utiliser l’Agent SQL sur Linux pour planifier l’exécution du package dans cette version. Pour plus d’informations, consultez [packages SSIS de planification sur Linux avec cron](sql-server-linux-schedule-ssis-packages.md).

## <a name="limitations-and-known-issues"></a>Limitations et problèmes connus

Pour obtenir des informations détaillées sur les limitations et problèmes connus de SSIS sur Linux, consultez [Limitations et problèmes connus pour SSIS sur Linux](sql-server-linux-ssis-known-issues.md).

## <a name="more-info-about-ssis-on-linux"></a>Plus d’informations sur Linux

Pour plus d’informations à propos de SSIS sur Linux, consultez les billets de blog suivants :

-   [SSIS sur Linux est disponible dans SQL Server CTP2.1](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC est prise en charge de SSIS sur Linux (actualisation de SQL Server CTP 2.1)](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-info-about-ssis"></a>Plus d’informations sur SSIS

Microsoft SQL Server Integration Services (SSIS) est une plateforme de création de solutions d’intégration de données hautes performances, y compris d’extraction, transformation et chargement (ETL) de packages pour l’entreposage des données. Pour plus d’informations, consultez [SQL Server Integration Services](/sql/integration-services/sql-server-integration-services).

SSIS inclut les fonctionnalités suivantes :
- Outils graphiques et des Assistants pour générer et déboguer des packages sur Windows
- Une variété de tâches pour effectuer des fonctions de flux de travail tels que les opérations FTP, l’exécution d’instructions SQL et envoi de messages électroniques
- Une variété de sources de données et des destinations pour extraction et chargement des données
- Diverses transformations intégrées pour le nettoyage, l’agrégation, la fusion et la copie de données
- Interfaces de programmation de l’application (API) pour l’extension SSIS avec vos propres scripts personnalisés et les composants

Pour bien démarrer avec SSIS, téléchargez la dernière version de [SQL Server Data Tools (SSDT)](../integration-services/ssis-how-to-create-an-etl-package.md).

Pour en savoir plus sur SSIS, consultez les articles suivants :
- [En savoir plus sur SQL Server Integration Services](../integration-services/sql-server-integration-services.md)
- [Outils de gestion et de développement de SQL Server Integration Services (SSIS)](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [Didacticiels pour SQL Server Integration Services](../integration-services/integration-services-tutorials.md)

## <a name="related-content-about-ssis-on-linux"></a>Contenu associé sur SSIS sur Linux
-   [Installer SQL Server Integration Services (SSIS) sur Linux](sql-server-linux-setup-ssis.md)
-   [Configurer SQL Server Integration Services sur Linux avec ssis-conf](sql-server-linux-configure-ssis.md)
-   [Limitations et problèmes connus pour SSIS sur Linux](sql-server-linux-ssis-known-issues.md)
-   [L’exécution sur Linux avec cron du package de planification SQL Server Integration Services](sql-server-linux-schedule-ssis-packages.md)
