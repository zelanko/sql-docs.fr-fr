---
title: "Integration Services (SSIS) Server et catalogue | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "packages [Integration Services], gestion"
  - "gestion de packages [Integration Services]"
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# Integration Services (SSIS) Server et catalogue
  Après avoir conçu et testé des packages dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], vous pouvez déployer les projets qui contiennent les packages sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Le [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server est une instance de la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge le **SSISDB** base de données. La base de données stocke les objets suivants : packages, projets, paramètres, autorisations, propriétés du serveur et historique opérationnel.  
  
 La base de données **SSISDB** expose les informations d'objet dans des vues publiques que vous pouvez interroger. La base de données fournit également des procédures stockées que vous pouvez appeler pour gérer les objets.  
  
 Avant de déployer les projets à le [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] serveur, vous devez créer le **SSISDB** catalogue.  
  
 Pour une vue d’ensemble de la fonctionnalité de catalogue SSISDB, consultez [catalogue SSIS](../../integration-services/service/ssis-catalog.md).  
  
## Haute disponibilité  
 Tout comme les autres bases de données utilisateur, la base de données **SSISDB** ne prend pas en charge la mise en miroir et la réplication de bases de données. Pour plus d’informations sur la mise en miroir et la réplication, consultez [mise en miroir de base de données & #40 ; SQL Server & #41 ;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Vous pouvez également fournir la haute disponibilité de SSISDB et son contenu en rendant SSIS et groupes de disponibilité AlwaysOn. Pour plus d’informations, consultez le blog par Matt Masson, [SSIS avec Always On](http://go.microsoft.com/fwlink/?LinkId=255873), sur blogs.msdn.com.  
  
##  <a name="ssms"></a> Serveur Integration Services dans SQL Server Management Studio  
 Lorsque vous vous connectez à une instance de la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge le **SSISDB** base de données, vous voyez les objets suivants dans l’Explorateur d’objets :  
  
-   **Base de données SSISDB**  
  
     La base de données **SSISDB** apparaît sous le nœud **Bases de données** dans l'Explorateur d'objets. Vous pouvez interroger les vues et appeler les procédures stockées qui gèrent le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les objets stockés sur le serveur.  
  
-   **Catalogues Integration Services**  
  
     Sous le nœud **Catalogues Integration Services** se trouvent des dossiers pour des environnements et des projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## Tâches associées  
  
-   [Créer le catalogue SSIS](../../integration-services/service/create-the-ssis-catalog.md)  
  
-   [Afficher la liste des packages sur le serveur Integration Services](../../integration-services/service/view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Déployer des projets sur le serveur Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md)  
  
-   [Exécuter un package sur le serveur SSIS à l'aide de SQL Server Management Studio](../../integration-services/packages/run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## Contenu connexe  
 Entrée de blog, [SSIS avec Always On](http://go.microsoft.com/fwlink/?LinkId=255873), sur blogs.msdn.com.  
  
  