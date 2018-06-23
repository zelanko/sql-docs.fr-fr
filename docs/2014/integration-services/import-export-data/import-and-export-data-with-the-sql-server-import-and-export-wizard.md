---
title: SQL Server Assistant Importation et exportation | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 87
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3e320ff0fdb834ca242739a76fb9e0b1242e3579
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143527"
---
# <a name="sql-server-import-and-export-wizard"></a>Assistant Importation et Exportation SQL Server
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation constitue le moyen le plus simple pour créer un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package qui copie les données d’une source vers une destination.  
  
> [!NOTE]  
>  Sur un ordinateur 64 bits, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installe la version 64 bits de l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (DTSWizard.exe). Toutefois, certaines sources de données, telles qu'Access ou Excel, ne dispose que d'un fournisseur 32 bits. Pour utiliser ces sources de données, il peut s'avérer nécessaire d'installer et d'exécuter la version 32 bits de l'Assistant. Pour installer la version 32 bits de l’Assistant, sélectionnez Outils clients ou [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] lors de l’installation.  
  
 Vous pouvez démarrer l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir du menu Démarrer, de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou à l'invite de commandes. Pour plus d’informations, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation peuvent copier des données vers et à partir de n’importe quelle source de données pour laquelle managé [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] fournisseur de données ou un fournisseur OLE DB natif est disponible. La liste des fournisseurs disponibles comprend les sources des données suivantes :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Fichiers plats  
  
-   Microsoft Office Access  
  
-   Microsoft Office Excel  
  
 Certaines fonctionnalités de l'Assistant fonctionnent différemment en fonction de l'environnement dans lequel vous le démarrez.  
  
-   Si vous démarrez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous exécutez le package immédiatement en sélectionnant le **exécuter immédiatement** case à cocher. Cette case à cocher est activée par défaut, et le package s'exécute immédiatement.  
  
     Vous pouvez également choisir d'enregistrer le package dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou dans le système de fichiers. Si vous choisissez d'enregistrer le package, vous devez également spécifier un niveau de protection pour ce dernier. Pour plus d’informations sur les niveaux de protection de package, consultez [le contrôle d’accès pour les données sensibles dans des Packages](../security/access-control-for-sensitive-data-in-packages.md).  
  
     Après le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation a créé le package et copié les données, vous pouvez utiliser la [!INCLUDE[ssIS](../../includes/ssis-md.md)] concepteur pour ouvrir et modifier le package enregistré en ajoutant des tâches, des transformations et une logique pilotée par événements.  
  
    > [!NOTE]  
    >  Dans [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], la possibilité d’enregistrer le package créé par l’Assistant n’est pas disponible.  
  
-   Si vous démarrez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation d’un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de projet dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], le package ne peut pas être exécuté comme une étape de fin de l’Assistant. Au lieu de cela, le package est ajouté au projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à partir duquel vous avez démarré l'Assistant. Vous pouvez ensuite exécuter le package ou l'étendre en y ajoutant des tâches, des transformations et une logique pilotée par les événements à l'aide du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 Pour plus d’informations, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
## <a name="permissions-required-by-the-import-and-export-wizard"></a>Autorisations requises par l'Assistant Importation et Exportation  
 Pour terminer le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation avec succès, doit avoir au moins les autorisations suivantes :  
  
-   Autorisations de vous connecter aux bases de données sources et de destination ou aux partages de fichiers. Dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], cela nécessite des droits de connexion de serveur et de base de données.  
  
-   Autorisation de lire les données d'une base de données ou d'un fichier source. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cela nécessite des autorisations SELECT sur les tables source et les vues.  
  
-   Autorisations d'écrire des données dans la base de données ou le fichier de destination. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cela nécessite des autorisations INSERT sur les tables de destination.  
  
-   Si vous souhaitez créer une base de données, une table ou un fichier de destination, vous devez, pour cela, disposer d'autorisations suffisantes. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cela implique les autorisations CREATE DATABASE ou CREATE TABLE.  
  
-   Si vous souhaitez enregistrer le package créé par l’Assistant, et disposer d’autorisations suffisantes pour écrire dans la base de données msdb ou au système de fichiers. Dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], cela nécessite des autorisations INSERT sur la base de données msdb.  
  
## <a name="mapping-data-types-in-the-import-and-export-wizard"></a>Mappage de types de données dans l'Assistant Importation et Exportation  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation fournit des fonctions de transformation minimales. À l'exception de la définition du nom, du type de données et des propriétés de type de données des colonnes des nouveaux fichiers et tables de destination, l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend en charge aucune transformation de niveau colonne.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation utilise le mappage de fichiers [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fournit pour mapper des types de données à partir de la version d’une base de données ou système vers un autre. Par exemple, il peut mapper de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à Oracle. Par défaut, les fichiers de mappage au format XML sont installés dans C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles. Si votre entreprise nécessite différents mappages entre types de données, vous pouvez mettre à jour les mappages pour affecter les mappages que l'Assistant effectue. Par exemple, si vous souhaitez que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **nchar** type de données à mapper à DB2 **graphique** type de données au lieu de DB2 **VARGRAPHIC** lors du transfert de données à partir de type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers DB2, vous devez modifier le **nchar** mappage dans le fichier de mappage SqlClientToIBMDB2.xml pour utiliser **graphique** au lieu de **VARGRAPHIC.**  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut des mappages entre de nombreuses combinaisons de sources et de destinations fréquemment employées, et vous pouvez ajouter de nouveaux fichiers de mappage dans le répertoire Mapping Files pour prendre en charge des sources et des destinations supplémentaires. Les nouveaux fichiers de mappage doivent se conformer au schéma XSD publié et être mappés entre une combinaison unique de source et de destination.  
  
> [!NOTE]  
>  Si vous modifiez un fichier de mappage existant ou ajoutez un nouveau fichier de mappage dans le dossier, vous devez fermer puis rouvrir le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation ou [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour les fichiers nouveaux ou modifiés être reconnus.  
  
## <a name="external-resources"></a>Ressources externes  
  
-   Vidéo, [exportation de données SQL Server vers Excel (vidéo liée à SQL Server)](http://go.microsoft.com/fwlink/?LinkID=200975), sur technet.microsoft.com  
  
-   Exemple CodePlex, [l’exportation d’ODBC vers un fichier plat en utilisant un didacticiel de l’Assistant : Packages de leçons](http://go.microsoft.com/fwlink/?LinkId=217657), sur msftisprodsamples.codeplex.com  
  
  