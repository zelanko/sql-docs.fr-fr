---
title: Serveur Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3425a628b5779f8f088a6144355449fc94d988b1
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439086"
---
# <a name="integration-services-ssis-server"></a>Serveur Integration Services (SSIS)
  Après avoir conçu et testé des packages dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], vous pouvez déployer les projets qui contiennent les packages sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge la base de données `SSISDB`. La base de données stocke les objets suivants : packages, projets, paramètres, autorisations, propriétés du serveur et historique opérationnel.  
  
 La base de données `SSISDB` expose les informations d'objet dans des vues publiques que vous pouvez interroger. La base de données fournit également des procédures stockées que vous pouvez appeler pour gérer les objets.  
  
 Avant de pouvoir déployer des projets sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous devez créer le catalogue `SSISDB`.  
  
 Vous trouverez une vue d’ensemble des fonctionnalités du catalogue SSISDB sur la page [Catalogue SSIS](ssis-catalog.md).  
  
## <a name="high-availability"></a>Haute disponibilité  
 Tout comme les autres bases de données utilisateur, la base de données `SSISDB` ne prend pas en charge la mise en miroir et la réplication de bases de données. Pour plus d’informations sur la mise en miroir et la réplication, consultez la page [Mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Vous pouvez également fournir une haute disponibilité de SSISDB et de son contenu en utilisant SSIS et les groupes de disponibilité AlwaysOn. Pour plus d'informations, consultez cette entrée de blog de Matt Masson, [SSIS with AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873)(en anglais), sur le site Web blogs.msdn.com.  
  
##  <a name="integration-services-server-in-sql-server-management-studio"></a><a name="ssms"></a>Integration Services Server dans SQL Server Management Studio  
 Lorsque vous vous connectez à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge la base de données `SSISDB`, vous affichez les objets suivants dans l'Explorateur d'objets :  
  
-   **Base de données SSISDB**  
  
     La `SSISDB` base de données apparaît sous le nœud **bases de données** dans l’Explorateur d’objets. Vous pouvez interroger les vues et appeler les procédures stockées qui gèrent le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et les objets stockés sur le serveur.  
  
-   **Catalogues Integration Services**  
  
     Sous le nœud **Catalogues Integration Services** se trouvent des dossiers pour des environnements et des projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Créer le catalogue SSIS](../create-the-ssis-catalog.md)  
  
-   [Afficher la liste des packages sur le serveur Integration Services](view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Déployer des projets sur le serveur Integration Services](../deploy-projects-to-integration-services-server.md)  
  
-   [Exécuter un package sur le serveur SSIS à l’aide de SQL Server Management Studio](../run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a>Contenu associé  
 Entrée de blog, [SSIS with AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873)(en anglais), sur le site Web blogs.msdn.com.  
  
  
