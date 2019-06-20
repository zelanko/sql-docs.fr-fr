---
title: Bonnes pratiques pour la gestion des exceptions dans Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fd38e382cc0b34de0498dd5ed9ce0237a5a1e07f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63046131"
---
# <a name="best-practices-for-reporting-services-exception-handling"></a>Meilleures pratiques pour la gestion des exceptions Reporting Services
  Lors du développement d'applications [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], vous disposez de plusieurs méthodologies pour supprimer ou réduire les exceptions. En cas d'exceptions, fournissez des informations claires et concises à l'utilisateur sous la forme de messages d'erreur, et prévoyez une gestion adéquate des exceptions pour empêcher vos applications de se terminer de façon inattendue.  
  
 Une application qui envoie des demandes au service Web Report Server doit effectuer les opérations suivantes :  
  
-   Éviter de provoquer des exceptions en empêchant le plus grand nombre possible de demandes non valides.  
  
-   Intercepter des exceptions et fournir le code spécifique de gestion des erreurs autant que possible.  
  
-   Traiter les cas d'erreur qui ne lèvent pas d'exceptions.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Éviter les requêtes non valides](preventing-invalid-requests.md)|Décrit des techniques pour empêcher l'envoi au serveur de rapports de demandes qui ne sont pas valides.|  
|[Utilisation des blocs Try/Catch](using-try-and-catch-blocks.md)|Décrit comment améliorer la fiabilité de votre application à l'aide des blocs try et catch.|  
|[Gestion des avertissements et des erreurs qui ne lèvent pas d'exceptions](handling-warnings-and-cases-that-do-not-cause-exceptions.md)|Explique comment gérer des erreurs qui ne provoquent pas la levée d'une exception par [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Utilisation de la propriété des détails pour gérer des erreurs spécifiques](using-the-detail-property-to-handle-specific-errors.md)|Explique comment gérer par programmation des erreurs spécifiques en utilisant la propriété **Detail** de l’objet **SoapException**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Detail, propriété](../soapexception-class/detail-property.md)   
 [Présentation de la gestion des exceptions dans Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException Reporting Services](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
