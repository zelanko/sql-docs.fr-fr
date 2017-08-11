---
title: "La Documentation du développeur de Reporting Services | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- developer's guide [Reporting Services]
- Reporting Services, programming
- programming [Reporting Services]
ms.assetid: d8afa405-1012-4349-a72d-e10d94f8453d
caps.latest.revision: 21
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 3704373a08b29a8f36ce843db5f67a860a04a47b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="reporting-services-developer-documentation"></a>Guide du développeur Reporting Services
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] offre plusieurs interfaces de programmation que vous pouvez tirer parti dans vos propres applications. Vous pouvez utiliser les fonctionnalités existantes de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour créer des outils de génération de rapports et de gestion personnalisés dans des sites Web et des applications Windows, ou vous pouvez étendre la plateforme [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
 L'extension de la plateforme [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] inclut la création de composants et de ressources qui peuvent être utilisées pour l'accès aux données, la remise de rapports, etc. Vous pouvez vendre ces composants et ressources aux sociétés qui utilisent [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] dans leur organisation.  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] inclut des exemples de programmation et des didacticiels pour vous aider à démarrer. Pour plus d’informations, consultez [exemples Reporting Services](https://msdn.microsoft.com/library/ms160954\(v=sql.110\).aspx) et [Guide du développeur : didacticiels (Reporting Services)](https://msdn.microsoft.com/library/aa337423\(v=sql.110\).aspx).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Intégration de Reporting Services dans des applications](../reporting-services/application-integration/integrating-reporting-services-into-applications.md)  
 Fournit une vue d'ensemble de la manière d'utiliser [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour intégrer la création de rapports dans des applications personnalisées. Décrit les situations dans lesquelles utiliser l'accès URL direct et le service Web pour accéder au serveur de rapports.  
  
 [Service Web Report Server](../reporting-services/report-server-web-service/report-server-web-service.md)  
 Le service Web Report Server donne accès aux fonctionnalités complètes du serveur de rapports. Le service Web utilise SOAP sur HTTP et est conçu pour servir d'interface de communication entre les programmes clients et le serveur de rapports. Le service Web et ses méthodes exposent les fonctionnalités du serveur de rapports et vous permettent de créer des outils personnalisés pour n'importe quelle partie du cycle de vie du rapport, depuis la gestion jusqu'à l'exécution.  
  
 [Accès URL &#40; SSRS &#41;](../reporting-services/url-access-ssrs.md)  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prend en charge un jeu complet de demandes basées sur une URL que vous pouvez utiliser comme point d'accès rapide et facile pour la navigation et la consultation des rapports. Vous pouvez utiliser cette technologie conjointement au service Web Report Server pour intégrer une solution de création de rapports complète dans vos applications de gestion personnalisées. L'accès URL s'avère particulièrement utile lors de l'intégration de rapports dans le cadre d'un portail Web ou lors de la consultation de rapports à partir d'un navigateur Web.  
  
 [Extensions Reporting Services](../reporting-services/extensions/reporting-services-extensions.md)  
 L'architecture modulaire de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est conçue à des fins d'extensibilité. Une API de code managé est disponible afin de vous permettre de développer, installer et gérer facilement des extensions consommées par de nombreux composants [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Vous pouvez créer des assemblys à l’aide de la [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] et ajouter de nouvelles [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fonctionnalités de rendu, la sécurité, remise et le traitement des données pour répondre aux besoins de votre entreprise en constante évolution.  
  
 [Éléments de rapports personnalisés](../reporting-services/custom-report-items/custom-report-items.md)  
 Décrit la manière de créer des éléments de rapports personnalisés afin d'ajouter des fonctionnalités à un élément RDL ou d'étendre certaines fonctionnalités des contrôles existants.  
  
 [Utilisation d'assemblages personnalisés avec des rapports](../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
 Décrit la manière d'utiliser des assemblys personnalisés avec des rapports en incluant des références de code dans la définition de rapport.  
  
 [Accéder au fournisseur WMI de Reporting Services](../reporting-services/tools/access-the-reporting-services-wmi-provider.md)  
 Décrit la manière d'utiliser le fournisseur WMI de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour gérer des déploiements de serveurs de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Reporting Services &#40; SSRS &#41;](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Langage de définition de rapport &#40; SSRS &#41;](../reporting-services/reports/report-definition-language-ssrs.md)   
 [Informations techniques de référence &#40; SSRS &#41;](../reporting-services/technical-reference-ssrs.md)   
 [Sécuriser le développement &#40; Reporting Services &#41;](../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
  
  
