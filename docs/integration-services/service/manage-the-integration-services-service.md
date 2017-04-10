---
title: "G&#233;rer le service Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Integration Services (service), configuration"
  - "services [Integration Services], configuration"
ms.assetid: 45554117-a0df-4830-b41c-5ebb33b764a5
caps.latest.revision: 63
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 63
---
# G&#233;rer le service Integration Services
    
> **IMPORTANT** Cette rubrique présente le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , un service Windows qui permet de gérer les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] prend en charge le service pour la compatibilité avec les versions antérieures de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. À compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], vous pouvez gérer des objets tels que des packages sur le serveur Integration Services.  
  
 Lorsque vous installez le composant [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est également installé. Par défaut, le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est démarré et le type de démarrage du service est défini comme étant automatique. Toutefois, vous devez également installer [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour utiliser le service afin de gérer les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stockés et en cours d'exécution.  
  
> **REMARQUE :** pour vous connecter directement à une instance du service Integration Services existante, vous devez utiliser la version de SQL Server Management Studio (SSMS) correspondant à la version de SQL Server sur lequel s’exécute le service Integration Services. Par exemple, pour vous connecter au service Integration Services existant s’exécutant sur une instance de SQL Server 2016, vous devez utiliser la version de SSMS publiée pour SQL Server 2016. [Téléchargez SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).
>
>   Dans la boîte de dialogue **Se connecter au serveur** de SSMS, vous ne pouvez pas entrer le nom d’un serveur sur lequel une version antérieure du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] s’exécute. Toutefois, pour gérer des packages stockés sur un serveur distant, vous ne devez pas vous connecter à l’instance du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur ce serveur distant. Au lieu de cela, modifiez le fichier de configuration du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] afin que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] affiche les packages stockés sur le serveur distant. Pour plus d’informations, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md).  
  
 Vous ne pouvez installer qu'une seule instance du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur un ordinateur. Le service n'est pas spécifique à une instance particulière du [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Vous vous connectez au service en utilisant le nom de l'ordinateur sur lequel il s'exécute.  
  
 Vous pouvez gérer le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à l’aide de l’un des composants logiciels enfichables MMC (Microsoft Management Console) suivants : Gestionnaire de configuration SQL Server ou Services. Avant de pouvoir gérer des packages dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous devez vérifier que le service a démarré.  
  
 Par défaut, le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est configuré pour gérer les packages dans la base de données msdb de l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui est installée au même moment que [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Si une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] n’est pas installée au même moment, le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est configuré pour gérer les packages dans la base de données msdb de l’instance locale par défaut du [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Pour gérer des packages stockés dans une instance nommée ou une instance distante du [!INCLUDE[ssDE](../../includes/ssde-md.md)]ou dans plusieurs instances du [!INCLUDE[ssDE](../../includes/ssde-md.md)], vous devez modifier le fichier de configuration du service. Pour plus d’informations, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md).  
  
 Par défaut, le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est configuré pour arrêter l'exécution des packages à l'arrêt du service. Toutefois, le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n'attend pas l'arrêt des packages et certains packages peuvent continuer à être exécutés après l'arrêt du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Si le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est arrêté, vous pouvez continuer à exécuter des packages par le biais de l’Assistant Importation et Exportation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], de l’utilitaire d’exécution de package et de l’utilitaire d’invite de commandes **dtexec** (dtexec.exe). Vous ne pouvez cependant pas surveiller les packages en cours d'exécution.  
  
 Par défaut, le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] s'exécute dans le contexte du compte SERVICE RESEAU.  
  
 Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] écrit dans le journal d'événements de Windows. Vous pouvez afficher les événements du service dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vous pouvez également consulter les événements du service à l'aide de l'Observateur d'événements Windows.  
  
### Pour définir les propriétés du service Integration Services à l'aide du composant logiciel enfichable Services  
  
-   [définir les propriétés du service Integration Services](../../integration-services/service/set-the-properties-of-the-integration-services-service.md)  
  
### Pour afficher les événements du service Integration Services  
  
-   [afficher les événements du service Integration Services](../../integration-services/service/view-events-for-the-integration-services-service.md)  
  
## Voir aussi  
 [Service Integration Services &#40;Service SSIS&#41;](../../integration-services/service/integration-services-service-ssis-service.md)   
 [Configuration du service Integration Services &#40;Service SSIS&#41;](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md)   
 [Assistant Importation et Exportation SQL Server](../Topic/SQL%20Server%20Import%20and%20Export%20Wizard.md)   
 [Utilitaire dtexec](../../integration-services/packages/dtexec-utility.md)   
 [Exécution de projets et de packages](https://msdn.microsoft.com/library/ms141708(v=sql.130).aspx)  
  
  