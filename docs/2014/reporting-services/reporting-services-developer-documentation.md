---
title: Guide des&#39;pour les développeurs (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e8c555d853fd791bed29a06f561021b138526ea1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63255102"
---
# <a name="developer39s-guide-reporting-services"></a>Guide des&#39;pour les développeurs (Reporting Services)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] offre plusieurs interfaces de programmation que vous pouvez utiliser dans vos propres applications. Vous pouvez utiliser les fonctionnalités existantes de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour créer des outils de génération de rapports et de gestion personnalisés dans des sites Web et des applications Windows, ou vous pouvez étendre la plateforme [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
 L'extension de la plateforme [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] inclut la création de composants et de ressources qui peuvent être utilisées pour l'accès aux données, la remise de rapports, etc. Vous pouvez vendre ces composants et ressources aux sociétés qui utilisent [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] dans leur organisation.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Intégration de Reporting Services dans les applications](application-integration/integrating-reporting-services-into-applications.md)  
 Fournit une vue d'ensemble de la manière d'utiliser [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour intégrer la création de rapports dans des applications personnalisées. Décrit les situations dans lesquelles utiliser l'accès URL direct et le service Web pour accéder au serveur de rapports.  
  
 [Service Web des serveurs de rapports](report-server-web-service/report-server-web-service.md)  
 Le service Web Report Server donne accès aux fonctionnalités complètes du serveur de rapports. Le service Web utilise SOAP sur HTTP et est conçu pour servir d'interface de communication entre les programmes clients et le serveur de rapports. Le service Web et ses méthodes exposent les fonctionnalités du serveur de rapports et vous permettent de créer des outils personnalisés pour n'importe quelle partie du cycle de vie du rapport, depuis la gestion jusqu'à l'exécution.  
  
 [Accès URL &#40;SSRS&#41;](url-access-ssrs.md)  
 
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge un jeu complet de demandes basées sur une URL que vous pouvez utiliser comme point d'accès rapide et facile pour la navigation et la consultation des rapports. Vous pouvez utiliser cette technologie conjointement au service Web Report Server pour intégrer une solution de création de rapports complète dans vos applications de gestion personnalisées. L'accès URL s'avère particulièrement utile lors de l'intégration de rapports dans le cadre d'un portail Web ou lors de la consultation de rapports à partir d'un navigateur Web.  
  
 [Extensions Reporting Services](extensions/reporting-services-extensions.md)  
 L'architecture modulaire de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est conçue à des fins d'extensibilité. Une API de code managé est disponible afin de vous permettre de développer, installer et gérer facilement des extensions consommées par de nombreux composants [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Vous pouvez créer des assemblys à [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] l’aide du [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et ajouter de nouvelles fonctionnalités de rendu, de sécurité, de remise et de traitement des données pour répondre à vos besoins d’entreprise en constante évolution.  
  
 [Éléments de rapport personnalisés](custom-report-items/custom-report-items.md)  
 Décrit la manière de créer des éléments de rapports personnalisés afin d'ajouter des fonctionnalités à un élément RDL ou d'étendre certaines fonctionnalités des contrôles existants.  
  
 [Utilisation d'assemblages personnalisés avec des rapports](custom-assemblies/using-custom-assemblies-with-reports.md)  
 Décrit la manière d'utiliser des assemblys personnalisés avec des rapports en incluant des références de code dans la définition de rapport.  
  
 [Accéder au fournisseur WMI de Reporting Services](tools/access-the-reporting-services-wmi-provider.md)  
 Décrit la manière d'utiliser le fournisseur WMI de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour gérer des déploiements de serveurs de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md)   
 [Informations techniques de référence &#40;SSRS&#41;](technical-reference-ssrs.md)   
 [Reporting Services de &#40;de développement sécurisé&#41;](extensions/secure-development/secure-development-reporting-services.md)  
  
  
