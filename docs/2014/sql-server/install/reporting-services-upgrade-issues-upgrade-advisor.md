---
title: Problèmes de mise à niveau de Reporting Services (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], upgrade issues
- Reporting Services, upgrades
- upgrading Reporting Services
- report servers [Reporting Services], upgrade issues
ms.assetid: d9663f25-98d7-4508-ae3c-55a7277211bd
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 75c3bda5d15e3930fcdeba9ca73d70128fd90336
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952058"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a>Problèmes de mise à niveau de Reporting Services (Conseiller de mise à niveau)
  Les rubriques suivantes décrivent les problèmes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui peuvent affecter votre mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les rubriques décrivent les actions que vous pouvez prendre pour atténuer l’effet de ces modifications sur votre environnement.  
  
 Le Conseiller de mise à niveau analyse une installation du serveur de rapports. Si seuls les composants clients sont installés (par exemple, si le Concepteur de rapports est le seul composant [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installé sur l'ordinateur), aucun problème ne sera signalé.  
  
 Selon la façon dont vous avez configuré votre installation, vous pouvez rencontrer des problèmes supplémentaires qui ne sont pas signalés par le Conseiller de mise à niveau. Ces problèmes n'empêchent pas la mise à niveau de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], mais ils peuvent affecter la manière dont les rapports et les applications s'exécuteront après la mise à niveau. Pour en savoir plus sur ces problèmes, consultez « Compatibilité descendante de Reporting Services » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Si vous ne pouvez pas utiliser le programme d'installation pour mettre à niveau une installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez installer une nouvelle instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et migrer votre installation existante vers la nouvelle instance. Pour plus d’informations, consultez « mettre à niveau et migrer Reporting Services » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [mettre à niveau et migrer Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
 Les rubriques suivantes décrivent les problèmes connus signalés par le Conseiller de mise à niveau et expliquent comment vous pouvez modifier votre installation existante pour permettre l'exécution d'une mise à niveau.  
  
> [!IMPORTANT]  
>  Le Conseiller de mise à niveau doit être installé sur le serveur de rapports pour analyser une instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne prend pas en charge l'analyse à distance.  
>   
>  Pour plus d’informations, consultez [installation du conseiller de mise à niveau](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Certificats clients sur le conseiller de mise à &#40;niveau du site Web Report Server&#41;](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [Des extensions personnalisées ont été détectées &#40;sur le conseiller de mise à niveau du serveur de rapports&#41;](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [Des éléments de rapport personnalisés ont été détectés &#40;sur le conseiller de mise à niveau du serveur de rapports&#41;](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [Le conseiller de mise à niveau des &#40;composants de compatibilité DESCENDANTe IIS n’a pas été détecté&#41;](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [Restriction d’adresse IP &#40;détectée par le conseiller de mise à niveau&#41;](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [Filtres ISAPI détectés sur le conseiller de &#40;mise à niveau de site du serveur de rapports&#41;](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [Des extensions obsolètes ont été détectées sur &#40;le conseiller de mise à niveau d’ordinateur du serveur de rapports&#41;](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [La base de données du serveur &#40;de rapports n’est pas configurée Advisor&#41;](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [SQL Server 2005 Groupe de service Web Report Server &#40;a détecté le conseiller de mise à niveau&#41;](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [Le conseiller de mise à &#40;niveau n’est pas spécifié dans les répertoires virtuels&#41;](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [Le répertoire virtuel a un conseiller de mise &#40;à niveau de méthode d’authentification non pris en charge&#41;](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [Modifications des limites de l’UC et de la mémoire &#40;pour SQL Server standard et le conseiller de mise à niveau d’entreprise&#41;](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [Comptes de domaine requis pour le &#40;conseiller de mise à niveau de batterie de serveurs SharePoint&#41;](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [Navigation directe vers le conseiller &#40;de mise à niveau du serveur de rapports&#41;](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [Microsoft SharePoint 2007 est installé &#40;avec le conseiller de mise à niveau&#41;](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [Microsoft SQL Server Reporting Services service partagé SharePoint est installé avec le conseiller &#40;de mise à niveau côte à côte&#41;](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [Conseiller de &#40;mise à niveau du classement moteur de base de données Server incompatible&#41;](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [Autres problèmes de mise à niveau de Reporting Services](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  
