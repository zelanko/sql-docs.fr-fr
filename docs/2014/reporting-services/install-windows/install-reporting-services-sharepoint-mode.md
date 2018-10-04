---
title: Installation en Mode SharePoint (SharePoint 2010 et SharePoint 2013) de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b1406c93a798df2b19f49d3a83123221826d1bf1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170819"
---
# <a name="reporting-services-sharepoint-mode-installation-sharepoint-2010-and-sharepoint-2013"></a>Installation du mode SharePoint de Reporting Services (SharePoint 2010 et SharePoint 2013)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint est une collection de composants serveur qui fournissent la génération de rapports et de remise, basées sur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[msCoName](../../includes/msconame-md.md)] les produits SharePoint.  
  
 L'exécution de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint fournit [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] et les fonctionnalités d'alerte de données. Pour plus d’informations sur les fonctionnalités en mode SharePoint, consultez la section « Différences en matière de prise en charge et de comportement des fonctionnalités en fonction du mode de serveur » dans [Serveur de rapports Reporting Services](../reporting-services-report-server.md).  
  
 Il existe deux installations fondamentales nécessaires pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint :  
  
|Installation|Description|  
|------------------|-----------------|  
|Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] complément pour les produits SharePoint.|Le complément installe les pages et les fonctionnalités de l'interface utilisateur de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un serveur Web frontal SharePoint. Les fonctionnalités d'interface utilisateur incluent [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], les pages d'administration dans l'Administration centrale de SharePoint, les pages de fonctionnalités utilisées dans les bibliothèques de documents SharePoint et pages d'alerte de données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] serveur de rapports installé en SharePoint Mode|Le serveur de rapports gère les données et le traitement et le rendu des rapports, ainsi que le traitement des abonnement et des alertes de données. Le serveur de rapports en mode SharePoint est conçu et installé en tant que service partagé SharePoint.|  
  
 Pour installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], utilisez le support d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Pour obtenir des instructions sur les scénarios de déploiement avancés, consultez [liste de vérification de déploiement : Reporting Services, Power View et PowerPivot pour SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) et [liste de vérification de déploiement : installer Reporting Services dans un existant Batterie de serveurs SharePoint](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en charge les combinaisons de SharePoint et Reporting Services serveur et complément &#40;SQL Server 2014&#41;](supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [Installer le Mode SharePoint de Reporting Services pour SharePoint 2013](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
 [Installer le mode SharePoint de Reporting Services pour SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 [Installer ou désinstaller le complément Services Reporting pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [Où trouver le complément Reporting Services pour les produits SharePoint](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [Ajouter un serveur de rapports supplémentaire à une batterie de serveurs &#40;SSRS Scale-out&#41;](add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [Ajouter un serveur Web frontal Reporting Services supplémentaire à un pool](add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Configurer la messagerie électronique pour l’Application de Service pour Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41;](configure-e-mail-for-a-reporting-services-service-application.md)  
  
 [Approvisionner les abonnements et les alertes pour les applications de service de SSRS](provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Service de jeton de revendications vers Windows &#40;C2WTS&#41; et Reporting Services](../../sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture et flux de travail des alertes de données](../reporting-services-data-alerts.md#AlertingWF)   
 [Gestionnaire des alertes de données pour les administrateurs d'alertes](../data-alert-manager-for-alerting-administrators.md)  
  
  
