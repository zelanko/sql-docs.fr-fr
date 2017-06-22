---
title: "Présentation de gestion des exceptions dans Reporting Services | Documents Microsoft"
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
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
caps.latest.revision: 29
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ae960b1dd8fc1020b5095e0af920464794905ee2
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="introducing-exception-handling-in-reporting-services"></a>Présentation de la gestion des exceptions dans Reporting Services
  Si votre application [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] envoie un demande au service Web Report Server, mais que ce dernier ne parvient pas à la traiter, le service retourne une exception SOAP au client. La gestion des exceptions levées par le service Web Report Server est une composante importante des applications que vous développez car vous avez la possibilité de retourner des informations utiles aux utilisateurs lorsque des erreurs se produisent.  
  
 Cette section contient des informations sur la gestion des exceptions, la manière d'éviter les entrées utilisateur non valides et l'envoi d'informations pertinentes sur les erreurs aux utilisateurs. Pour obtenir des informations générales sur la gestion des exceptions, consultez « Gestion et levée des Exceptions » dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] documentation du Kit de développement logiciel.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[La gestion des Exceptions dans Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/handling-exceptions-in-reporting-services.md)|Fournit une vue d'ensemble des exceptions dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et le rôle de SOAP dans le renvoi d'erreurs depuis un service Web.|  
|[Meilleures pratiques pour la gestion des exceptions de Services de création de rapports](../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/best-practices-for-reporting-services-exception-handling.md)|Fournit des recommandations sur la manière de gérer les exceptions dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[Classe SoapException Reporting Services](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)|Décrit la **SoapException** classe dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
