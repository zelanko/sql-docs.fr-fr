---
title: "Intégration de Reporting Services à l’aide de SOAP | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- Report Server Web service, application integration
- SOAP [Reporting Services]
- SOAP [Reporting Services], about report integration
- integrating reports [Reporting Services]
- Web service [Reporting Services], application integration
ms.assetid: 6bc17af5-883c-4bfa-87d9-48cd7056d145
caps.latest.revision: 45
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 00c18a33dc186c5724c6812451153539571cd96c
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="integrating-reporting-services-using-soap"></a>Intégration de Reporting Services à l'aide de SOAP
  Le [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API SOAP fournit plusieurs points de terminaison de service Web de développement de solutions de création de rapports personnalisées. Les points de terminaison se répartissent actuellement dans deux catégories : la gestion et l'exécution. Les fonctionnalités de gestion sont exposées par le biais des points de terminaison <xref:ReportService2005>, <xref:ReportService2006> et <xref:ReportService2010>. Le point de terminaison <xref:ReportService2005> est utilisé pour gérer un serveur de rapports configuré en mode natif et le point de terminaison <xref:ReportService2006> est utilisé pour gérer un serveur de rapports configuré pour le mode intégré SharePoint. Le <xref:ReportService2010> fusionne les fonctionnalités de <xref:ReportService2005> et de <xref:ReportService2006> et peut gérer un serveur de rapports configuré pour le mode natif ou intégré SharePoint.  
  
> [!NOTE]  
>  Les points de terminaison <xref:ReportService2005> et <xref:ReportService2006> sont déconseillés dans [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Le point de terminaison <xref:ReportService2010> inclut les fonctionnalités des deux points de terminaison, ainsi que des fonctionnalités de gestion supplémentaires.  
  
 Les fonctionnalités d'exécution sont exposées par le biais du point de terminaison <xref:ReportExecution2005> et elles sont utilisées lorsque le serveur de rapports est configuré en mode natif ou intégré SharePoint. Les rubriques suivantes montrent comment ces points de terminaison peuvent être utilisés pour développer des solutions de création de rapports dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, SharePoint et les applications Web.  
  
## <a name="in-this-section"></a>Dans cette section  
 [À l’aide de l’API SOAP dans une Application Windows](../../reporting-services/application-integration/integrating-reporting-services-using-soap-windows-application.md)  
 Décrit comment utiliser l'API SOAP pour intégrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans un environnement Windows.  
  
 [À l’aide de l’API SOAP dans une Application Web](../../reporting-services/application-integration/integrating-reporting-services-using-soap-web-application.md)  
 Décrit comment utiliser l'API SOAP pour intégrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans un environnement Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Intégration de Reporting Services dans des Applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Service web Report Server](../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
