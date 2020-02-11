---
title: Assistant importation et exportation SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- exporting data
- mapping files [Integration Services]
- SQL Server Import and Export Wizard
- SSIS packages, creating
- packages [Integration Services], copying
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
- Import and Export Wizard
- copying data [Integration Services]
- importing data, SSIS packages
- sources [Integration Services], copying data
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2f3ce90e2670357d0842b0a6ac7838f396465bab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62768161"
---
# <a name="sql-server-import-and-export-wizard"></a>Assistant Importation et Exportation SQL Server
  L' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant importation et exportation offre la méthode la plus simple pour créer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] un package qui copie les données d’une source vers une destination.  
  
> [!NOTE]  
>  Sur un ordinateur 64 bits, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installe la version 64 bits de l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (DTSWizard.exe). Toutefois, certaines sources de données, telles qu'Access ou Excel, ne dispose que d'un fournisseur 32 bits. Pour utiliser ces sources de données, il peut s'avérer nécessaire d'installer et d'exécuter la version 32 bits de l'Assistant. Pour ce faire, sélectionnez Outils clients ou [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] lors de l'installation.  
  
 Vous pouvez démarrer l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir du menu Démarrer, de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou à l'invite de commandes. Pour plus d’informations, consultez [exécuter l’Assistant importation et exportation SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 L'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut copier des données dans et à partir de toute source de données pour laquelle un fournisseur de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] managé ou un fournisseur OLE DB natif est disponible. La liste des fournisseurs disponibles comprend les sources des données suivantes :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Fichiers plats  
  
-   Microsoft Office Access  
  
-   Microsoft Office Excel  
  
 Certaines fonctionnalités de l'Assistant fonctionnent différemment en fonction de l'environnement dans lequel vous le démarrez.  
  
-   Si vous démarrez l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant importation et exportation dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous exécutez immédiatement le package en activant la case à cocher **exécuter immédiatement** . Cette case à cocher est activée par défaut, et le package s'exécute immédiatement.  
  
     Vous pouvez également choisir d'enregistrer le package dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou dans le système de fichiers. Si vous choisissez d'enregistrer le package, vous devez également spécifier un niveau de protection pour ce dernier. Pour plus d’informations sur les niveaux de protection des packages, consultez [Access Control pour obtenir des données sensibles dans des packages](../security/access-control-for-sensitive-data-in-packages.md).  
  
     Une fois que l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a créé le package et copié les données, vous pouvez utiliser le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] pour ouvrir et modifier le package enregistré, en ajoutant des tâches, des transformations et une logique pilotée par les événements.  
  
    > [!NOTE]  
    >  Dans [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], l'option permettant d'enregistrer le package créé par l'Assistant n'est pas disponible.  
  
-   Si vous démarrez l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], le package ne peut pas être exécuté en tant qu'étape de l'Assistant. Au lieu de cela, le package est ajouté au projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à partir duquel vous avez démarré l'Assistant. Vous pouvez ensuite exécuter le package ou l'étendre en y ajoutant des tâches, des transformations et une logique pilotée par les événements à l'aide du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 Pour plus d’informations, consultez [exécuter l’Assistant importation et exportation SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
## <a name="permissions-required-by-the-import-and-export-wizard"></a>Autorisations requises par l'Assistant Importation et Exportation  
 Pour mener à bien les étapes de l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez disposer au moins des autorisations suivantes :  
  
-   Autorisations de vous connecter aux bases de données sources et de destination ou aux partages de fichiers. Dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], cela implique des droits de connexion aux bases de données et au serveur.  
  
-   Autorisation de lire les données d'une base de données ou d'un fichier source. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cela implique des autorisations SELECT pour les tables et les vues sources.  
  
-   Autorisations d'écrire des données dans la base de données ou le fichier de destination. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cela implique des autorisations INSERT dans les tables de destination.  
  
-   Si vous souhaitez créer une base de données, une table ou un fichier de destination, vous devez, pour cela, disposer d'autorisations suffisantes. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cela implique les autorisations CREATE DATABASE ou CREATE TABLE.  
  
-   Si vous souhaitez enregistrer le package créé par l'Assistant, vous devez disposer d'autorisations suffisantes pour écrire dans la base de données msdb ou dans le système de fichiers. Dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], cela nécessite des autorisations INSERT sur la base de données msdb.  
  
## <a name="mapping-data-types-in-the-import-and-export-wizard"></a>Mappage de types de données dans l'Assistant Importation et Exportation  
 L'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre des fonctions de transformation minimales. À l'exception de la définition du nom, du type de données et des propriétés de type de données des colonnes des nouveaux fichiers et tables de destination, l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend en charge aucune transformation de niveau colonne.  
  
 L'Assistant Importation et Exportation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise des fichiers de mappage que [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fournit pour mapper des types de données d'une version de base de données ou de système à une autre. Par exemple, il peut mapper de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à Oracle. Par défaut, les fichiers de mappage au format XML sont installés dans C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles. Si votre entreprise nécessite différents mappages entre types de données, vous pouvez mettre à jour les mappages pour affecter les mappages que l'Assistant effectue. Par exemple, si vous souhaitez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le type de données **nchar** soit mappé au type de données **Graphics** DB2 au **** lieu du type de données DB2 VARGRAPHIC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lors du transfert de données de vers DB2, vous devez modifier le mappage **nchar** dans le fichier de mappage SqlClientToIBMDB2. xml pour qu’il utilise **Graphic** au lieu de **VARGRAPHIC.**  
  
 
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut des mappages entre de nombreuses combinaisons de sources et de destinations fréquemment employées, et vous pouvez ajouter de nouveaux fichiers de mappage dans le répertoire Mapping Files pour prendre en charge des sources et des destinations supplémentaires. Les nouveaux fichiers de mappage doivent se conformer au schéma XSD publié et être mappés entre une combinaison unique de source et de destination.  
  
> [!NOTE]  
>  Si vous modifiez un fichier de mappage existant ou ajoutez un nouveau fichier de mappage au dossier, vous devez fermer et rouvrir l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour identifier les fichiers nouveaux ou modifiés.  
  
## <a name="external-resources"></a>Ressources externes  
  
-   Vidéo, [exportation de données SQL Server vers Excel (vidéo SQL Server)](https://go.microsoft.com/fwlink/?LinkID=200975), sur TechNet.Microsoft.com  
  
-   Exemple CodePlex, [exportation d’ODBC vers un fichier plat à l’aide d’un Assistant : packages de leçon](https://go.microsoft.com/fwlink/?LinkId=217657), sur MSFTISProdSamples.codeplex.com  
  
  
