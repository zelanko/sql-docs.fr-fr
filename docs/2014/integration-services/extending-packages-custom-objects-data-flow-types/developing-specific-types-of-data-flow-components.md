---
title: Développement de types spécifiques de composants de flux de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 348e219a-b8ff-425e-b9c6-811880101c54
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 92c038a3d293b63682efbba62204ad335bf0ba12
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85427906"
---
# <a name="developing-specific-types-of-data-flow-components"></a>Développement de types spécifiques de composants de flux de données
  Cette section explique de manière détaillée comment développer des composants source, des composants de transformation à sorties synchrones, des composants de transformation à sorties asynchrones et des composants de destination.  
  
 Pour plus d’informations sur le développement de composants, consultez [Développement d’un composant de flux de données personnalisé](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Développement d’un composant source personnalisé](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)  
 Contient des informations sur le développement d'un composant qui accède aux données d'une source de données externe et qui les fournit à des composants situés en aval du flux de données.  
  
 [Développement d’un composant de transformation personnalisé avec des sorties synchrones](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)  
 Contient des informations sur le développement d'un composant de transformation dont les sorties sont synchrones avec ses entrées. Ces composants n'ajoutent pas de données au flux de données, mais traitent les données pendant leur transfert.  
  
 [Développement d’un composant de transformation personnalisé avec des sorties asynchrones](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
 Contient des informations sur le développement d'un composant de transformation dont les sorties ne sont pas synchrones avec ses entrées. Ces composants reçoivent des données des composants en amont, mais ils ajoutent également des données au flux de données.  
  
 [Développement d’un composant de destination personnalisé](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)  
 Contient des informations sur le développement d'un composant qui reçoit des lignes des composants situés en amont du flux de données et qui les écrit dans une source de données externe.  
  
## <a name="reference"></a>Informations de référence  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 Contient les classes et les interfaces qui permettent de créer des composants de flux de données personnalisés.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 Contient les classes et interfaces non managées de la tâche de flux de données. Les développeurs utilisent ces dernières, ainsi que l'espace de noms <xref:Microsoft.SqlServer.Dts.Pipeline> managé, lorsqu'ils génèrent un flux de données par programme ou qu'ils créent des composants de flux de données personnalisés.  
  
![Icône de Integration Services (petite)](../media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Comparaison des solutions de script et des objets personnalisés](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Développement de types spécifiques de composants Script](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
  
  
