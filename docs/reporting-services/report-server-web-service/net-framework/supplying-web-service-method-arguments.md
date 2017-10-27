---
title: "Fournissant des Arguments de méthode de Service Web | Documents Microsoft"
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
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
caps.latest.revision: 38
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 761571f88c2321c823dc240cfa9bb3ba75d9414b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="supplying-web-service-method-arguments"></a>Spécification d'arguments de méthode de service Web
  Une méthode de service Web Report Server envoie une demande au service à une URL donnée à l'aide de SOAP sur HTTP. Le service reçoit la demande, la traite, puis renvoie une réponse. Ces demandes et réponses prennent la forme de documents XML.  
  
## <a name="optional-parameters"></a>Paramètres facultatifs  
 Dans certains cas, une méthode de service Web peut comporter des paramètres d'entrée facultatifs. Même si un paramètre d’entrée pour une méthode de service Web est facultatif, vous devez toujours inclure et définir la valeur du paramètre **null** (**rien** dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]). Définition d’une valeur de paramètre **null** définit la valeur de l’élément pour ce paramètre dans la demande SOAP à **null**.  
  
 L'exemple suivant utilise la méthode <xref:ReportService2010.ReportingService2010.CreateFolder%2A> pour créer un dossier nommé Product Sales dans le dossier Sales. En fournissant un **null** valeur pour les propriétés du dossier, aucune des propriétés spécifiques à l’utilisateur sont fournis pour le dossier :  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a>Types de données complexes  
 La classe principale du service Web Report Server est l'objet <xref:ReportService2010.ReportingService2010>, que vous utilisez pour appeler les opérations SOAP ou les méthodes Web de la classe proxy. Pour prendre en charge cette classe et ses méthodes, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] inclut des types de données complexes et définis par l'utilisateur qui sont propres aux paramètres d'entrée et de sortie des méthodes de service Web. Ces types de données complexes font partie de la classe proxy générée, que vous pouvez utiliser lors du développement dans le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] environnement.  
  
 Lorsque vous générez une classe proxy, les types de données complexes définis dans le fichier WSDL sont représentés par les classes du proxy, qui incluent des propriétés qui correspondent aux divers éléments SOAP des types de données complexes. Les séquences de ces types de données deviennent des tableaux d'objets que vous pouvez énumérer dans votre code. Cela élimine le besoin d'utiliser directement les structures XML envoyées dans les messages SOAP. Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] gère cette traduction à votre place.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Service Web Report Server](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Informations techniques de référence &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  

