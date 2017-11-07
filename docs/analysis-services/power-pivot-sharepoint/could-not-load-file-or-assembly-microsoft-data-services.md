---
title: "Impossible de charger fichier ou ensemble de Services de données Microsoft | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 653e99076ed3b4aec45b116e02c20cccdde53c21
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="could-not-load-file-or-assembly-microsoft-data-services"></a>Impossible de charger fichier ou ensemble de Services de données Microsoft
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
  
  

