---
title: Gestion des exceptions dans Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], exceptions
- .NET Framework [Reporting Services]
- exceptions [Reporting Services], about exception handling
- SoapException object
ms.assetid: 1a443432-2db5-48c5-bc29-433b4688082f
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3cecbb0fcdbaae51e53c5277402b264d9c2468ba
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068409"
---
# <a name="handling-exceptions-in-reporting-services"></a>Gestion des exceptions dans Reporting Services
  Lorsqu'une demande de client de l'API SOAP Reporting Services ne peut pas être exécutée, le serveur de rapports retourne une erreur au lieu des résultats attendus de l'appel. Quand un appel ne peut pas être passé, une erreur pour le service web Report Server est retournée sous la forme d’élément XML **Fault** SOAP. L’élément descriptif principal de l’erreur est l’élément **detail**, qui inclut toutes les informations sur l’erreur fournies par le serveur de rapports, ainsi que d’éventuelles informations supplémentaires sur l’erreur du service web. L’information essentielle de l’élément **detail** est le code d’erreur du serveur de rapports. En fonction du message et du code d'erreur, vous pouvez déterminer l'action appropriée suivante à prendre dans vos applications. Pour plus d'informations sur les erreurs SOAP, consultez le site Web du W3C (World Wide Consortium) à l'adresse http://www.w3.org/TR/SOAP.  
  
## <a name="soap-faults-and-the-net-framework"></a>Erreurs SOAP et le .NET Framework  
 Dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], si une erreur se produit dans une requête de client au service web, le serveur de rapports communique l’erreur au code client qui appelle le service web en levant un objet **SoapException**. L’objet **SoapException** inclut dans un wrapper les informations contenues dans une erreur SOAP. La propriété **Detail** de **SoapException** est mappée à l’élément **detail** dans l’erreur SOAP. Les applications doivent intercepter l’objet **SoapException** avec un bloc try/catch et utiliser la propriété **Detail** de **SoapException** pour prendre la mesure appropriée. Pour plus d’informations sur la classe **SoapException** et la propriété **Detail** dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [SoapException, classe Reporting Services](soapexception-class/reporting-services-soapexception-class.md). Pour plus d’informations sur la classe **SoapException**, consultez la documentation du SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Detail, propriété](soapexception-class/detail-property.md)   
 [Présentation de la gestion des exceptions dans Reporting Services](introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException Reporting Services](soapexception-class/reporting-services-soapexception-class.md)  
  
  
