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
ms.openlocfilehash: 0e2f39ea7b911f2ca83767dcfbfd82947acd4f52
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059006"
---
# <a name="reporting-services-upgrade-issues-upgrade-advisor"></a>Problèmes de mise à niveau de Reporting Services (Conseiller de mise à niveau)
  Les rubriques suivantes décrivent les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] problèmes qui peuvent affecter votre mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Les rubriques décrivent les actions que vous pouvez prendre pour atténuer l’effet de ces modifications sur votre environnement.  
  
 Le Conseiller de mise à niveau analyse une installation du serveur de rapports. Si seuls les composants clients sont installés (par exemple, si le Concepteur de rapports est le seul composant [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installé sur l'ordinateur), aucun problème ne sera signalé.  
  
 Selon la façon dont vous avez configuré votre installation, vous pouvez rencontrer des problèmes supplémentaires qui ne sont pas signalés par le Conseiller de mise à niveau. Ces problèmes n'empêchent pas la mise à niveau de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], mais ils peuvent affecter la manière dont les rapports et les applications s'exécuteront après la mise à niveau. Pour en savoir plus sur ces problèmes, consultez « Compatibilité descendante de Reporting Services » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Si vous ne pouvez pas utiliser le programme d'installation pour mettre à niveau une installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez installer une nouvelle instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et migrer votre installation existante vers la nouvelle instance. Pour plus d’informations, consultez « mettre à niveau et migrer Reporting Services » dans la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentation en ligne, [mettre à niveau et migrer Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
 Les rubriques suivantes décrivent les problèmes connus signalés par le Conseiller de mise à niveau et expliquent comment vous pouvez modifier votre installation existante pour permettre l'exécution d'une mise à niveau.  
  
> [!IMPORTANT]  
>  Le Conseiller de mise à niveau doit être installé sur le serveur de rapports pour analyser une instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne prend pas en charge l'analyse à distance.  
>   
>  Pour plus d’informations, consultez [installation du conseiller de mise à niveau](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Certificats clients sur le site Web du serveur de rapports &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/client-certificates-on-the-report-server-web-site-upgrade-advisor.md)  
  
-   [Des extensions personnalisées ont été détectées sur le serveur de rapports &#40;le conseiller de mise à niveau&#41;](../../../2014/sql-server/install/custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [Des éléments de rapport personnalisés ont été détectés sur le serveur de rapports &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)  
  
-   [Les composants de compatibilité descendante IIS n’ont pas été détectés &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)  
  
-   [Restriction d’adresse IP détectée &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/ip-address-restriction-detected-upgrade-advisor.md)  
  
-   [Filtres ISAPI détectés sur le site du serveur de rapports &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)  
  
-   [Des extensions obsolètes ont été détectées sur l’ordinateur du serveur de rapports &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)  
  
-   [La base de données du serveur de rapports n’est pas configurée &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/report-server-database-is-not-configured-upgrade-advisor.md)  
  
-   [SQL Server groupe de services Web du serveur de rapports 2005 détecté &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)  
  
-   [Les répertoires virtuels ne sont pas spécifiés &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/virtual-directories-are-unspecified-upgrade-advisor.md)  
  
-   [Le répertoire virtuel a une méthode d’authentification non prise en charge &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)  
  
-   [Modifications des limites de l’UC et de la mémoire pour SQL Server Standard et Enterprise &#40;le conseiller de mise à niveau&#41;](../../../2014/sql-server/install/cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)  
  
-   [Comptes de domaine requis pour la batterie de serveurs SharePoint &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)  
  
-   [Navigation directe vers le conseiller de mise à niveau &#40;du serveur de rapports&#41;](../../../2014/sql-server/install/direct-browsing-to-report-server-upgrade-advisor.md)  
  
-   [Microsoft SharePoint 2007 est installé &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)  
  
-   [Microsoft SQL Server Reporting Services service partagé SharePoint est installé côte à côte &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)  
  
-   [Le conseiller de mise à niveau de Moteur de base de données Server &#40;&#41;](../../../2014/sql-server/install/incompatible-database-engine-server-collation-upgrade-advisor.md)  
  
-   [Autres problèmes de mise à niveau de Reporting Services](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)  
  
  
