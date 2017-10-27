---
title: Classe SoapException Reporting Services | Documents Microsoft
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
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: e24a518bee7b192505fc93ad26d4345f9d710143
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="reporting-services-soapexception-class"></a>Classe SoapException Reporting Services
  Vous devez traiter les erreurs [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] spécifiques que vous anticipez. Par exemple, dans une application dans laquelle vous demandez à l'utilisateur de créer un dossier, il est possible que l'utilisateur tente de créer un dossier qui existe déjà. En tant que développeur, vous n'avez pas le contrôle de ce que l'utilisateur entre dans les champs relatifs au nom de dossier et au chemin d'accès de votre application. Toutefois, vous êtes maître de l'expérience vécue par l'utilisateur lorsqu'il tente accidentellement de créer un élément qui existe déjà.  
  
 Pour faciliter l’interception de conditions d’erreur spécifiques, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] classifie un code d’erreur pour l’exception et retourne la classification de l’erreur à l’aide des propriétés à partir de la **SoapException** classe. Pour plus d’informations, consultez « Classe SoapException » dans le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] documentation du Kit de développement logiciel.  
  
 Le tableau suivant répertorie les propriétés publiques de la **SoapException** classe.  
  
|Propriété publique| Description|  
|---------------------|-----------------|  
|**Acteur**|Code ayant provoqué l'exception. La valeur est l'URL à la méthode du service Web.|  
|**Détail**|Informations d'erreur spécifiques à l'application. La valeur est définie par le serveur de rapports et est au format XML. Pour plus d’informations, consultez [propriété Detail](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md) et [à l’aide de la propriété Detail pour gérer les erreurs spécifiques](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md).|  
|**HelpLink**|URL ou URN vers un fichier d'aide associé à l'erreur. La valeur, généralement définie par le service Web, est l'URL du Centre d'aide et de support [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. Étant donné que [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] prend en charge plusieurs liens d’aide pour les erreurs qui se produisent, le serveur de rapports définit aide lier les informations dans le cadre de la **détail** propriété. Pour plus d’informations, consultez [HelpLink élément](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md).|  
|**Boîte de**|Message descriptif localisé qui décrit l'erreur. Ce texte peut apparaître dans l'interface utilisateur de l'application.|  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de gestion des exceptions dans Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Table d’erreurs SoapException](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/soapexception-errors-table.md)  
  
  

