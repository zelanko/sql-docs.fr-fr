---
title: "Création d’Applications à l’aide du Service Web et le .NET Framework | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
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
- Report Server Web service, application building
- .NET Framework [Reporting Services]
- XML Web service [Reporting Services], client creation
- reports [Reporting Services], building
- Web service [Reporting Services], application building
- Report Server Web service, client creation
- client configuration [Reporting Services]
- XML Web service [Reporting Services], application building
- Web service [Reporting Services], client creation
ms.assetid: 92a9678c-bc4f-4d7a-ba44-85989bfe27ca
caps.latest.revision: 38
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 58588838e0e74b545290df5ff0e77dc68ad5e918
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a>Building Applications Using the Web Service and the .NET Framework
  Avec la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], vous pouvez utiliser des constructions de programmation familières, telles que les méthodes, types primitifs, et les types complexes définis par l’utilisateur pour travailler avec les services Web. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] contient une infrastructure et des outils qui vous permettent de créer des clients de service Web qui peuvent appeler des services Web conformes aux normes du World Wide Web Consortium (W3C).  
  
 Un client de service Web Report Server est un composant ou une application qui communique avec un serveur de rapports à l'aide des messages SOAP.  
  
 **Pour créer un client de service Web Report Server à l’aide de .NET Framework, suivez ces étapes de base :**  
  
1.  Créez une classe proxy pour le service Web.  
  
     Pour ce faire, ajoutez une classe proxy ou une référence Web à votre projet de développement, référencez la classe proxy dans votre code client et créez une instance de ce proxy. Pour plus d’informations, consultez [création du Proxy de Service Web](../../../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md).  
  
2.  Authentifiez le client de service Web avec le serveur de rapports.  
  
     Pour cela, définissez la propriété <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> de l'objet du service pour qu'elle soit équivalente aux informations d'identification d'un utilisateur authentifié sur le serveur de rapports. Pour plus d’informations, consultez [l’authentification du Service Web](../../../reporting-services/report-server-web-service/net-framework/web-service-authentication.md).  
  
3.  Appelez la méthode de la classe proxy qui correspond à l'opération de service Web que vous souhaitez appeler.  
  
     Pour ce faire, appelez une méthode de service Web et fournissez les arguments nécessaires. Pour plus d’informations sur les méthodes de service Web, consultez [méthodes de Service Web Report Server](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md). Pour plus d’informations sur l’appel, consultez [appelant des méthodes de Service Web](../../../reporting-services/report-server-web-service/net-framework/calling-web-service-methods.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Création du Proxy de Service Web](../../../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md)|Décrit les façons d’ajouter une classe proxy dans votre projet en utilisant [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].|  
|[Authentification du Service Web](../../../reporting-services/report-server-web-service/net-framework/web-service-authentication.md)|Explique comment les appels vers le service Web Report Server sont authentifiés.|  
|[Appel de méthodes de Service Web](../../../reporting-services/report-server-web-service/net-framework/calling-web-service-methods.md)|Décrit comment utiliser l’API SOAP pour appeler des méthodes de service Web dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].|  
|[Définition de la propriété Url du Service Web](../../../reporting-services/report-server-web-service/net-framework/setting-the-url-property-of-the-web-service.md)|Explique comment diriger par programme votre proxy de service Web vers une nouvelle URL du serveur après avoir créé votre référence Web.|  
|[Fournissant des Arguments de méthode de Service Web](../../../reporting-services/report-server-web-service/net-framework/supplying-web-service-method-arguments.md)|Décrit comment appeler une méthode de service Web et fournir des arguments de méthode.|  
|[Omission de valeurs pour les objets de Service Web facultatifs](../../../reporting-services/report-server-web-service/net-framework/omitting-values-for-optional-web-service-objects.md)|Décrit comment omettre des valeurs pour des objets de service Web facultatifs.|  
|[À l’aide des méthodes de Service Web sécurisé](../../../reporting-services/report-server-web-service/net-framework/using-secure-web-service-methods.md)|Décrit la **SecureConnectionLevel** paramètre et la façon dont il affecte l’utilisation de l’API SOAP de Reporting Services.|  
|[Passage de paramètres d’informations de périphérique aux Extensions de rendu](../../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)|Décrit les paramètres d'informations de périphérique utilisés pour effectuer un rendu des rapports dans des formats différents.|  
|[Paramètres Extension de remise Reporting Services](../../../reporting-services/report-server-web-service/net-framework/reporting-services-delivery-extension-settings.md)|Décrit les paramètres utilisés pour remettre des rapports à l'aide de la messagerie électronique du serveur de rapports.|  
|[À l’aide de Reporting Services des en-têtes SOAP](../../../reporting-services/report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|Explique l'utilisation des en-têtes SOAP dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Présentation de gestion des exceptions dans Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|Fournit des informations sur la gestion des erreurs dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Service web Report Server](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
