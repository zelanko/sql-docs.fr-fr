---
title: Génération d’applications à l’aide du service web et du .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
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
caps.latest.revision: 37
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e732d4ec998b3d1a44b28b14b4a810156f57d435
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041755"
---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a>Génération d'applications à l'aide du service Web et du .NET Framework
  Grâce au [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], vous pouvez utiliser des constructions de programmation familières, telles que des méthodes, des types primitifs et des types complexes définis par l’utilisateur pour utiliser des services web. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] contient une infrastructure et des outils qui vous permettent de créer des clients de service Web qui peuvent appeler des services Web conformes aux normes du World Wide Web Consortium (W3C).  
  
 Un client de service Web Report Server est un composant ou une application qui communique avec un serveur de rapports à l'aide des messages SOAP.  
  
 **Pour créer un client de service web Report Server à l’aide du .NET Framework, suivez les étapes de base suivantes :**  
  
1.  Créez une classe proxy pour le service Web.  
  
     Pour ce faire, ajoutez une classe proxy ou une référence Web à votre projet de développement, référencez la classe proxy dans votre code client et créez une instance de ce proxy. Pour plus d’informations, consultez [Création du proxy du service web](creating-the-web-service-proxy.md).  
  
2.  Authentifiez le client de service Web avec le serveur de rapports.  
  
     Pour cela, définissez la propriété <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> de l'objet du service pour qu'elle soit équivalente aux informations d'identification d'un utilisateur authentifié sur le serveur de rapports. Pour plus d’informations, consultez [Authentification du service web](web-service-authentication.md).  
  
3.  Appelez la méthode de la classe proxy qui correspond à l'opération de service Web que vous souhaitez appeler.  
  
     Pour ce faire, appelez une méthode de service Web et fournissez les arguments nécessaires. Pour plus d’informations sur les méthodes de service web, consultez [Méthodes du service web Report Server](../methods/report-server-web-service-methods.md). Pour plus d’informations sur l’appel, consultez [Appel des méthodes de service web](calling-web-service-methods.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Création du proxy du service web](creating-the-web-service-proxy.md)|Décrit les façons d’ajouter une classe proxy à votre projet à l’aide du [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].|  
|[Authentification du service web](web-service-authentication.md)|Explique comment les appels vers le service Web Report Server sont authentifiés.|  
|[Appel des méthodes du service web](calling-web-service-methods.md)|Explique comment utiliser l’API SOAP pour appeler des méthodes de service web dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].|  
|[Définition de la propriété Url du service web](setting-the-url-property-of-the-web-service.md)|Explique comment diriger par programme votre proxy de service Web vers une nouvelle URL du serveur après avoir créé votre référence Web.|  
|[Approvisionnement des arguments des méthodes du service web](supplying-web-service-method-arguments.md)|Décrit comment appeler une méthode de service Web et fournir des arguments de méthode.|  
|[Omission de valeurs pour les objets facultatifs du service web](omitting-values-for-optional-web-service-objects.md)|Décrit comment omettre des valeurs pour des objets de service Web facultatifs.|  
|[Utilisation des méthodes sécurisées du service web](using-secure-web-service-methods.md)|Décrit le paramètre **SecureConnectionLevel** et la façon dont il affecte l’utilisation de l’API SOAP de Reporting Services.|  
|[Transfert des paramètres d’information d’appareil aux extensions de rendu](passing-device-information-settings-to-rendering-extensions.md)|Décrit les paramètres d'informations de périphérique utilisés pour effectuer un rendu des rapports dans des formats différents.|  
|[Paramètres des extensions de remise de Reporting Services](reporting-services-delivery-extension-settings.md)|Décrit les paramètres utilisés pour remettre des rapports à l'aide de la messagerie électronique du serveur de rapports.|  
|[Utilisation d’en-têtes SOAP Reporting Services](../../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|Explique l'utilisation des en-têtes SOAP dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Présentation de la gestion des exceptions dans Reporting Services](../../report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|Fournit des informations sur la gestion des erreurs dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Service web Report Server](../report-server-web-service.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  