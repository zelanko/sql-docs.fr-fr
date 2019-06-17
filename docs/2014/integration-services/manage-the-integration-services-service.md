---
title: Gérer le Service Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- services [Integration Services], configuring
ms.assetid: 45554117-a0df-4830-b41c-5ebb33b764a5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fc3b1eb4e73b3d77b49cc9f485e0a6fc456a8875
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66057788"
---
# <a name="manage-the-integration-services-service"></a>Gérer le service Integration Services
    
> [!IMPORTANT]  
>  Cette rubrique présente le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , un service Windows qui permet de gérer les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] prend en charge le service pour la compatibilité avec les versions antérieures de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. À compter de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], vous pouvez gérer des objets tels que des packages sur le serveur Integration Services.  
  
 Lorsque vous installez le composant [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est également installé. Par défaut, le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est démarré et le type de démarrage du service est défini comme étant automatique. Toutefois, vous devez également installer [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour utiliser le service afin de gérer les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] stockés et en cours d'exécution.  
  
> [!NOTE]  
>  Vous ne pouvez pas vous connecter à une instance de la [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service à partir de la [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] version de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Autrement dit, dans la boîte de dialogue **Se connecter au serveur** , vous ne pouvez pas entrer le nom d'un serveur sur lequel seule la version [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] s'exécute. Toutefois, vous pouvez modifier le fichier de configuration pour le service et gérer ainsi les packages stockés dans une instance de [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] à partir de la version [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] de [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Pour plus d’informations, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](service/integration-services-service-ssis-service.md).  
  
 Vous ne pouvez installer qu'une seule instance du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur un ordinateur. Le service n'est pas spécifique à une instance particulière du [!INCLUDE[ssDE](../includes/ssde-md.md)]. Vous vous connectez au service en utilisant le nom de l'ordinateur sur lequel il s'exécute.  
  
 Vous pouvez gérer le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] à l’aide de l’un des composants logiciels enfichables Microsoft Management Console (MMC) suivants : Gestionnaire de configuration ou Services SQL Server. Avant de pouvoir gérer des packages dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], vous devez vérifier que le service a démarré.  
  
 Par défaut, le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est configuré pour gérer les packages dans la base de données msdb de l’instance du [!INCLUDE[ssDE](../includes/ssde-md.md)] qui est installée au même moment que [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Si une instance du [!INCLUDE[ssDE](../includes/ssde-md.md)] n’est pas installée au même moment, le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est configuré pour gérer les packages dans la base de données msdb de l’instance locale par défaut du [!INCLUDE[ssDE](../includes/ssde-md.md)]. Pour gérer des packages stockés dans une instance nommée ou une instance distante du [!INCLUDE[ssDE](../includes/ssde-md.md)]ou dans plusieurs instances du [!INCLUDE[ssDE](../includes/ssde-md.md)], vous devez modifier le fichier de configuration du service. Pour plus d’informations, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](service/integration-services-service-ssis-service.md).  
  
 Par défaut, le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est configuré pour arrêter l'exécution des packages à l'arrêt du service. Toutefois, le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] n'attend pas l'arrêt des packages et certains packages peuvent continuer à être exécutés après l'arrêt du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Si le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] est arrêté, vous pouvez continuer à exécuter des packages par le biais de l’Assistant Importation et Exportation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], du concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)], de l’utilitaire d’exécution de package et de l’utilitaire d’invite de commandes **dtexec** (dtexec.exe). Vous ne pouvez cependant pas surveiller les packages en cours d'exécution.  
  
 Par défaut, le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] s'exécute dans le contexte du compte SERVICE RESEAU.  
  
 Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] écrit dans le journal d'événements de Windows. Vous pouvez afficher les événements du service dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Vous pouvez également consulter les événements du service à l'aide de l'Observateur d'événements Windows.  
  
### <a name="to-set-properties-of-integration-services-service-using-the-services-snap-in"></a>Pour définir les propriétés du service Integration Services à l'aide du composant logiciel enfichable Services  
  
-   [Définir les propriétés du service Integration Services](../../2014/integration-services/set-the-properties-of-the-integration-services-service.md)  
  
### <a name="to-view-service-events-for-integration-services-service"></a>Pour afficher les événements du service Integration Services  
  
-   [afficher les événements du service Integration Services](../../2014/integration-services/view-events-for-the-integration-services-service.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Service Integration Services &#40;Service SSIS&#41;](service/integration-services-service-ssis-service.md)   
 [Configuration du service Integration Services &#40;Service SSIS&#41;](configuring-the-integration-services-service-ssis-service.md)   
 [Assistant Importation et Exportation SQL Server](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)   
 [Utilitaire dtexec](packages/dtexec-utility.md)   
 [Exécution de projets et de packages](packages/run-integration-services-ssis-packages.md)  
  
  
