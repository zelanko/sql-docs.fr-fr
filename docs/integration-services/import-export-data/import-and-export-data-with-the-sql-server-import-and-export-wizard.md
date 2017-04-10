---
title: "Importer et exporter des donn&#233;es avec l’Assistant Importation et Exportation SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exportation de données"
  - "mappage de fichiers [Integration Services]"
  - "Assistant Importation et Exportation SQL Server"
  - "packages SSIS, création"
  - "packages [Integration Services], copie"
  - "packages Integration Services, création"
  - "packages [Integration Services], création"
  - "packages SQL Server Integration Services, création"
  - "Assistant Importation et Exportation"
  - "copie de données [Integration Services]"
  - "importation de données, packages SSIS"
  - "sources [Integration Services], copie de données"
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
caps.latest.revision: 160
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 134
---
# Importer et exporter des donn&#233;es avec l’Assistant Importation et Exportation SQL Server
 La fonction de l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est de copier simplement des données d’une source vers une destination. Vous n’êtes pas obligé d’avoir installé SQL Server pour exécuter l’Assistant. Cette vue d’ensemble décrit les sources de données depuis ou vers lesquelles vous pouvez importer ou exporter des données à l’aide de l’Assistant, et les autorisations nécessaires pour exécuter l’Assistant.

Cette rubrique fournit uniquement une **vue d’ensemble** de l’Assistant.
-   Si vous êtes prêt à exécuter l’Assistant et souhaitez simplement savoir comment le démarrer, consultez [Démarrer l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).
-   Si vous recherchez des informations sur les étapes de l’Assistant, sélectionnez la page voulue dans le menu de navigation du contenu. Il existe une page distincte de documentation pour chaque page de l’Assistant. Sinon, pour afficher la documentation sur une page ou une boîte de dialogue déterminée de l’Assistant, appuyez sur la touche F1 à partir de cette page.

**Procurez-vous l’Assistant.** Si vous souhaitez exécuter l’Assistant, mais [!INCLUDE[msCoName] (../Token/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas installé sur votre ordinateur, vous pouvez installer l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en installant SSDT (SQL Server Data Tools). Pour plus d’informations, consultez [Télécharger SSDT (SQL Server Data Tools)](https://msdn.microsoft.com/library/mt204009.aspx).

> [!TIP] Si vous devez copier plusieurs bases de données ou des objets de base de données autres que des tables et des vues, utilisez l’Assistant Copie de base de données au lieu de l’Assistant Importation et exportation. Pour plus d’informations, consultez [Utiliser l’Assistant Copie de base de données](../../relational-databases/databases/use-the-copy-database-wizard.md).

## <a name="example-of-a-common-use-case---exporting-data-to-excel-video"></a>Exemple de cas d’utilisation courant : exporter des données vers Excel (vidéo)  
Une utilisation courante de l’Assistant est d’exporter des données vers Excel. Voici une vidéo de quatre minutes sur YouTube qui décrit l’Assistant et explique comment l’utiliser, avec des instructions claires et simples - [Using the SQL Server Import and Export Wizard to Export to Excel](https://go.microsoft.com/fwlink/?linkid=829049) (Utilisation de l’Assistant Importation et Exportation SQL Server pour exporter vers Excel).

##  <a name="a-namewizardsourcesa-what-data-sources-and-destinations-can-i-use"></a><a name="wizardSources"></a> Quelles sont les sources et destinations de données que je peux utiliser ?  
 L’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut copier des données à destination et en provenance des sources de données suivantes. Pour utiliser certains de ces sources de données, vous devrez peut-être télécharger et installer des fichiers supplémentaires.

| Source de données | Dois-je télécharger des fichiers supplémentaires ? |
|-------------|-----------------------------------------|
|**Bases de données d’entreprise**<br/>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Oracle et autres.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installe les fichiers nécessaires pour vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Oracle, mais n’installe pas les fichiers nécessaires pour vous connecter à d’autres bases de données d’entreprise, comme IBM DB2 ou Informix.<br/>- Si vous disposez déjà du logiciel client de votre système de base de données d’entreprise, vous avez en général ce qu’il vous faut pour établir une connexion.<br/>- Si vous n’avez pas installé le logiciel client, contactez l’administrateur de base de données pour lui demander comment installer une copie sous licence.|
|**Bases de données open source**<br/>MySql, PostgreSQL, SQLite et autres.|Vous devez télécharger des fichiers supplémentaires pour vous connecter à ces sources de données.<br/><br/>- Pour **MySql**, consultez [MySQL Connectors](http://dev.mysql.com/downloads/connector/).<br/>- Pour **PostgreSQL**, consultez [psqlODBC - PostgreSQL ODBC driver](https://odbc.postgresql.org/) et des produits tiers comme [Npgsql - .NET Data Provider for PostgreSQL](http://www.npgsql.org/).<br/>- Pour **SQLite**, plusieurs pilotes et fournisseurs open source sont disponibles en ligne.|
|**Fichiers texte** (fichiers plats).|Aucun fichier supplémentaire n’est requis.|
|**Fichiers Microsoft Excel et Microsoft Access**|Microsoft Office n’installe pas tous les fichiers nécessaires à l’établissement d’une connexion à des sources de données Excel et Access. Obtenez le téléchargement suivant : [Microsoft Access Runtime 2016](https://www.microsoft.com/download/details.aspx?id=50040).|
|**Sources de données Azure**<br/>Stockage d’objets blob Azure uniquement pour l’instant.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’installe pas les fichiers dont vous avez besoin pour vous connecter à Stockage Blob Azure en tant que source de données. Obtenez le téléchargement suivant : [Microsoft SQL Server 2016 Integration Services Feature Pack pour Azure](https://www.microsoft.com/download/details.aspx?id=49492).|
|**Toute autre source de données pour laquelle un connecteur est disponible**.|Généralement, vous devez télécharger des fichiers supplémentaires pour vous connecter aux sources de données des types suivants.<br/><br/>- N’importe quelle source pour laquelle un **pilote ODBC** est disponible. Créez une connexion ODBC (Open Database Connectivity) en sélectionnant le fournisseur .NET Framework pour ODBC dans la page **Choisir une source de données** ou **Choisir une destination** de l’Assistant, puis en fournissant une chaîne de connexion ou un nom de source de données (DSN) existant qui fait référence au pilote ODBC.<br/>- N’importe quelle source pour laquelle un **fournisseur OLE DB** est disponible.<br/>- N’importe quelle source pour laquelle un **fournisseur de données .NET Framework** est disponible.<br/>- Autres sources de données pour lesquelles des **composants tiers** offrent des fonctionnalités pour la source et la destination. En général, ces produits tiers sont vendus en tant que composants additionnels pour SQL Server Integration Services (SSIS).|
  
> [!TIP] Si votre source de données nécessite une chaîne de connexion, des exemples sont disponibles sur ce site tiers : [The Connection Strings Reference](https://www.connectionstrings.com/).  
  
## <a name="what-permissions-do-i-need-to-run-the-wizard"></a>Quelles sont les autorisations nécessaires pour exécuter l’Assistant ?  
 Pour mener à bien les étapes de l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez disposer au moins des autorisations suivantes. Si vous utilisez déjà vos source et destination de données, vous avez probablement les autorisations nécessaires.
  
|Des autorisations sont nécessaires pour effectuer les opérations suivantes|Si vous vous connectez à SQL Server, vous avez besoin de ces autorisations |  
|-------------------------|----------------------------------------------------|  
|Se connecter aux bases de données sources et de destination ou aux partages de fichiers|Droits de connexion aux bases de données et au serveur|  
|Exporter ou lire les données d’une base de données ou d’un fichier source.|Autorisations SELECT pour les tables et les vues sources|  
|Importer ou écrire des données dans la base de données ou le fichier de destination.|Autorisations INSERT dans les tables de destination|  
|Créer la base de données ou le fichier de destination, le cas échéant|Autorisations CREATE DATABASE ou CREATE TABLE|  
|Enregistrer le package SSIS créé par l’Assistant, le cas échéant|Si vous souhaitez enregistrer le package dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]autorisations suffisantes pour enregistrer le package dans la base de données **msdb**.|  
  
##  <a name="a-namewizardssisa-the-wizard-uses-sql-server-integration-services-ssis"></a><a name="wizardSSIS"></a> L’Assistant utilise SQL Server Integration Services (SSIS)  
 L’Assistant utilise SQL Server Integration Services (SSIS) pour copier les données. SSIS est un outil d’extraction, de transformation et de chargement (ETL) des données. Les pages de l’Assistant utilisent en partie le langage de SSIS.
  
 Dans SSIS, l’unité de base est le **package**. L’Assistant crée un package SSIS en mémoire à mesure que vous parcourez les pages de l’Assistant et spécifiez les options.    
  
Si vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition ou une édition supérieure, vous pouvez éventuellement enregistrer le package SSIS. Vous pouvez ensuite réutiliser le package et l’étendre à l’aide du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] pour y ajouter des tâches, des transformations et une logique pilotée par les événements. L’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] constitue le moyen le plus simple de créer un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de base qui copie des données à partir d’une source vers une destination.

Pour plus d’informations, consultez [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md).

## <a name="get-help-while-the-wizard-is-running"></a>Obtenir de l’aide pendant l’exécution de l’Assistant
> [!TIP] Pour afficher la documentation sur une page ou une boîte de dialogue déterminée de l’Assistant, appuyez sur la touche F1 à partir de cette page.   
  
## <a name="whats-next"></a>Étape suivante  
 Démarrez l'Assistant. Pour plus d’informations, consultez [Démarrer l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md).  
  
## <a name="see-also"></a>Voir aussi
[Mappage de type de données dans l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/data-type-mapping-in-the-sql-server-import-and-export-wizard.md)
