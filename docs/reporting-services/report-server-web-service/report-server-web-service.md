---
title: Service Web Report Server | Documents Microsoft
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
- SSIS, Web service
- Web service [Reporting Services]
- Reporting Services, extending
- SQL Server Reporting Services, Web service
- Reporting Services, Web service
- XML Web service [Reporting Services]
- Report Server Web service
ms.assetid: 16c21dec-6b46-4497-9a0c-1b0f2b6ab8fc
caps.latest.revision: 47
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 5fd4d415e452549e80aa12b9eb1397bf83ce6557
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="report-server-web-service"></a>service Web Report Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit l’accès aux fonctionnalités complètes du serveur de rapports via le service Web Report Server. Le service Web Report Server est un service Web XML avec une API SOAP. Il utilise SOAP sur HTTP et agit comme une interface de communication entre les programmes clients et le serveur de rapports. Le service Web fournit deux points de terminaison (un pour l'exécution des rapports et l'autre pour la gestion des rapports) avec des méthodes qui exposent les fonctionnalités du serveur de rapports et qui vous permettent de créer des outils personnalisés pour n'importe quelle partie du cycle de vie du rapport.  
  
 Il existe trois principaux moyens pour développer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications basées sur le service Web. Vous pouvez :  
  
-   Développer des applications à l’aide de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] et [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Kit de développement logiciel. Pour plus d’informations sur l’utilisation de la [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] pour générer des applications de service Web, consultez [génération d’Applications à l’aide du Service Web et le .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
-   Développer des applications à l’aide de la **rs** utilitaire (RS.exe), le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] environnement de script. Avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] des scripts, vous pouvez exécuter une des opérations de service Web Report Server. Pour plus d’informations sur les scripts [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Script avec la rs.exe utilitaire et le Service Web](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md).  
  
-   Développer des applications à l'aide de n'importe quel jeu SOAP d'outils de développement. Pour plus d’informations, consultez [The Role of SOAP dans Reporting Services](../../reporting-services/report-server-web-service/the-role-of-soap-in-reporting-services.md).  
  
## <a name="programming-diagram"></a>Diagramme de programmation  
 ![Options de développement du service Web du serveur de rapports](../../reporting-services/report-server-web-service/media/reportserviceswebserviceprog-01.gif "Report Server Web service development options")  
Options de développement de service Web disponibles dans Reporting Services  
  
## <a name="in-this-section"></a>Dans cette section  
 [Méthodes de Service Web Report Server](../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)  
 Décrit les fonctionnalités et les méthodes de chaque service Web Report Server.  
  
 [Le rôle de SOAP dans Reporting Services](../../reporting-services/report-server-web-service/the-role-of-soap-in-reporting-services.md)  
 Fournit une vue d'ensemble du protocole SOAP et de la manière dont il est utilisé dans les services Web Report Server.  
  
 [L’accès à l’API SOAP](../../reporting-services/report-server-web-service/accessing-the-soap-api.md)  
 Décrit le langage WSDL (Web Service Description Language) et fournit des URL pour accéder à un fichier WSDL Reporting Services.  
  
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
 Contient des informations sur le développement d'applications et de services Web qui appellent l'API SOAP Reporting Services.  
  
 [Script avec l’utilitaire rs.exe et le Service Web](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
 Fournit une vue d'ensemble de l'environnement de script [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Informations techniques de référence &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)  
 Contient les documents de référence spécifiques aux méthodes des services Web Report Server et aux types complexes correspondants.  
  
## <a name="user-requirements-for-web-service-development"></a>Conditions requises liées à l'utilisateur pour le développement du service Web  
 Pour développer des applications à l'aide du service Web Report Server, vous devez posséder :  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)]Internet Explorer 5.5 ou version ultérieure, installé sur un ordinateur avec une connexion Internet et l’accès au serveur de rapports.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Kit de développement logiciel installé sur un ordinateur si vous souhaitez développer et déployer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applications à l’aide de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
-   Une connaissance approfondie de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fonctionnalités et fonctions.  
  
-   de solides acquis concernant SOAP et les [!INCLUDE[vstecwebservices](../../includes/vstecwebservices-md.md)] ;  
  
-   Expérience de développement dans un [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-langage compatible comme [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], si vous envisagez d’utiliser le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] comme plateforme de développement.  
  
## <a name="see-also"></a>Voir aussi  
 [Service Web Report Server](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  

