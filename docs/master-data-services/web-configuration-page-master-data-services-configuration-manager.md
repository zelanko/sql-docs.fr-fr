---
title: "Page Configuration Web (Gestionnaire de configuration des services de donn&#233;es de r&#233;f&#233;rence) | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.mds.configmanager.webconfigpg.f1"
ms.assetid: 7b900778-0169-4e42-9faf-98dc1c01313e
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Page Configuration Web (Gestionnaire de configuration des services de donn&#233;es de r&#233;f&#233;rence)
  Utilisez la page **Configuration web** pour configurer un site web et une application web. Vous pouvez également activer Data Quality Services.  
  
## Configurer l'application Web  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Site Web**|Créez un site web, sélectionnez le site Web par défaut, ou sélectionnez un autre site disponibles (si répertorié). Cette liste affiche les sites Web définis dans les services Internet (IIS) sur l'ordinateur local. Lorsque vous créez un site web, une application Web est automatiquement créée. Lorsque vous sélectionnez une valeur par défaut ou un site existant différent, vous devez créer une application manuellement.|  
|**application Web**|Sélectionnez une application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] pour la configuration. Cette zone affiche uniquement les applications Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] du site Web sélectionné.<br /><br /> Si rien n’est affiché, cliquez sur **Créer** pour créer un site web.|  
|**Créer**|Ouvre la boîte de dialogue **Créer une application Web** dans laquelle vous créez une application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sur le site sélectionné. Ce bouton est activé uniquement lorsque le site sélectionné n'a aucune application Web racine configurée comme application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .|  
  
## Associer une base de données  à une application  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Select**|Ouvre la boîte de dialogue **Se connecter au serveur** à partir de laquelle vous vous connectez à une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sélectionnez une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] à associer à l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sélectionnée.|  
|**Instance SQL Server**|Affiche le nom de l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sélectionnée qui héberge la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Cette valeur est vide jusqu'à ce que vous vous connectiez à une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sélectionniez une base de données.|  
|**Base de données**|Affiche le nom de la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] associée à l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sélectionnée. Cette valeur est vide jusqu'à ce que vous vous connectiez à une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sélectionniez une base de données.|  
  
## Activer l'intégration du DQS  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Activer l'intégration avec Data Quality Services**|Sélectionnez cette option pour activer les fonctionnalités Data Quality disponibles dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]. Pour plus d'informations, consultez [Enable Data Quality Services Integration with Master Data Services](../master-data-services/install-windows/enable-data-quality-services-integration-with-master-data-services.md).|  
  
## Voir aussi  
 [Prise en main de Master Data Services &#40;SQL Server 2016&#41;](../Topic/Get%20Started%20with%20Master%20Data%20Services%20\(SQL%20Server%202016\).md)   
 [Configuration requise pour l’application web &#40;Master Data Services&#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md)   
 [Créer une application web Master Data Manager &#40;Master Data Services&#41;](../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  