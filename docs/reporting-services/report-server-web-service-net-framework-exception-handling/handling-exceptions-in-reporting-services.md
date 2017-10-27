---
title: Gestion des Exceptions dans Reporting Services | Documents Microsoft
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
- SOAP [Reporting Services], exceptions
- .NET Framework [Reporting Services]
- exceptions [Reporting Services], about exception handling
- SoapException object
ms.assetid: 1a443432-2db5-48c5-bc29-433b4688082f
caps.latest.revision: 31
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 7e1472c11575ba8bed99992ec9630e408c347291
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="handling-exceptions-in-reporting-services"></a>Gestion des exceptions dans Reporting Services
  Lorsqu'une demande de client de l'API SOAP Reporting Services ne peut pas être exécutée, le serveur de rapports retourne une erreur au lieu des résultats attendus de l'appel. Lorsqu’un appel ne peut pas être exécuté, une erreur pour le service Web Report Server est retournée comme un protocole SOAP **erreur** élément XML. L’élément descriptif clé de l’erreur est le **détail** élément, qui inclut toutes les informations d’erreur fournies par le serveur de rapports, ainsi que toutes les informations d’erreur de service Web supplémentaires. Les informations de clé dans le **détail** élément est le code d’erreur de report server. En fonction du message et du code d'erreur, vous pouvez déterminer l'action appropriée suivante à prendre dans vos applications. Pour plus d'informations sur les erreurs SOAP, consultez le site Web du W3C (World Wide Consortium) à l'adresse http://www.w3.org/TR/SOAP.  
  
## <a name="soap-faults-and-the-net-framework"></a>Erreurs SOAP et le .NET Framework  
 Dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], si une erreur se produit dans une demande du client au service Web, le serveur de rapports communique l’erreur dans le code client qui appelle le service Web en levant un **SoapException** objet. Le **SoapException** encapsule les informations contenues dans une erreur SOAP. Le **détail** propriété de la **SoapException** mappe à la **détail** élément dans l’erreur SOAP. Les applications doivent intercepter le **SoapException** de l’objet avec un bloc try/catch et utiliser le **détail** propriété de la **SoapException** à prendre les mesures appropriées. Pour plus d’informations sur la **SoapException** classe et le **détail** propriété dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Reporting Services SoapException, classe](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md). Pour plus d’informations sur la **SoapException** de classe, consultez la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] documentation du Kit de développement logiciel.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété Detail](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Présentation de gestion des exceptions dans Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  

