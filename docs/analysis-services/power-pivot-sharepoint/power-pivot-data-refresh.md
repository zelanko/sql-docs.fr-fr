---
title: "Actualisation des données de tableau croisé dynamique de l’alimentation | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: ac8358a3-ee71-44c7-8ee6-ac7afe3ebaa4
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1e7ea7d3193394c3fd337a3ee3211473472e43b2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="power-pivot-data-refresh"></a>Actualisation des données Power Pivot
  Une fois que vous avez créé un classeur contenant des données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , vous pouvez actualiser périodiquement les données en réexécutant une requête ou une commande afin d’obtenir les informations mises à jour à partir des sources utilisées initialement pour créer le classeur. Ce processus est appelé **actualisation des données**, et vous pouvez actualiser les données à la demande dans [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], ou de manière planifiée avec un processus [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui s’exécute sur un serveur d’applications dans une batterie de serveurs SharePoint. Pour plus d'informations, consultez :  
  
-   [Actualisation des données Power Pivot avec SharePoint 2010](http://msdn.microsoft.com/en-us/01b54e6f-66e5-485c-acaa-3f9aa53119c9)  
  
-   [Configurer le compte d’actualisation des données PowerPivot sans assistance (PowerPivot pour SharePoint)](http://msdn.microsoft.com/en-us/81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
-   [Configurer les informations d’identification stockées pour l’actualisation des données Power Pivot (Power Pivot pour SharePoint)](http://msdn.microsoft.com/en-us/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)  
  
-   [Planifier une actualisation des données (PowerPivot pour SharePoint)](http://msdn.microsoft.com/en-us/8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
-   [Afficher l’historique d’actualisation des données &#40;Power Pivot pour SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]et SharePoint Server 2013 Excel Services utilisent une architecture différente pour l’actualisation des données de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] des modèles de données. L’architecture prise en charge par SharePoint 2013 utilise Excel Services en tant que composant principal pour charger les modèles de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . L’architecture d’actualisation des données précédente reposait sur un serveur exécutant le service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint afin de charger les modèles de données. Pour plus d'informations, consultez les documents suivants :  
>   
>  -   [Actualisation des données Power Pivot avec SharePoint 2013](../../analysis-services/power-pivot-sharepoint/power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [Mettre à niveau les classeurs et l’actualisation planifiée des données &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
