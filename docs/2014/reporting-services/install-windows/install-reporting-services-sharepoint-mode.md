---
title: Reporting Services l’installation en mode SharePoint (SharePoint 2010 et SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef049b4ded6408e651d5ec2c3db99c10bf7c27b6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108767"
---
# <a name="reporting-services-sharepoint-mode-installation-sharepoint-2010-and-sharepoint-2013"></a>Installation du mode SharePoint de Reporting Services (SharePoint 2010 et SharePoint 2013)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]en mode SharePoint est un ensemble de composants serveur qui assurent la génération et la remise de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rapports [!INCLUDE[msCoName](../../includes/msconame-md.md)] , basés sur les produits et SharePoint.  
  
 L'exécution de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint fournit [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] et les fonctionnalités d'alerte de données. Pour plus d’informations sur les fonctionnalités en mode SharePoint, consultez la section « prise en charge des fonctionnalités et différences de comportement par le mode serveur » dans [Reporting Services Report Server](../reporting-services-report-server.md)  
  
 Il existe deux installations fondamentales nécessaires pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint :  
  
|Installation|Description|  
|------------------|-----------------|  
|Complément [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint.|Le complément installe les pages et les fonctionnalités de l'interface utilisateur de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur un serveur Web frontal SharePoint. Les fonctionnalités d'interface utilisateur incluent [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], les pages d'administration dans l'Administration centrale de SharePoint, les pages de fonctionnalités utilisées dans les bibliothèques de documents SharePoint et pages d'alerte de données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .|  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] serveur de rapports installé en mode SharePoint|Le serveur de rapports gère les données et le traitement et le rendu des rapports, ainsi que le traitement des abonnement et des alertes de données. Le serveur de rapports en mode SharePoint est conçu et installé en tant que service partagé SharePoint.|  
  
 Pour installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], utilisez le support d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Pour obtenir des instructions sur les scénarios de déploiement avancé, consultez [liste de vérification du déploiement : Reporting Services, Power View et PowerPivot pour SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md) et liste de vérification du [déploiement : installer Reporting Services dans une batterie de serveurs SharePoint existante](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Combinaisons prises en charge de SharePoint et Reporting Services Server et des compléments &#40;SQL Server 2014&#41;](supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [Installer le mode SharePoint de Reporting Services pour SharePoint 2013](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
 [Installer Reporting Services mode SharePoint pour SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 [Installer ou désinstaller le complément Reporting Services pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [Où trouver le complément Reporting Services pour les produits SharePoint](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [Ajouter un serveur de rapports supplémentaire à une batterie &#40;montée en puissance SSRS&#41;](add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [Ajouter un serveur Web frontal Reporting Services supplémentaire à une batterie](add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Configurer la messagerie électronique pour une application de service Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41;](configure-e-mail-for-a-reporting-services-service-application.md)  
  
 [Configurer les abonnements et les alertes pour les applications de service de SSRS](provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Service d’jetons Revendications vers Windows &#40;C2WTS&#41; et Reporting Services](../../sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture et flux de travail des alertes de données](../reporting-services-data-alerts.md#AlertingWF)   
 [Gestionnaire des alertes de données pour les administrateurs d’alertes](../data-alert-manager-for-alerting-administrators.md)  
  
  
