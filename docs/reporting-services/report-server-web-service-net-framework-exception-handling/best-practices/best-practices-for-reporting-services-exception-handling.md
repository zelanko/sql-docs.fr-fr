---
title: "Meilleures pratiques pour la gestion des exceptions de Services de création de rapports | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 8f6546605af6bb6c23b6b380fbaf7042d093addf
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="best-practices-for-reporting-services-exception-handling"></a>Meilleures pratiques pour la gestion des exceptions Reporting Services
  Lors du développement d'applications [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], vous disposez de plusieurs méthodologies pour supprimer ou réduire les exceptions. En cas d'exceptions, fournissez des informations claires et concises à l'utilisateur sous la forme de messages d'erreur, et prévoyez une gestion adéquate des exceptions pour empêcher vos applications de se terminer de façon inattendue.  
  
 Une application qui envoie des demandes au service Web Report Server doit effectuer les opérations suivantes :  
  
-   Éviter de provoquer des exceptions en empêchant le plus grand nombre possible de demandes non valides.  
  
-   Intercepter des exceptions et fournir le code spécifique de gestion des erreurs autant que possible.  
  
-   Traiter les cas d'erreur qui ne lèvent pas d'exceptions.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Éviter les requêtes non valides](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/preventing-invalid-requests.md)|Décrit des techniques pour empêcher l'envoi au serveur de rapports de demandes qui ne sont pas valides.|  
|[Utilisation des blocs Try/Catch](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-try-and-catch-blocks.md)|Décrit comment améliorer la fiabilité de votre application à l'aide des blocs try et catch.|  
|[Gestion des avertissements et des erreurs qui ne lèvent pas d'exceptions](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/handling-warnings-and-cases-that-do-not-cause-exceptions.md)|Explique comment gérer des erreurs qui ne provoquent pas la levée d'une exception par [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[À l’aide de la propriété Detail pour gérer les erreurs spécifiques](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)|Explique comment gérer par programme des erreurs spécifiques à l’aide de la **détail** propriété de la **SoapException** objet.|  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété Detail](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Présentation de gestion des exceptions dans Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  

