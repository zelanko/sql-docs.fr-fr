---
title: "N’a pas pu charger 'Microsoft.AnalysisServices.SharePoint.Integration' | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: power-pivot-sharepoint
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dec23d57b74350f9952246c5b0a0fa915b91a9d7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="could-not-load-microsoftanalysisservicessharepointintegration"></a>N’a pas pu charger Microsoft.AnalysisServices.SharePoint.Integration
  Dans les environnements SharePoint 2010 qui disposent de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint, cette erreur se produit si la solution au niveau de l’application pour [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] n’a pas été déployée correctement.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S'applique à|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|La solution Powerpivotwebapp n'est pas déployée ou n'a pas été déployée correctement.|  
|Texte du message|Impossible de charger le fichier ou l'assembly 'Microsoft.AnalysisServices.SharePoint.Integration'|  
  
## <a name="explanation"></a>Explication  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint utilise des packages de solution pour déployer ses fonctionnalités sur un serveur SharePoint. L'une des solutions n'est pas déployée correctement. Cette erreur s’affiche donc chaque fois que vous essayez d’ouvrir la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ou d’autres pages d’application [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sur un site SharePoint.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Déployez le package de solution.  
  
1.  Dans l'Administration centrale, sous Paramètres système, cliquez sur **Gérer les solutions de la batterie**.  
  
2.  Cliquez sur **Powerpivotwebapp**.  
  
3.  Cliquez sur **Déployer la solution**.  
  
4.  Choisissez l'application Web pour laquelle cette erreur se produit. S'il y a plusieurs applications Web, redéployez la solution pour chacune d'entre elles.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déployer des solutions Power Pivot sur SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
