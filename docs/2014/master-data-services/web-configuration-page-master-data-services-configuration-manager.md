---
title: Page Configuration web (Gestionnaire de configuration Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.webconfigpg.f1
ms.assetid: 7b900778-0169-4e42-9faf-98dc1c01313e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 12ba4a2d03e98d5f2dac79917e23a93c0a24cdb0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65481212"
---
# <a name="web-configuration-page-master-data-services-configuration-manager"></a>Page Configuration Web (Gestionnaire de configuration des services de données de référence)
  Utilisez la page **Configuration Web** pour créer un nouveau site web ou pour créer un nouveau site web ou une application Web. Après avoir sélectionné une application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , vous pouvez spécifier la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] de l'application et activer les Data Quality Services.  
  
## <a name="configure-the-web-application"></a>Configurer l'application Web  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Site web**|Créez un site web, sélectionnez le site Web par défaut, ou sélectionnez un autre site disponibles (si répertorié). Cette liste affiche les sites Web définis dans les services Internet (IIS) sur l'ordinateur local. Lorsque vous créez un site web, une application Web est automatiquement créée. Lorsque vous sélectionnez une valeur par défaut ou un site existant différent, vous devez créer une application manuellement.|  
|**Application web**|Sélectionnez une application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] pour la configuration. Cette zone affiche uniquement les applications Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] du site Web sélectionné.<br /><br /> Si rien n'est affiché, cliquez sur **Créer une application** pour créer un site Web.|  
|**Créer une application**|Ouvre la boîte de dialogue **Créer une application Web** dans laquelle vous créez une application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sur le site sélectionné. Ce bouton est activé uniquement lorsque le site sélectionné n'a aucune application Web racine configurée comme application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .|  
  
## <a name="associate-application-with-database"></a>Associer une base de données  à une application  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Select**|Ouvre la boîte de dialogue **Se connecter au serveur** à partir de laquelle vous vous connectez à une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sélectionnez une base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] à associer à l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sélectionnée.|  
|**Instance SQL Server**|Affiche le nom de l'instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sélectionnée qui héberge la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Cette valeur est vide jusqu'à ce que vous vous connectiez à une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sélectionniez une base de données.|  
|**Sauvegarde de la base de données**|Affiche le nom de la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] associée à l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sélectionnée. Cette valeur est vide jusqu'à ce que vous vous connectiez à une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et sélectionniez une base de données.|  
  
## <a name="enable-dqs-integration"></a>Activer l'intégration du DQS  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Activer l'intégration avec Data Quality Services**|Sélectionnez cette option pour activer les fonctionnalités Data Quality disponibles dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]. Pour plus d'informations, consultez [Activer l'intégration de Data Quality Services avec Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la base de données et le site Web pour Master Data Services](../../2014/master-data-services/set-up-the-database-and-website-for-master-data-services.md)   
 [Configuration requise pour l’application Web &#40;Master Data Services&#41;](install-windows/web-application-requirements-master-data-services.md)   
 [Créer une application Web Data Manager principale &#40;Master Data Services&#41;](install-windows/create-a-master-data-manager-web-application-master-data-services.md)   
 [MDS 2014 et erreur « Service indisponible »](https://blogs.msdn.com/b/womeninanalytics/archive/2015/08/19/mds-2014-and-service-unavailable-error.aspx)  
  
  
