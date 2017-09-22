---
title: "Extraire, transformer et charger des données sur Linux avec SSIS | Documents Microsoft"
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9dab69c7-73af-4340-aef0-de057356b791
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 736b7e0744a95d859bd25a6c7974dc13e79d4bb7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/21/2017

---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Extraire, transformer et charger des données sur Linux avec SSIS

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Cette rubrique décrit comment exécuter les packages SQL Server Integration Services (SSIS) sur Linux. SSIS résout les problèmes d’intégration de données complexes en chargement des données à partir de plusieurs sources et de formats, transformation et de nettoyage des données et de mise à jour de plusieurs destinations. 

Les packages SSIS en cours d’exécution sur Linux peuvent se connecter à Microsoft SQL Server est en cours d’exécution sur Windows local ou dans le cloud, sur Linux, ou dans Docker. Ils peuvent également se connecter à la base de données SQL Azure, Azure SQL Data Warehouse et sources de données ODBC.

Vous pouvez utiliser SSIS pour exécuter des packages sur Linux quand vous avez également un ordinateur Windows pour créer et gérer des packages. Les outils de conception et de gestion de SSIS sont des applications Windows. 

## <a name="prerequisites"></a>Conditions préalables

Pour exécuter des packages SSIS sur un ordinateur Linux, vous devez d’abord installer SQL Server Integration Services. Pour obtenir des instructions d’installation, consultez [installer SQL Server Integration Services](sql-server-linux-setup-ssis.md).

## <a name="run-an-ssis-package"></a>Exécutez un package SSIS

Pour exécuter un package SSIS sur un ordinateur Linux, procédez comme suit :

1.  Copiez le package SSIS sur l’ordinateur Linux.
2.  Exécutez la commande suivante :
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="more-about-ssis-on-linux"></a>En savoir plus sur SSIS sur Linux

**Connexions ODBC**. SSIS lors de l’actualisation de Linux CTP 2.1 et versions ultérieures, les packages SSIS permet les connexions ODBC sur Linux. Cette fonctionnalité a été testée avec les pilotes ODBC MySQL sur le serveur SQL Server, mais il est également prévue pour fonctionner avec n’importe quel pilote ODBC Unicode qui respecte la spécification ODBC. Au moment du design, vous pouvez fournir une source de données ou une chaîne de connexion pour se connecter aux données ODBC ; Vous pouvez également utiliser l’authentification Windows. Pour plus d’informations, consultez la [blog de l’annonce prise en charge d’ODBC sur Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

**Chemins d’accès**. SSIS sur Linux ne prend pas en charge les chemins d’accès de type Linux, mais mappe les chemins d’accès de type Windows aux chemins d’accès de type Linux en cours d’exécution. Spécifiez les chemins d’accès de type Windows dans vos packages SSIS. Ensuite, par exemple, SSIS sur Linux mappe le chemin d’accès de type Windows `C:\test` pour le chemin d’accès de type Linux `/test`.

**Déploiement de packages**. Vous ne pouvez stocker des packages dans le système de fichiers sur Linux dans cette version. La base de données du catalogue SSIS et le service SSIS hérité ne sont pas disponibles sur Linux pour le stockage et le déploiement du package.

**Planification de packages**. Vous ne pouvez pas utiliser l’Agent SQL sur Linux pour planifier l’exécution du package dans cette version.

**Autres limitations et les problèmes connus**. Les fonctionnalités suivantes ne sont pas pris en charge dans cette version lorsque vous exécutez des packages SSIS sur Linux :
  - Base de données du catalogue SSIS
  - Exécution du package planifiés par l’Agent SQL
  - Authentification Windows
  - Les composants tiers
  - Capture de données modifiées (CDC)
  - Avec montée en puissance SSIS
  - Azure Feature Pack pour SSIS
  - Prise en charge de Hadoop et HDFS
  - Microsoft Connector pour SAP BW

Pour les autres limitations et problèmes connus avec SSIS sur Linux, consultez le [Notes de publication](sql-server-linux-release-notes.md#ssis).

Pour plus d’informations sur SSIS sur Linux, consultez les billets de blog suivants :

-   [SSIS sur Linux n’est disponible dans SQL Server 2017 CTP2.1](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC est pris en charge dans SSIS sur Linux (SQL Server 2017 CTP 2.1 Actualiser)](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-about-ssis"></a>En savoir plus sur SSIS

Microsoft SQL Server Integration Services (SSIS) est une plate-forme de création de solutions d’intégration de données hautes performances, y compris l’extraction, transformation et chargement (ETL) de packages pour l’entreposage des données. Pour plus d’informations, consultez [SQL Server Integration Services](/sql/integration-services/sql-server-integration-services.md).

SSIS inclut les fonctionnalités suivantes :
- outils graphiques et des Assistants pour générer et déboguer des packages sur Windows
- une variété de tâches pour effectuer des fonctions de flux de travail tels que les opérations FTP, exécution d’instructions SQL et envoi de messages électroniques
- une variété de sources de données et des destinations pour l’extraction et chargement des données
- différentes transformations pour le nettoyage, l’agrégation, la fusion et la copie de données
- interfaces de programmation d’application (API) pour l’extension SSIS avec vos propres scripts personnalisés et les composants

Pour commencer avec SSIS, téléchargez la dernière version de [SQL Server Data Tools (SSDT)](/sql-docs/docs/integration-services/ssis-how-to-create-an-etl-package).

## <a name="see-also"></a>Voir aussi
- [En savoir plus sur SQL Server Integration Services](/sql-docs/docs/integration-services/sql-server-integration-services)
- [Développement de SQL Server Integration Services (SSIS) et les outils de gestion](/sql-docs/docs/integration-services/integration-services-ssis-development-and-management-tools)
- [Didacticiels sur SQL Server Integration Services](/sql-docs/docs/integration-services/integration-services-tutorials)

