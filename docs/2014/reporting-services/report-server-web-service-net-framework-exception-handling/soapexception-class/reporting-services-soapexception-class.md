---
title: SoapException, classe Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f6efdfac89014116957990ef2db21cf52e76a4f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046029"
---
# <a name="reporting-services-soapexception-class"></a>Classe SoapException Reporting Services
  Vous devez traiter les erreurs [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] spécifiques que vous anticipez. Par exemple, dans une application dans laquelle vous demandez à l'utilisateur de créer un dossier, il est possible que l'utilisateur tente de créer un dossier qui existe déjà. En tant que développeur, vous n'avez pas le contrôle de ce que l'utilisateur entre dans les champs relatifs au nom de dossier et au chemin d'accès de votre application. Toutefois, vous êtes maître de l'expérience vécue par l'utilisateur lorsqu'il tente accidentellement de créer un élément qui existe déjà.  
  
 Pour faciliter l’interception de conditions d’erreur spécifiques, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] classifie un code d’erreur pour l’exception et retourne la classification de l’erreur à l’aide de propriétés de la classe **SoapException**. Pour plus d’informations, consultez « SoapException Class » dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] la documentation du kit de développement logiciel (SDK).  
  
 Le tableau suivant répertorie les propriétés publiques de la classe **SoapException**.  
  
|Propriété publique|Description|  
|---------------------|-----------------|  
|**Intervenant**|Code ayant provoqué l'exception. La valeur est l'URL à la méthode du service Web.|  
|**Detail**|Informations d'erreur spécifiques à l'application. La valeur est définie par le serveur de rapports et est au format XML. Pour plus d’informations, consultez [Detail, propriété](detail-property.md) et [Utilisation de la propriété Detail pour gérer des erreurs spécifiques](../best-practices/using-the-detail-property-to-handle-specific-errors.md).|  
|**HelpLink**|URL ou URN vers un fichier d'aide associé à l'erreur. La valeur, généralement définie par le service Web, est l'URL du Centre d'aide et de support [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. 
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] prenant en charge plusieurs liens d’aide pour les erreurs qui se produisent, le serveur de rapports définit des informations de lien d’aide dans le cadre de la propriété **Detail**. Pour plus d’informations, consultez [HelpLink, élément](helplink-element.md).|  
|**Message**|Message descriptif localisé qui décrit l'erreur. Ce texte peut apparaître dans l'interface utilisateur de l'application.|  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de la gestion des exceptions dans Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Table d'erreurs SoapException](soapexception-errors-table.md)  
  
  
