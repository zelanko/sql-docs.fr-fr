---
title: Omission de valeurs pour les objets de Service Web facultatifs | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
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
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 890b0d174e5277f45db91db23725ae203edf4e2f
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="omitting-values-for-optional-web-service-objects"></a>Omission de valeurs pour les objets de service Web facultatifs
  Propriétés de plusieurs des types complexes de service Web Report Server ont suivie d’une propriété connue en tant que la propriété spécifiée. Lorsque c'est le cas, le nom des propriétés se compose de leur nom original suivi de la mention « Specified ». La présence de cette mention signifie que certaines valeurs des propriétés peuvent parfois être omises. Ce phénomène est la conséquence directe de la conversion à partir du langage WSDL (Web Service Description Language) dans une classe proxy du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Par exemple, la propriété de service Web <xref:ReportService2010.DataSourceDefinition.Enabled%2A> de type complexe <xref:ReportService2010.DataSourceDefinition> est suivie d'une propriété intitulée <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>. Si vous créez une application et que vous ne souhaitez pas définir une valeur pour le <xref:ReportService2010.DataSourceDefinition.Enabled%2A> propriété, il est inutile de fournir une valeur pour <xref:ReportService2010.DataSourceDefinition.Enabled%2A>; la valeur par défaut **true** est utilisé. Toutefois, vous devez toujours définir <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> à **false**. Si vous fournissez une valeur pour le <xref:ReportService2010.DataSourceDefinition.Enabled%2A> propriété, vous devez définir <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> égal à **true**. Seules les propriétés accessibles en écriture nécessitent de respecter cette condition. En revanche, les propriétés en lecture seule ne requièrent aucune action de votre part.  
  
> [!IMPORTANT]  
>  Si vous ne parvenez pas à spécifier une propriété en suivant la procédure mentionnée ci-avant, le comportement du service Web peut se révéler imprévisible.  
  
 Les types de données qui vous permet de gérer la propriété Specified supplémentaire nécessitent généralement sont **booléenne**, **DateTime**, et **énumération**.  
  
 Pour obtenir un exemple, consultez la méthode <xref:ReportService2010.ReportingService2010.CreateDataSource%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’Applications à l’aide du Service Web et le .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Informations techniques de référence &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
