---
title: Présentation de la gestion des exceptions dans Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
caps.latest.revision: 28
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: de3d63926b2dfde735403b21f5c986d5b4241198
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143427"
---
# <a name="introducing-exception-handling-in-reporting-services"></a>Présentation de la gestion des exceptions dans Reporting Services
  Si votre application [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] envoie un demande au service Web Report Server, mais que ce dernier ne parvient pas à la traiter, le service retourne une exception SOAP au client. La gestion des exceptions levées par le service Web Report Server est une composante importante des applications que vous développez car vous avez la possibilité de retourner des informations utiles aux utilisateurs lorsque des erreurs se produisent.  
  
 Cette section contient des informations sur la gestion des exceptions, la manière d'éviter les entrées utilisateur non valides et l'envoi d'informations pertinentes sur les erreurs aux utilisateurs. Pour obtenir des informations générales sur la gestion des exceptions, consultez « Gestion et levée des exceptions » dans la documentation du SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Gestion des exceptions dans Reporting Services](handling-exceptions-in-reporting-services.md)|Fournit une vue d'ensemble des exceptions dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et le rôle de SOAP dans le renvoi d'erreurs depuis un service Web.|  
|[Meilleures pratiques pour la gestion des exceptions dans Reporting Services](best-practices/best-practices-for-reporting-services-exception-handling.md)|Fournit des recommandations sur la manière de gérer les exceptions dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[Classe SoapException Reporting Services](soapexception-class/reporting-services-soapexception-class.md)|Décrit la classe **SoapException** dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications à l’aide du service web et de .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  