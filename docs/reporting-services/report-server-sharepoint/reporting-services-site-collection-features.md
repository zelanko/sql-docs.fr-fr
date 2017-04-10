---
title: "Fonctionnalit&#233;s de collection de sites de Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
caps.latest.revision: 8
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Fonctionnalit&#233;s de collection de sites de Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit trois fonctionnalités de collection de sites SharePoint. Les fonctionnalités prennent en charge l’environnement de création de rapports général du mode SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], une fonctionnalité du complément [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition, et les opérations de gestion de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans l’Administration centrale de SharePoint.  
  
## Fonctionnalités de la collection de sites  
 Le tableau ci-dessous décrit les fonctionnalités de la collection de sites [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|**Fonctionnalité Administration centrale du serveur de rapports**|Active les fonctionnalités de gestion de l'intégration avec un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Cette fonctionnalité est uniquement installée et utilisée dans la collection de sites Administration centrale de SharePoint.<br /><br /> La fonctionnalité d’intégration du serveur de rapports est activée automatiquement dans la collection de sites Administration centrale de SharePoint après l’installation du complément [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] pour les produits SharePoint. Dans certaines circonstances, vous devrez activer la fonctionnalité manuellement. Pour activer la fonctionnalité de serveur de rapports, utilisez les pages [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de la page Paramètres du site de l'Administration centrale de SharePoint.<br /><br /> La version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et les versions ultérieures du complément pour les produits SharePoint activent la fonctionnalité d’intégration du serveur de rapports pour toutes les collections de sites existantes pendant l’installation du complément. En outre, la fonctionnalité sera automatiquement active pour les nouvelles collections de sites.|  
|**Fonctionnalité d'intégration du serveur de rapports**|Active la création de rapports détaillés à l'aide de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<br /><br /> Cette fonctionnalité est activée par défaut.|  
|**Fonctionnalité d'intégration de Power View**|Active l’exploration interactive de données et la présentation visuelle dans les classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et les bases de données tabulaires Analysis Services.<br /><br /> Cette fonctionnalité est accessible via les menus contextuels des sources de données suivantes :<br /><br /> **.rdlx**<br /><br /> **.rsds**<br /><br /> fichier de connexion**.bism** <br /><br /> <br /><br /> Si [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] n'apparaît pas dans les menus contextuels, vérifiez que **Fonctionnalité d'intégration de Power View** est activé.<br /><br /> Cette fonctionnalité est désactivée par défaut.|  
  
## Voir aussi  
 [Activer les fonctionnalités d'intégration Report Server et Power View dans SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Paramètres et fonctions du site Reporting Services &#40;mode SharePoint&#41;](../../reporting-services/report-server-sharepoint/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [Activer la fonctionnalité Synchronisation de fichiers de serveur de rapports dans l'Administration centrale de SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  
  
  