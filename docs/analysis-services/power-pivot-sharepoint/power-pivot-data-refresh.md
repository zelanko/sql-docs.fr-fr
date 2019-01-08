---
title: Actualisation des données de tableau croisé dynamique de l’alimentation | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 243c2649af82aad3488051da543628203699a27e
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53201749"
---
# <a name="power-pivot-data-refresh"></a>Actualisation des données Power Pivot
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Une fois que vous avez créé un classeur contenant des données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , vous pouvez actualiser périodiquement les données en réexécutant une requête ou une commande afin d’obtenir les informations mises à jour à partir des sources utilisées initialement pour créer le classeur. Ce processus est appelé **actualisation des données**, et vous pouvez actualiser les données à la demande dans [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], ou de manière planifiée avec un processus [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui s’exécute sur un serveur d’applications dans une batterie de serveurs SharePoint. Pour plus d'informations, consultez :  
  
-   [Actualisation des données Power Pivot avec SharePoint 2010](http://msdn.microsoft.com/01b54e6f-66e5-485c-acaa-3f9aa53119c9)  
  
-   [Configurer le compte d’actualisation des données PowerPivot sans assistance (PowerPivot pour SharePoint)](http://msdn.microsoft.com/81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
-   [Configurer les informations d’identification stockées pour l’actualisation des données Power Pivot (Power Pivot pour SharePoint)](http://msdn.microsoft.com/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)  
  
-   [Planifier une actualisation des données (PowerPivot pour SharePoint)](http://msdn.microsoft.com/8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
-   [Afficher l’historique d’actualisation des données &#40;Power Pivot pour SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et SharePoint Server 2013 Excel Services utilisent une architecture différente pour l'actualisation des données des modèles de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . L’architecture prise en charge par SharePoint 2013 utilise Excel Services en tant que composant principal pour charger les modèles de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . L’architecture d’actualisation des données précédente reposait sur un serveur exécutant le service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint afin de charger les modèles de données. Pour plus d'informations, consultez les documents suivants :  
> 
>  -   [Actualisation des données Power Pivot avec SharePoint 2013](../../analysis-services/power-pivot-sharepoint/power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [Mettre à niveau les classeurs et l’actualisation planifiée des données &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
