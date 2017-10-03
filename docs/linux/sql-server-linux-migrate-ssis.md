---
title: "Extraire, transformer et charger des données sur Linux avec SSIS | Documents Microsoft"
description: 
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9dab69c7-73af-4340-aef0-de057356b791
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: aa4ac0cca739ea57a28beb399325d55b38502217
ms.contentlocale: fr-fr
ms.lasthandoff: 10/02/2017

---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>Extraire, transformer et charger des données sur Linux avec SSIS

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Cette rubrique décrit comment exécuter les packages SQL Server Integration Services (SSIS) sur Linux. SSIS permet de résoudre des problèmes d’intégration des données complexes en extrayant les données à partir de plusieurs sources et de formats, transformation et de nettoyage des données et de charger les données dans plusieurs destinations. 

Les packages SSIS en cours d’exécution sur Linux peuvent se connecter à Microsoft SQL Server est en cours d’exécution sur Windows local ou dans le cloud, sur Linux, ou dans Docker. Ils peuvent également se connecter à la base de données SQL Azure, Azure SQL Data Warehouse, les sources de données ODBC, fichiers plats et autres sources de données, y compris les sources de ADO.NET, les fichiers XML et les services OData.

Pour plus d’informations sur les fonctionnalités de SSIS, consultez [SQL Server Integration Services](../integration-services/sql-server-integration-services.md).

## <a name="prerequisites"></a>Conditions préalables

Pour exécuter des packages SSIS sur un ordinateur Linux, vous devez d’abord installer SQL Server Integration Services. SSIS n’est pas inclus dans l’installation de SQL Server pour les ordinateurs Linux. Pour obtenir des instructions d’installation, consultez [installer SQL Server Integration Services](sql-server-linux-setup-ssis.md).

Vous devez également disposer d’un ordinateur Windows pour créer et gérer des packages. Les outils de conception et de gestion de SSIS sont des applications Windows qui ne sont pas actuellement disponibles pour les ordinateurs Linux. 

## <a name="run-an-ssis-package"></a>Exécutez un package SSIS

Pour exécuter un package SSIS sur un ordinateur Linux, procédez comme suit :

1.  Copiez le package SSIS sur l’ordinateur Linux.
2.  Exécutez la commande suivante :
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="other-common-ssis-tasks"></a>Autres tâches courantes de SSIS

-   **Concevoir des packages**.

    -   **Se connecter aux sources de données ODBC**. SSIS lors de l’actualisation de Linux CTP 2.1 et versions ultérieures, les packages SSIS permet les connexions ODBC sur Linux. Cette fonctionnalité a été testée avec les pilotes ODBC MySQL sur le serveur SQL Server, mais il est également prévue pour fonctionner avec n’importe quel pilote ODBC Unicode qui respecte la spécification ODBC. Au moment du design, vous pouvez fournir une source de données ou une chaîne de connexion pour se connecter aux données ODBC ; Vous pouvez également utiliser l’authentification Windows. Pour plus d’informations, consultez la [blog de l’annonce prise en charge d’ODBC sur Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

    -   **Chemins d’accès**. Spécifiez les chemins d’accès de type Windows dans vos packages SSIS. SSIS sur Linux ne prend pas en charge les chemins d’accès de type Linux, mais mappe les chemins d’accès de type Windows aux chemins d’accès de type Linux en cours d’exécution. Ensuite, par exemple, SSIS sur Linux mappe le chemin d’accès de type Windows `C:\test` pour le chemin d’accès de type Linux `/test`.

-   **Déployer des packages**. Vous ne pouvez stocker des packages dans le système de fichiers sur Linux dans cette version. La base de données du catalogue SSIS et le service SSIS hérité ne sont pas disponibles sur Linux pour le stockage et le déploiement du package.

-   **Planifier les packages**. Vous pouvez utiliser le système Linux tels que les outils de planification `cron` pour planifier les packages. Vous ne pouvez pas utiliser l’Agent SQL sur Linux pour planifier l’exécution du package dans cette version. Pour plus d’informations, consultez [packages SSIS de planification sur Linux avec cron](sql-server-linux-schedule-ssis-packages.md).

## <a name="limitations-and-known-issues"></a>Limitations et problèmes connus

### <a name="general-limitations-and-known-issues"></a>Limitations générales et les problèmes connus

Les fonctionnalités suivantes ne sont pas pris en charge dans cette version de SSIS sur Linux :
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

### <a name="components"></a>Composants pris en charge et non pris en charge

Les composants Integration Services intégrés suivants sont pris en charge sous Linux. Certaines d'entre elles ont des limitations sur la plate-forme Linux, comme décrit dans les tableaux suivants.

Les composants intégrés qui ne sont pas répertoriés ici ne sont pas pris en charge sous Linux.

#### <a name="supported-control-flow-tasks"></a>Prise en charge des tâches de flux de contrôle
- tâche d'insertion en bloc
- tâche de flux de données
- Tâche de profilage des données
- Tache d'exécution de requêtes SQL
- Tâche Exécuter l'instruction T-SQL
- Tâche d'expression
- Tâche FTP
- Tâche de service Web
- Tâche XML

#### <a name="control-flow-tasks-supported-with-limitations"></a>Tâches de flux de contrôle pris en charge avec les limitations

| Tâche | Limitations |
|------------|---|
| Exécuter la tâche de processus | Prend uniquement en charge le mode in-process. |
| Tâche de système de fichiers | Le *répertoire de déplacement* et *définir les attributs de fichier* actions ne sont pas prises en charge. |
| tâche de script | Prend uniquement en charge les API .NET Framework standard. |
| tache Envoyer un message | Prend en charge uniquement en mode utilisateur anonyme. |
| Tâche de transfert de base de données | Les chemins d'accès UNC ne sont pas pris en charge. |
| | |

#### <a name="supported-control-flow-containers"></a>Prise en charge des conteneurs de flux de contrôle
- conteneur de séquences
- Conteneur de boucles For
- Conteneur de boucles Foreach

#### <a name="supported-data-flow-sources-and-destinations"></a>Sources de flux de données pris en charge et des destinations
- Destination et source de fichier brut
- Source XML

#### <a name="data-flow-sources-and-destinations-supported-with-limitations"></a>Sources de flux de données et des destinations prises en charge avec les limitations

| Composant | Limitations |
|------------|---|
| ADO.NET source et destination | Prennent uniquement en charge le fournisseur de données SQLClient. |
| Source de fichier plat et de destination | Prend en charge uniquement les chemins de fichier Windows de style, auquel la règle de mappage du chemin d’accès par défaut est appliquée. Par exemple `D:\home\ssis\travel.csv` devient `/home/ssis/travel.csv`. |
| Source OData | Prend uniquement en charge l’authentification de base. |
| ODBC source et destination | Prend en charge des pilotes ODBC Unicode de 64 bits sur Linux. Varie selon le Gestionnaire de pilotes UnixODBC sur Linux. |
| OLE DB source et destination | Prennent uniquement en charge SQL Server Native Client 11.0 et le fournisseur Microsoft OLE DB pour SQL Server. |
| | |

#### <a name="supported-data-flow-transformations"></a>Prise en charge les transformations du flux de données
- Agrégat
- Audit
- Distributeur de données équilibrées
- Table des caractères
- Fractionnement conditionnel
- Copie de colonnes
- Conversion de données
- Colonne dérivée
- Exportation de colonne
- Regroupement probable
- Recherche floue
- Importation de colonne
- Lookup
- Fusion
- Merge Join
- Multidiffusion
- Tableau croisé dynamique
- Nombre de lignes
- Dimension à variation lente
- Trier
- Recherche de terme
- Union All
- Supprimer le tableau croisé dynamique

#### <a name="data-flow-transformations-supported-with-limitations"></a>Transformations du flux de données pris en charge avec les limitations

| Composant | Limitations |
|------------|---|
| transformation de commande OLE DB | Mêmes limitations que OLE DB source et de destination. |
| composant Script | Prend uniquement en charge les API .NET Framework standard. |
| | |

### <a name="supported-and-unsupported-log-providers"></a>Modules fournisseurs d’informations de prise en charge et non pris en charge
Tous les modules fournisseurs d’informations SSIS intégrées sont prises en charge sous Linux, sauf le fournisseur du journal des événements Windows.

Le fournisseur de journaux SQL Server prend en charge uniquement l’authentification SQL ; Il ne prend pas en charge l’authentification Windows.

Les fournisseurs de journal SSIS pour SQL Server Profiler pour les fichiers texte et pour les fichiers XML enregistrent leur sortie dans un fichier que vous spécifiez. Les considérations suivantes s’appliquent au chemin de fichier :
-   Si vous ne fournissez pas un chemin d’accès, le fournisseur de journaux est écrit dans le répertoire actuel de l’hôte. Si l’utilisateur actuel n’est pas autorisé à écrire dans le répertoire actuel de l’hôte, le fournisseur de journaux génère une erreur.
-   Vous ne pouvez pas utiliser une variable d’environnement dans un chemin d’accès de fichier. Si vous spécifiez une variable d’environnement, le texte littéral que vous spécifiez s’affiche dans le chemin d’accès de fichier. Par exemple, si vous spécifiez `%TMP%/log.txt`, le fournisseur de journaux ajoute le texte littéral `/%TMP%/log.txt` vers le répertoire actuel de l’hôte.

## <a name="more-info-about-ssis-on-linux"></a>Plus d’informations sur SSIS sur Linux

Pour plus d’informations sur SSIS sur Linux, consultez les billets de blog suivants :

-   [SSIS sur Linux n’est disponible dans SQL Server 2017 CTP2.1](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC est pris en charge dans SSIS sur Linux (SQL Server 2017 CTP 2.1 Actualiser)](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-info-about-ssis"></a>Plus d’informations sur SSIS

Microsoft SQL Server Integration Services (SSIS) est une plate-forme de création de solutions d’intégration de données hautes performances, y compris l’extraction, transformation et chargement (ETL) de packages pour l’entreposage des données. Pour plus d’informations, consultez [SQL Server Integration Services](/sql/integration-services/sql-server-integration-services.md).

SSIS inclut les fonctionnalités suivantes :
- outils graphiques et des Assistants pour générer et déboguer des packages sur Windows
- une variété de tâches pour effectuer des fonctions de flux de travail tels que les opérations FTP, exécution d’instructions SQL et envoi de messages électroniques
- une variété de sources de données et des destinations pour l’extraction et chargement des données
- différentes transformations pour le nettoyage, l’agrégation, la fusion et la copie de données
- interfaces de programmation d’application (API) pour l’extension SSIS avec vos propres scripts personnalisés et les composants

Pour commencer avec SSIS, téléchargez la dernière version de [SQL Server Data Tools (SSDT)](../integration-services/ssis-how-to-create-an-etl-package.md).

## <a name="see-also"></a>Voir aussi
- [En savoir plus sur SQL Server Integration Services](../integration-services/sql-server-integration-services.md)
- [Développement de SQL Server Integration Services (SSIS) et les outils de gestion](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [Didacticiels sur SQL Server Integration Services](../integration-services/integration-services-tutorials.md)

