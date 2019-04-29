---
title: Integration Services (SSIS) et environnements de Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- studio environments [Integration Services]
- tools [Integration Services], Business Intelligence Development Studio
- Business Intelligence Development Studio, Integration Services in
- SQL Server Management Studio [Integration Services]
- SSIS, studio environments
- SQL Server Integration Services, studio environments
- tools [Integration Services], SQL Server Management Studio
ms.assetid: 4eb73e65-d9f3-4ac6-a408-abfa85afc537
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7c8f05c1b822cc3cad81ed910b71cb46621554eb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62892416"
---
# <a name="integration-services-ssis-and-studio-environments"></a>Integration Services (SSIS) et environnements de Studio
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclut deux studios de travail pour travailler avec [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour le développement des packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] requis par une solution métier. [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] fournit le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans lequel vous créez des packages.  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour la gestion de packages dans un environnement de production.  
  
## <a name="sql-server-data-tools"></a>SQL Server Data Tools  
 Vous pouvez réaliser les tâches suivantes dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]:  
  
-   exécuter l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour créer des packages de base qui copient des données entre une source et une destination ;  
  
-   créer des packages qui incluent un flux de contrôle complexe, un flux de données, une logique piloté par les événements et la journalisation ;  
  
-   tester et déboguer les packages à l'aide des fonctionnalités de résolution des problèmes et de surveillance du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] et des fonctionnalités de débogage de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)];  
  
-   créer des configurations qui mettent à jour les propriétés des packages et les objets de package au moment de l'exécution ;  
  
-   créer un utilitaire de déploiement qui peut installer les packages et leurs dépendances sur d'autres ordinateurs ;  
  
-   enregistrer des copies des packages dans la base de données msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], le magasin de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] et le système de fichiers.  
  
 Pour plus d'informations sur [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], consultez [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686.aspx).  
  
## <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] fournit le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] que vous utilisez pour gérer des packages, surveiller les packages en cours d'exécution, et déterminer l'impact et le lignage des données pour les objets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Vous pouvez réaliser les tâches suivantes dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]:  
  
-   créer des dossiers pour organiser les packages de manière significative pour votre organisation ;  
  
-   exécuter les packages stockés sur l'ordinateur local à l'aide de l'utilitaire d'exécution de package ;  
  
-   exécuter l’utilitaire d’exécution de package pour générer une ligne de commande à utiliser lors de l’exécution de l’utilitaire de ligne de commande **dtexec** (dtexec.exe) ;  
  
-   importer et exporter des packages dans la base de données msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la banque de packages [!INCLUDE[ssIS](../includes/ssis-md.md)] et le système de fichiers.  
  
