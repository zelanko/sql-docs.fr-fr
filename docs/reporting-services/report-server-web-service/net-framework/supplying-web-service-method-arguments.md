---
title: Spécification d’arguments de méthode de service web | Microsoft Docs
description: Découvrez les arguments des méthodes de service web dans Reporting Services, y compris les paramètres facultatifs et les types de données complexes.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 112db971dd632b5114c8a05f9642b740335de03f
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "79198546"
---
# <a name="supplying-web-service-method-arguments"></a>Spécification d'arguments de méthode de service Web
  Une méthode de service Web Report Server envoie une demande au service à une URL donnée à l'aide de SOAP sur HTTP. Le service reçoit la demande, la traite, puis renvoie une réponse. Ces demandes et réponses prennent la forme de documents XML.  
  
## <a name="optional-parameters"></a>Paramètres facultatifs  
 Dans certains cas, une méthode de service Web peut comporter des paramètres d'entrée facultatifs. Quand bien même un paramètre d’entrée d’une méthode de service web est facultatif, vous devez quand même l’inclure et lui affecter la valeur **null** (**Nothing** en [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]). L’affectation de la valeur **null** à un paramètre permet d’affecter la valeur **null** à l’élément de ce paramètre dans la requête SOAP.  
  
 L'exemple suivant utilise la méthode <xref:ReportService2010.ReportingService2010.CreateFolder%2A> pour créer un dossier nommé Product Sales dans le dossier Sales. En spécifiant la valeur **null** pour les propriétés du dossier, aucune propriété propre à l’utilisateur n’est fournie pour le dossier :  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a>Types de données complexes  
 La classe principale du service Web Report Server est l'objet <xref:ReportService2010.ReportingService2010>, que vous utilisez pour appeler les opérations SOAP ou les méthodes Web de la classe proxy. Pour prendre en charge cette classe et ses méthodes, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] inclut des types de données complexes et définis par l'utilisateur qui sont propres aux paramètres d'entrée et de sortie des méthodes de service Web. Ces types de données complexes font partie de la classe proxy générée, que vous pouvez utiliser dans le cadre d’un développement dans l’environnement [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Lorsque vous générez une classe proxy, les types de données complexes définis dans le fichier WSDL sont représentés par les classes du proxy, qui incluent des propriétés qui correspondent aux divers éléments SOAP des types de données complexes. Les séquences de ces types de données deviennent des tableaux d'objets que vous pouvez énumérer dans votre code. Cela élimine le besoin d'utiliser directement les structures XML envoyées dans les messages SOAP. Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] gère cette traduction à votre place.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’applications à l’aide du service web et du .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service web Report Server](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
