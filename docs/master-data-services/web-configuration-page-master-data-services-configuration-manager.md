---
title: Page de Configuration (Gestionnaire de Configuration Master Data Services) Web | Documents Microsoft
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.mds.configmanager.webconfigpg.f1
ms.assetid: 7b900778-0169-4e42-9faf-98dc1c01313e
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 32cc0f559017846efbc349377255634e89515c7d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="web-configuration-page-master-data-services-configuration-manager"></a>Page Configuration Web (Gestionnaire de configuration des services de données de référence)
  Utilisez la page **Configuration web** pour configurer un site web et une application web. Vous pouvez également activer Data Quality Services.  
  
## <a name="configure-the-web-application"></a>Configurer l'application Web  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Site Web**|Créez un site web, sélectionnez le site Web par défaut, ou sélectionnez un autre site disponibles (si répertorié). Cette liste affiche les sites Web définis dans les services Internet (IIS) sur l'ordinateur local. Lorsque vous créez un site web, une application Web est automatiquement créée. Lorsque vous sélectionnez une valeur par défaut ou un site existant différent, vous devez créer une application manuellement.|  
|**application Web**|Sélectionnez une application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] pour la configuration. Cette zone affiche uniquement les applications Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] du site Web sélectionné.<br /><br /> Si rien n’est affiché, cliquez sur **Créer** pour créer un site web.|  
|**Créer**|Ouvre la boîte de dialogue **Créer une application Web** dans laquelle vous créez une application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sur le site sélectionné. Ce bouton est activé uniquement lorsque le site sélectionné n'a aucune application Web racine configurée comme application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .|  
  
## <a name="associate-application-with-database"></a>Associer une base de données  à une application  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Select**|Ouvre la boîte de dialogue **Se connecter au serveur** à partir de laquelle vous vous connectez à une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sélectionnez une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] à associer à l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sélectionnée.|  
|**Instance SQL Server**|Affiche le nom de l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sélectionnée qui héberge la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Cette valeur est vide jusqu'à ce que vous vous connectiez à une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sélectionniez une base de données.|  
|**Base de données**|Affiche le nom de la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] associée à l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sélectionnée. Cette valeur est vide jusqu'à ce que vous vous connectiez à une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sélectionniez une base de données.|  
  
## <a name="enable-dqs-integration"></a>Activer l'intégration du DQS  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Activer l'intégration avec Data Quality Services**|Sélectionnez cette option pour activer les fonctionnalités de qualité des données disponibles dans le [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]. Pour plus d'informations, consultez [Enable Data Quality Services Integration with Master Data Services](../master-data-services/install-windows/enable-data-quality-services-integration-with-master-data-services.md).|  
  
## <a name="see-also"></a>Voir aussi  
[Installation de Master Data Services et la Configuration](../master-data-services/master-data-services-installation-and-configuration.md) [Web configuration requise pour Application &#40; Master Data Services &#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md)   
 [Créer une Application Web Master Data Manager &#40; Master Data Services &#41;](../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  
