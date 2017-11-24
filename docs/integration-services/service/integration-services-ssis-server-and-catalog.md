---
title: Integration Services (SSIS) Server et catalogue | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: service
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 939f31adf1ab0a975bd4339dabab310ef9025049
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-server-and-catalog"></a>Integration Services (SSIS) Server et de catalogue
  Après avoir conçu et testé des packages dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], vous pouvez déployer les projets qui contiennent les packages sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge la base de données **SSISDB** . La base de données stocke les objets suivants : packages, projets, paramètres, autorisations, propriétés du serveur et historique opérationnel.  
  
 La base de données **SSISDB** expose les informations d'objet dans des vues publiques que vous pouvez interroger. La base de données fournit également des procédures stockées que vous pouvez appeler pour gérer les objets.  
  
 Avant de pouvoir déployer des projets sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vous devez créer le catalogue **SSISDB** .  
  
 Pour une vue d’ensemble de la fonctionnalité de catalogue SSISDB, consultez [catalogue SSIS](../../integration-services/service/ssis-catalog.md).  
  
## <a name="high-availability"></a>Haute disponibilité  
 Tout comme les autres bases de données utilisateur, la base de données **SSISDB** ne prend pas en charge la mise en miroir et la réplication de bases de données. Pour plus d’informations sur la mise en miroir et la réplication, consultez [mise en miroir de base de données &#40; SQL Server &#41; ](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Vous pouvez également fournir la haute disponibilité de SSISDB et son contenu en rendant utilisant SSIS et des groupes de disponibilité AlwaysOn. Pour plus d’informations, voir ce blog par Matt Masson, [SSIS avec Always On](http://go.microsoft.com/fwlink/?LinkId=255873), sur blogs.msdn.com.  
  
##  <a name="ssms"></a> Serveur Integration Services dans SQL Server Management Studio  
 Lorsque vous vous connectez à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge la base de données **SSISDB** , vous affichez les objets suivants dans l'Explorateur d'objets :  
  
-   **Base de données SSISDB**  
  
     La base de données **SSISDB** apparaît sous le nœud **Bases de données** dans l'Explorateur d'objets. Vous pouvez interroger les vues et appeler les procédures stockées qui gèrent le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les objets stockés sur le serveur.  
  
-   **Catalogues Integration Services**  
  
     Sous le nœud **Catalogues Integration Services** se trouvent des dossiers pour des environnements et des projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Afficher la liste des Packages sur le serveur Integration Services](../../integration-services/service/view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Integration Services (SSIS) de déployer les projets et Packages](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
-   [Exécuter des packages Integration Services (SSIS)](../../integration-services/packages/run-integration-services-ssis-packages.md)  
  
## <a name="related-content"></a>Contenu connexe  
 Entrée de blog, [SSIS avec Always On](http://go.microsoft.com/fwlink/?LinkId=255873), sur blogs.msdn.com.  
  
  

