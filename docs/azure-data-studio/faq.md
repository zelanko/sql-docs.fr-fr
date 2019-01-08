---
title: Questions fréquentes (FAQ)
titleSuffix: Azure Data Studio
description: Forum aux questions (FAQ) sur Azure Data Studio.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 129e7de66e896e1f452c5d68fc4891d9cc5eafa3
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030330"
---
# <a name="includeazure-data-studioincludesname-sosmd-faq"></a>[!INCLUDE[Azure Data Studio](../includes/name-sos.md)] FAQ

## <a name="what-is-azure-data-studio"></a>Qu’est Azure Data Studio ?

Azure Data Studio est un nouveau open source, l’environnement de bureau multiplateforme pour les professionnels des données à l’aide de la famille Azure données locaux et cloud des plateformes de données sur Windows, MacOS et Linux. Précédemment publiées sous le nom de la version préliminaire de SQL Operations Studio, un éditeur modern expérience avec des offres Azure Data Studio comme l’éclair rapide IntelliSense, des extraits de code, intégration du contrôle de code source et un terminal intégré. Il est conçu avec l’utilisateur de plate-forme de données à l’esprit, avec intégrées dans les graphiques de jeux de résultats de requête et les tableaux de bord personnalisables.

Research a montré que les utilisateurs passent d’un ordre de grandeur plus de temps sur la modification de la requête que sur toute autre tâche avec SQL Server Management Studio. Pour cette raison, Azure Data Studio a été conçu pour concentrer étroitement sur les fonctionnalités qui sert le plus, avec des expériences supplémentaires disponibles en tant qu’extensions facultatives dans le produit. Ainsi, chaque utilisateur de personnaliser leur environnement pour les flux de travail qu’ils utilisent le plus souvent.


## <a name="how-much-does-azure-data-studio-cost"></a>Combien coûte Azure Data Studio ?

Azure Data Studio est gratuit pour une utilisation privée ou professionnelle.

## <a name="who-should-use-azure-data-studio"></a>Qui doit utiliser Azure Data Studio

Toute personne peut utiliser Azure Data Studio. Toutefois, il est conçu pour simplifier les tâches effectuées par les développeurs de base de données, les administrateurs de base de données, les administrateurs système et les éditeurs de logiciels indépendants.

## <a name="what-can-i-do-with-azure-data-studio"></a>Que puis-je faire avec Azure Data Studio ?

Azure Data Studio s’appuie sur Visual Studio Code et offre un léger, expérience de flux de travail de code moderne de focus du clavier lorsque vous travaillez avec SQL Server, base de données SQL Azure, Azure SQL DW. Azure Data Studio rend les expériences core que vous utilisez quotidiennement simple et facile avec les fonctionnalités intégrées telles que les fenêtres à plusieurs onglets, un éditeur SQL riche, IntelliSense, saisie automatique de mots-clés, des extraits de code & navigation dans le code et intégration du contrôle de code source (Git et TFS). Vous pouvez exécuter des requêtes à la demande, Afficher & Enregistrer les résultats en tant que texte, JSON ou Excel, modifier des données, organiser & gérer vos connexions de base de données préféré et parcourir les objets de base de données dans une expérience de navigation par objets familière.

Utilisez vos outils préférés de ligne de commande (par exemple, Bash, PowerShell, sqlcmd, bcp, psql et ssh) dans la fenêtre de Terminal intégré directement dans l’interface utilisateur Studio de données Azure. Générer et exécuter de créer facilement et les scripts d’insertion pour vos objets de base de données créer des copies de votre base de données pour le développement ou à des fins de tests. Améliorez votre productivité avec code intelligent des extraits de code et de riches graphiques expériences qui créent des nouvelles bases de données et des objets de base de données (tels que des tables, vues, procédures stockées, les utilisateurs, connexions, rôles, etc.) ou de mettre à jour des objets de base de données existants. Utilisez riche tableaux de bord personnalisables pour surveiller et résoudre rapidement les goulots d’étranglement de performances dans vos bases de données en local, dans Azure ou de n’importe quel cloud.

Azure Data Studio offre une expérience cohérente pour sauvegarder et restaurer vos bases de données. Avec prise en charge planifié pour les groupes de disponibilité SQL Server Always-On, vous pouvez facilement configurer, surveiller et résoudre les problèmes des groupes de disponibilité pour vos bases de données SQL Server critiques et rapidement basculer vers une base de données secondaire lors d’un sinistre. Azure Data Studio a été conçu pour améliorer votre productivité dans le cycle de développement de vos bases de données de choix sur les systèmes d’exploitation de votre choix. Par conséquent, vous pouvez toujours dans le contrôle, et vous pouvez réduire les risques, résoudre les problèmes plus rapidement et distribuez en continu valeur qui dépasse les attentes des clients.

## <a name="is-azure-data-studio-open-source"></a>Est Open Source de données Azure Studio ?

Le code source pour Azure Data Studio et ses fournisseurs de données est disponible sur GitHub. Le code source pour le front-end Data Studio Azure (qui est basé sur Visual Studio Code) est disponible sous un CLUF qui fournit des droits pour modifier et utiliser le logiciel, mais pas à le redistribuer ou de l’héberger dans un service cloud de code source. Le code source pour les fournisseurs de données est disponible sous licence MIT à [ https://github.com/Microsoft/sqltoolsservice ](https://github.com/Microsoft/sqltoolsservice).

## <a name="do-we-plan-to-open-source-ssms"></a>Nous prévoyons ouvrir la source de SSMS ?

Non. Toutefois, nouvelle génération multios CLI et l’interface graphique utilisateur des outils sont open source. Par exemple, l’extension mssql pour Visual Studio Code, mssql-scripter et msql-CLI sont tous open source sur GitHub. Le code source pour Azure Data Studio est disponible sur GitHub.  

## <a name="now-that-there-is-azure-data-studio-does-microsoft-plan-to-deprecate-ssms-and-ssdt"></a>Maintenant qu’il y ait Azure Data Studio, Microsoft prévoit-elle de déconseiller SSMS et SSDT ? 

Non. En plus de la prochaine génération de multios et d’outils CLI et l’interface graphique utilisateur de multi-DB continue investissements dans les outils de Windows phare (SSMS, SSDT, PowerShell). L’objectif est de proposer aux clients de choisir d’utiliser les outils qu’ils souhaitent sur les plateformes de leur choix pour les scénarios. Azure Data Studio se concentre plus étroitement sur les expériences autour de l’édition de requêtes et de développement de données, les études ont montré est la capacité plus très utilisée dans SQL Server Management Studio en un ordre de grandeur. Supplémentaires importants d’administration fonctionnalités telles que la sauvegarde, restauration, gestion des travaux de l’agent et le profilage de serveur sont également disponibles en tant qu’extensions dans Azure Data Studio. Azure Data Studio est également multiplateforme, permettant aux utilisateurs de travailler sur leur plateforme de votre choix. Toutefois, SQL Server Management Studio offre le plus large éventail de fonctions administratives toujours et reste l’outil phare pour les tâches de gestion de plateforme. 

## <a name="when-should-i-use-azure-data-studio-vs-sql-server-management-studio"></a>Quand dois-je utiliser Azure Data Studio vs SQL Server Management Studio ?

*Utiliser Azure Data Studio si vous :*

- Passez la majeure partie de votre temps de modification ou de l’exécution de requêtes.
- Ont besoin de pouvoir rapidement du graphique et visualiser des jeux de résultats.
- Peut exécuter la plupart des tâches d’administration via le terminal intégré à l’aide de sqlcmd ou Powershell.
- Ont besoin minimal pour les expériences de l’Assistant.
- N’avez pas besoin effectuer deep d’administration ou configuration associés de plateforme.
- Vous devrez exécuter sur Mac OS ou Linux.

*Utilisez SQL Server Management Studio si vous :*

- Passez la majeure partie de votre temps sur les tâches d’administration de base de données.
- Permet de faire une configuration d’administration ou de la plate-forme complexe.
- Gestion de la sécurité, y compris la gestion des utilisateurs, évaluation des vulnérabilités et configuration des fonctionnalités de sécurité font.
- Avez besoin rendre l’utilisation des conseillers de réglage de performances et des tableaux de bord.
- Utilisez les diagrammes de base de données et les concepteurs de table.
- Permet de faire importation/exportation d’un dacpac.
- Besoin d’accéder à des serveurs inscrits.
- Assurez-vous d’utiliser le mode sqlcmd, des statistiques des requêtes ou des statistiques du client.

## <a name="feature-comparison"></a>Comparaison des fonctionnalités

### <a name="shell-features"></a>Fonctionnalités du shell

|Fonctionnalité|Azure Data Studio|SSMS|
|:---|:---|:---|
|Authentification dans Azure|Oui|Oui|
|Tableau de bord|Oui| |
|Extensions|Oui| |
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
|Assistant Générer des scripts||Oui
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
|Débogueur T-SQL||Oui|

### <a name="operating-system-support"></a>Prise en charge du système d'exploitation

|Fonctionnalité|Azure Data Studio|SSMS|
|:---|:---|:---|
|Windows|Oui|Oui|
|macOS|Oui||
|Linux|Oui||

### <a name="data-engineering"></a>Ingénierie des données

|Fonctionnalité|Azure Data Studio|SSMS|
|:---|:---|:---|
|Assistant de données externes|Preview||
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
|Diagrammes de base de données||Oui|
|Visionneuse de journal d’erreur||Oui|
|Plans de maintenance||Oui|
|Requête de plusieurs serveur||Oui|
|Gestion basée sur des stratégies||Oui|
|PolyBase||Oui|
|Magasin de requêtes||Oui|
|Serveurs inscrits||Oui|
|REPLICATION||Oui|
|Gestion de la sécurité||Oui|
|Service Broker||Oui|
|SQL Mail||Oui|
|Explorateur de modèles||Oui|
|Évaluation des vulnérabilités||Oui|
|Gestion de XEvent||Oui|


## <a name="azure-data-studio-is-missing-a-feature-that-is-in-ssmsssdt-will-you-add-it"></a>Il manque une fonctionnalité qui se trouve dans SSMS/SSDT Studio de données Azure. Vous ajouterez il ?

Cela dépend de la nécessité de scénario & / l’activité du client. Pour aider à hiérarchiser, signaler une suggestion sur [GitHub](https://github.com/microsoft/azuredatastudio/issues).

## <a name="i-understand-azure-data-studio-and-the-mssql-extension-for-vs-code-are-powered-by-a-new-tools-service-that-uses-smo-apis-under-the-covers-is-smo-available-on-linux-and-macos"></a>Je comprends que Studio de données Azure et l’extension mssql pour Visual Studio Code sont alimentées par un nouveau service d’outils qui utilise les API de SMO en arrière-plan. SMO est disponible sur Linux et macOS ?

L’API SMO ne soient disponibles sur Linux ou macOS de manière consommable. Nous avons porté sur un sous-ensemble de l’API SMO vers .NET Core qui nous avions besoin pour Azure Data Studio et nous prévoyons d’étendre dans le cadre de la feuille de route. Le Service d’outils SQL se trouve sur GitHub : [ https://github.com/Microsoft/sqltoolsservice ](https://github.com/Microsoft/sqltoolsservice).

## <a name="do-you-plan-to-port-the-dacfx-apis-andor-sqlpackageexe-andor-ssdt-to-linux-and-macos"></a>Prévoyez-vous de DACFx APIs et/ou de sqlpackage.exe et/ou de SSDT pour Linux et macOS de port ?

Il se trouve sur la feuille de route à long terme. Pour aider à hiérarchiser, signaler une suggestion sur [GitHub](https://github.com/microsoft/azuredatastudio/issues).

## <a name="will-sql-powershell-cmdlets-be-available-on-linux-and-macos"></a>Applets de commande PowerShell de SQL sera disponible sur Linux et macOS ?

SQL PowerShell est disponible dès aujourd'hui sur PowerShell gallery et vous pouvez l’utiliser sur Windows pour fonctionner avec SQL Server en cours d’exécution n’importe où, y compris SQL sur Linux. Applets de commande sur Linux et macOS offre SQL PowerShell est dans la feuille de route. Pour aider à hiérarchiser, signaler une suggestion sur [GitHub](https://github.com/microsoft/azuredatastudio/issues).

## <a name="who-usually-uses-azure-data-studio"></a>Généralement, qui utilise Azure Data Studio ?

Les développeurs et administrateurs citent est généralement les utilisateurs d’Azure Data Studio.

## <a name="does-azure-data-studio-integrate-with-azure-sql-data-warehouse"></a>Azure Data Studio s’intègre avec Azure SQL Data Warehouse ?

Oui. Azure Data Studio prise en charge pour Azure SQL Data Warehouse est actuellement en version préliminaire, ainsi que Azure SQL Database Managed Instance et SQL Server 2019 Big Data.

## <a name="why-is-azure-data-studio-important-for-the-new-version-of-sql-server"></a>Pourquoi est-Azure Data Studio important pour la nouvelle version de SQL Server ?

Comme SQL Server étend ses capacités dans l’espace de données volumineuses, il a besoin de nouveaux outils pour prendre en charge les cas d’usage. Pour cette raison, Azure Data Studio livre dès aujourd'hui une nouvelle expérience de préversion de prise en charge pour SQL Server Big Data, y compris la première expérience de bloc-notes jamais dans l’ensemble d’outils de SQL Server et un nouvel Assistant de créer une Table externe qui rend l’accès aux données à partir de SQL à distance Instances de serveur et Oracle faciles et rapides.
