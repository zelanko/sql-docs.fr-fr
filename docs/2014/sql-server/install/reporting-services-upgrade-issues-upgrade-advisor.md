---
title: Problèmes (Conseiller de mise à niveau) de la mise à niveau des Services de création de rapports | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], upgrade issues
- Reporting Services, upgrades
- upgrading Reporting Services
- report servers [Reporting Services], upgrade issues
ms.assetid: d9663f25-98d7-4508-ae3c-55a7277211bd
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ed4ae6c15a16c3db009145f7daa995988ac04fbf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227499"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a>Problèmes de mise à niveau de Reporting Services (Conseiller de mise à niveau)
  Les rubriques suivantes décrivent les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] problèmes susceptibles d’affecter votre mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les rubriques décrivent les mesures que vous pouvez prendre pour atténuer l’effet de ces modifications sur votre environnement.  
  
 Le Conseiller de mise à niveau analyse une installation du serveur de rapports. Si seuls les composants clients sont installés (par exemple, si le Concepteur de rapports est le seul composant [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installé sur l'ordinateur), aucun problème ne sera signalé.  
  
 Selon la façon dont vous avez configuré votre installation, vous pouvez rencontrer des problèmes supplémentaires qui ne sont pas signalés par le Conseiller de mise à niveau. Ces problèmes n'empêchent pas la mise à niveau de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], mais ils peuvent affecter la manière dont les rapports et les applications s'exécuteront après la mise à niveau. Pour en savoir plus sur ces problèmes, consultez « Compatibilité descendante de Reporting Services » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Si vous ne pouvez pas utiliser le programme d'installation pour mettre à niveau une installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez installer une nouvelle instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et migrer votre installation existante vers la nouvelle instance. Pour plus d’informations, consultez « Mise à niveau et migrer Reporting Services » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne, [mise à niveau et migrer Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
 Les rubriques suivantes décrivent les problèmes connus signalés par le Conseiller de mise à niveau et expliquent comment vous pouvez modifier votre installation existante pour permettre l'exécution d'une mise à niveau.  
  
> [!IMPORTANT]  
>  Le Conseiller de mise à niveau doit être installé sur le serveur de rapports pour analyser une instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne prend pas en charge l'analyse à distance.  
>   
>  Pour plus d’informations, consultez [Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Certificats clients sur le site web de serveur de rapports &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [Extensions personnalisées ont été détectées sur le serveur de rapports &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [Éléments de rapport personnalisés ont été détectées sur le serveur de rapports &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [Composants de compatibilité descendante IIS n’ont pas été détectés &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [Restriction d’adresse IP détectée &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [Filtres ISAPI détectés sur le site de serveur de rapports &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [Des extensions obsolètes ont été détectées sur l’ordinateur de serveur de rapports &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [Base de données du serveur de rapports n’est pas configuré &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [Groupe de Service Web de SQL Server 2005 Report Server a détecté &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [Répertoires virtuels ne sont pas spécifiés &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [Méthode d’authentification du répertoire virtuel a non pris en charge &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [Modifications des limites de processeur et mémoire pour SQL Server Standard et Enterprise &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [Comptes de domaine requis pour la batterie de serveurs SharePoint &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [Accès direct au serveur de rapports &#40;Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [Microsoft SharePoint 2007 est installé &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [Microsoft SQL Server Reporting Services Service partagé SharePoint est installé côte à côte &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [Classement de serveur du moteur de base de données incompatible &#40;Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [Autres problèmes de mise à niveau de Reporting Services](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  
