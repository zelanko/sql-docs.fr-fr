---
title: "Impossible de charger fichier ou ensemble de Services de données Microsoft | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0daa7111e93a81c367fda433cc7b530a4c90e8f4
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="could-not-load-file-or-assembly-microsoft-data-services"></a>Impossible de charger fichier ou ensemble de Services de données Microsoft
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Dans les environnements SharePoint 2010 qui disposent de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint, cette erreur se produira si vous tentez une exportation de flux de données et que la version requise de Microsoft ADO.NET Data Services n’est pas disponible sur le système.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S'applique à|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|ADO.NET Data Services 3.5 SP1 est introuvable.|  
|Texte du message|Impossible de charger le fichier ou l'assembly 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' ou une de ses dépendances. Le système ne trouve pas le fichier spécifié.|  
  
## <a name="explanation"></a>Explication  
 SharePoint 2010 inclut un bouton Exporter en tant que flux que vous pouvez utiliser pour exporter une liste SharePoint en tant que flux de données XML. De plus, Reporting Services en mode SharePoint et [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint prennent tous les deux en charge les fonctionnalités de flux de données requises par ADO.NET Data Services.  
  
 Si ADO.NET Data Services n'est pas installé, cette erreur se produira lorsque vous demanderez un flux.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
1.  Accédez à la documentation relative à la configuration matérielle et logicielle requise pour SharePoint 2010, [Déterminer la configuration matérielle et logicielle requise (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=169734) (http://go.microsoft.com/fwlink/?LinkId=169734).  
  
2.  Dans **Installer les logiciels requis**, recherchez le lien pour ADO.NET Data Services 3.5 correspondant au système d'exploitation que vous utilisez.  
  
3.  Cliquez sur le lien, puis exécutez le programme d'installation qui installe le service.  
  
## <a name="see-also"></a>Voir aussi  
 [Déployer des solutions Power Pivot sur SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
