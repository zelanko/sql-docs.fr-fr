---
title: Installer Reporting Services en Mode SharePoint | Documents Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 06/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b2c77f21304b04b5349691b6c464026fe944a4eb
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="install-reporting-services-sharepoint-mode"></a>Installer le mode SharePoint de Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans SharePoint permet non seulement de créer des rapports et de les afficher dans des bibliothèques de documents, mais également de distribuer les rapports dans le cadre d’un abonnement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] par courrier électronique, via  [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]ou grâce à des alertes de données et des fonctionnalités de gestion de rapports, le tout dans un déploiement de base de [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint. Pour plus d’informations sur les fonctionnalités en mode SharePoint, consultez la section « Différences en matière de prise en charge et de comportement des fonctionnalités en fonction du mode de serveur » dans [Serveur de rapports Reporting Services](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md).  
  
 Vous devez installer deux composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] essentiels pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint :  
  
|Installation|Description|  
|------------------|-----------------|  
|**Serveur de rapports :** le serveur de rapports [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installé en mode SharePoint|Le serveur de rapports gère les données et le traitement et le rendu des rapports, ainsi que le traitement des abonnement et des alertes de données. Le serveur de rapports en mode SharePoint est conçu et installé en tant que service partagé SharePoint.<br /><br /> **Modalités :** utilisez le support d’installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour installer le serveur de rapports.|  
|**Add-in:** The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products, **rssharepoint.msi**.|Le complément installe les pages et les fonctionnalités de l'interface utilisateur de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un serveur Web frontal SharePoint. Les fonctionnalités d'interface utilisateur incluent [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], les pages d'administration dans l'Administration centrale de SharePoint, les pages de fonctionnalités utilisées dans les bibliothèques de documents SharePoint et pages d'alerte de données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .<br /><br /> **Modalités**  : le complément peut être installé à partir d’un téléchargement en ligne ou du support d’installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Combinaisons de serveur et complément SharePoint et Reporting Services prises en charge &#40;SQL Server 2016&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [Où trouver le complément Reporting Services pour les produits SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [Installer le premier serveur de rapports en mode SharePoint](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md)  
  
 [Installer ou désinstaller le complément Reporting Services pour SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [Ajouter un serveur de rapports supplémentaire à une batterie &#40;montée en puissance SSRS&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [Ajouter un serveur Web frontal Reporting Services supplémentaire à une batterie](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Configurer la messagerie électronique pour une application de service Reporting Services &#40;SharePoint 2013 et SharePoint 2016&#41;](http://msdn.microsoft.com/en-us/38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f)  
  
 [Configurer les abonnements et les alertes pour les applications de service de SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Service d’émission de jetons Revendications vers Windows &#40;c2WTS&#41; et Reporting Services](../../reporting-services/install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture des alertes de données et flux de travail](../../reporting-services/reporting-services-data-alerts.md#AlertingWF)   
 [Gestionnaire des alertes de données pour les administrateurs d'alertes](../../reporting-services/data-alert-manager-for-alerting-administrators.md)  
  
  

