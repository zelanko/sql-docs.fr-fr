---
title: Spécification d’arguments de méthode de service web | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ef5188934628589751fe92d1839da0efb265766
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62522225"
---
# <a name="supplying-web-service-method-arguments"></a>Spécification d'arguments de méthode de service Web
  Une méthode de service Web Report Server envoie une demande au service à une URL donnée à l'aide de SOAP sur HTTP. Le service reçoit la demande, la traite, puis renvoie une réponse. Ces demandes et réponses prennent la forme de documents XML.  
  
## <a name="optional-parameters"></a>Paramètres facultatifs  
 Dans certains cas, une méthode de service Web peut comporter des paramètres d'entrée facultatifs. Quand bien même un paramètre d'entrée d'une méthode de service Web est facultatif, vous devez quand même l'inclure et lui affecter la valeur `null` (`Nothing` dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]). L'affectation de la valeur `null` à un paramètre permet d'affecter la valeur `null` à l'élément de ce paramètre dans la demande SOAP.  
  
 L'exemple suivant utilise la méthode <xref:ReportService2010.ReportingService2010.CreateFolder%2A> pour créer un dossier nommé Product Sales dans le dossier Sales. En spécifiant la valeur `null` pour les propriétés du dossier, aucune propriété propre à l'utilisateur n'est fournie pour le dossier :  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a>Types de données complexes  
 La classe principale du service Web Report Server est l'objet <xref:ReportService2010.ReportingService2010>, que vous utilisez pour appeler les opérations SOAP ou les méthodes Web de la classe proxy. Pour prendre en charge cette classe et ses méthodes, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] inclut des types de données complexes et définis par l'utilisateur qui sont propres aux paramètres d'entrée et de sortie des méthodes de service Web. Ces types de données complexes font partie de la classe proxy générée, que vous pouvez utiliser dans le cadre d’un développement dans l’environnement [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Lorsque vous générez une classe proxy, les types de données complexes définis dans le fichier WSDL sont représentés par les classes du proxy, qui incluent des propriétés qui correspondent aux divers éléments SOAP des types de données complexes. Les séquences de ces types de données deviennent des tableaux d'objets que vous pouvez énumérer dans votre code. Cela élimine le besoin d'utiliser directement les structures XML envoyées dans les messages SOAP. Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] gère cette traduction à votre place.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’applications à l’aide du service web et du .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service web Report Server](../report-server-web-service.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  
