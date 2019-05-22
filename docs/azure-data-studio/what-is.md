---
title: Qu’est Azure Data Studio
titleSuffix: Azure Data Studio
description: Azure Data Studio est un outil gratuit, léger, qui s’exécute sur Windows, macOS et Linux, pour la gestion de SQL Server, base de données SQL Azure et Azure SQL Data Warehouse.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: overview
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.openlocfilehash: e93c417f286246f6db25d0463cec97eba8541c1c
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65993846"
---
# <a name="what-is-azure-data-studio"></a>Qu’est Azure Data Studio ?

Azure Data Studio est un multiplates-outil de base de données pour les professionnels des données à l’aide de la famille Microsoft locaux et cloud des plateformes de données sur Windows, MacOS et Linux.

Précédemment publiées sous le nom de la version préliminaire de SQL Operations Studio, Azure Data Studio offre une expérience de l’éditeur moderne avec Intellisense, des extraits de code, intégration du contrôle de source et un terminal intégré. Il est conçu avec l’utilisateur de plate-forme de données à l’esprit, avec intégrées dans les graphiques de jeux de résultats de requête et les tableaux de bord personnalisables.

**[Téléchargez et installez [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md)**


## <a name="sql-code-editor-with-intellisense"></a>Éditeur de code SQL avec IntelliSense

[!INCLUDE[name-sos](../includes/name-sos-short.md)] offre une SQL moderne, axée sur le clavier expérience qui facilite vos tâches quotidiennes avec des fonctionnalités intégrées, telles que les fenêtres à plusieurs onglets, un éditeur SQL riche, IntelliSense, l’achèvement de mot clé, des extraits de code, navigation dans le code et contrôle de code source de codage intégration (Git). Exécuter des requêtes SQL à la demande, afficher et enregistrer les résultats en tant que texte, JSON ou Excel. Modifiez les données, organisez vos connexions de base de données préférées et parcourez les objets de celles-ci dans une expérience de navigation familière. Pour savoir comment utiliser l’éditeur SQL, consultez [utilisez l’éditeur SQL pour créer des objets de base de données](tutorial-sql-editor.md).

## <a name="smart-sql-code-snippets"></a>Extraits de code SQL actives

Extraits de code SQL génèrent la syntaxe SQL appropriée pour créer des bases de données, tables, vues, procédures stockées, les utilisateurs, connexions, rôles, etc. et mettre à jour les objets de base de données existants. Utilisez les extraits de code intelligent pour créer rapidement des copies de votre base de données de développement ou à des fins de tests et pour générer et exécuter des scripts CREATE et INSERT.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] fournit également des fonctionnalités permettant de créer des extraits de code SQL personnalisés. Pour plus d’informations, consultez [créer et utiliser des extraits de code](code-snippets.md).


## <a name="customizable-server-and-database-dashboards"></a>Serveur personnalisable et tableaux de bord de base de données

Créer des tableaux de bord personnalisables pour surveiller et résoudre rapidement les goulots d’étranglement de performances de vos bases de données. Pour en savoir plus sur les widgets d’aperçu et les tableaux de bord de base de données (et de serveur), consultez [gérer les serveurs et les bases de données avec les widgets d'aperçu](insight-widgets.md).

## <a name="connection-management-server-groups"></a>Gestion des connexions (groupes de serveurs)

Les groupes de serveurs vous permettent d’organiser les informations de connexion pour les serveurs et les bases de données avec lesquels vous travaillez. Pour plus d’informations, consultez [groupes de serveurs](server-groups.md).

## <a name="integrated-terminal"></a>Terminal intégré

Utilisez vos outils de ligne de commande favoris (par exemple Bash, PowerShell, sqlcmd, bcp et ssh) dans la fenêtre du terminal intégré, directement dans l'interface utilisateur de [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Pour en savoir plus sur le terminal intégré, consultez [terminal intégré](integrated-terminal.md).

## <a name="extensibility-and-extension-authoring"></a>Extensibilité et la création d’extensions

Améliorer la [!INCLUDE[name-sos](../includes/name-sos-short.md)] expérience en étendant les fonctionnalités de l’installation de base. [!INCLUDE[name-sos](../includes/name-sos-short.md)] Fournit des points d’extensibilité pour les activités de gestion de données, ainsi que la prise en charge pour la création de l’extension.

Pour en savoir plus sur l’extensibilité dans [!INCLUDE[name-sos](../includes/name-sos-short.md)], consultez [extensibilité](extensibility.md).
Pour en savoir plus sur la création d’extensions, consultez [création d’extensions](extension-authoring.md).

## <a name="feature-comparison-with-sql-server-management-studio-ssms"></a>Comparaison des fonctionnalités avec SQL Server Management Studio (SSMS)

**Utiliser Azure Data Studio si vous :**
- Doivent s’exécuter sur Mac OS ou Linux
- Vous connectez à un cluster de données volumineux de SQL Server 2019
- La plupart de votre temps de modification ou de l’exécution de requêtes
- Ont besoin de pouvoir rapidement du graphique et visualiser des jeux de résultats
- Peuvent exécuter la plupart des tâches d’administration via le terminal intégré à l’aide de sqlcmd ou Powershell
- Avez besoin minimal pour les expériences de l’Assistant
- N’avez pas besoin d’effectuer une configuration approfondie d’administration

**Utilisez SQL Server Management Studio si vous :**
- Passez la majeure partie de votre temps sur les tâches d’administration de base de données
- Font configuration approfondie d’administration
- Effectuez la gestion de la sécurité, y compris la gestion des utilisateurs, évaluation des vulnérabilités et configuration des fonctionnalités de sécurité
- Utiliser les rapports pour SQL Server Query Store
- Avez besoin rendre l’utilisation des conseillers de réglage de performances et des tableaux de bord
- Font d’importation/exportation d’un dacpac
- Besoin d’accéder à des serveurs inscrits et souhaitez contrôler SQL Server des services sur Windows

### <a name="shell"></a>Shell

|Fonctionnalité|Azure Data Studio|SSMS|
|:---|:---|:---|
|Authentification dans Azure|Oui|Oui|
|Tableau de bord|Oui||
|Extensions|Oui||
|Terminal intégré|Oui||
|Explorateur d’objets|Oui|Oui|
|Scripts d’objets|Oui|Oui|
|Système de projet|Oui||
|Sélectionnez à partir de la Table|Oui|Oui|
|Contrôle de Code source|Oui||
|Volet de tâches|Oui||
|Thèmes|Oui||
|Mode foncé|Oui||
|Explorateur de ressources Azure|Preview||
|Assistant Générer des scripts||Oui|
|Importation/exportation DACPAC||Oui|
|Propriétés des objets||Oui|
|Concepteur de tables||Oui|


### <a name="query-editor"></a>Éditeur de requête

|Fonctionnalité|Azure Data Studio|SSMS|
|:---|:---|:---|
|Visionneuse de graphique|Oui||
|Exporter les résultats vers CSV, JSON, XLSX|Oui||
|IntelliSense|Oui|Oui|
|Extraits de code|Oui|Oui|
|Afficher le Plan|Preview|Oui|
|Statistiques du client||Oui|
|Statistiques des requêtes actives||Oui|
|Options de requête||Oui|
|Résultats dans un fichier||Oui|
|Résultats dans du texte||Oui|
|Visionneuse spatial||Oui|
|SQLCMD||Oui|

### <a name="operating-system-support"></a>Prise en charge du système d'exploitation

|Fonctionnalité|Azure Data Studio|SSMS|
|:---|:---|:---|
|Linux|Oui||
|macOS|Oui||
|Windows|Oui|Oui|

### <a name="data-engineering"></a>Ingénierie des données

|Fonctionnalité|Azure Data Studio|SSMS|
|:---|:---|:---|
|Créer l’Assistant de Table externe|Preview||
|Intégration de HDFS|Preview||
|Notebooks|Preview||

### <a name="database-administration"></a>Administration de bases de données

|Fonctionnalité|Azure Data Studio|SSMS|
|:---|:---|:---|
|Sauvegarde / restauration|Oui|Oui|
|Importation de fichier plat|Preview|Oui|
|Agent SQL|Preview|Oui|
|SQL Profiler|Preview|Oui|
|Always On||Oui|
|Always Encrypted||Oui|
|Assistant Copier des données||Oui|
|Assistant Paramétrage de données||Oui|
|Visionneuse de journal d’erreur||Oui|
|Plans de maintenance||Oui|
|Requête de plusieurs serveur||Oui|
|Gestion basée sur des stratégies||Oui|
|PolyBase||Oui|
|Magasin des requêtes||Oui|
|Serveurs inscrits||Oui|
|REPLICATION||Oui|
|Gestion de la sécurité||Oui|
|Service Broker||Oui|
|SQL Mail||Oui|
|Explorateur de modèles||Oui|
|Évaluation des vulnérabilités||Oui|
|Gestion de XEvent||Oui|

## <a name="next-steps"></a>Étapes suivantes

- [Téléchargez et installez[!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md)

- [Se connecter à et interroger SQL Server](quickstart-sql-server.md)
- [Se connecter et interroger la base de données SQL Azure](quickstart-sql-database.md)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]