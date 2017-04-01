---
title: "Impossible de charger le fichier ou l&#39;assembly &#39;Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089&#39; ou une de ses d&#233;pendances. Le syst&#232;me ne trouve pas le fichier sp&#233;cifi&#233;. | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
caps.latest.revision: 7
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Impossible de charger le fichier ou l&#39;assembly &#39;Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089&#39; ou une de ses d&#233;pendances. Le syst&#232;me ne trouve pas le fichier sp&#233;cifi&#233;.
  Dans les environnements SharePoint 2010 qui disposent de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint, cette erreur se produira si vous tentez une exportation de flux de données et que la version requise de Microsoft ADO.NET Data Services n’est pas disponible sur le système.  
  
## Détails  
  
|||  
|-|-|  
|S'applique à|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|ADO.NET Data Services 3.5 SP1 est introuvable.|  
|Texte du message|Impossible de charger le fichier ou l'assembly 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' ou une de ses dépendances. Le système ne trouve pas le fichier spécifié.|  
  
## Explication  
 SharePoint 2010 inclut un bouton Exporter en tant que flux que vous pouvez utiliser pour exporter une liste SharePoint en tant que flux de données XML. De plus, Reporting Services en mode SharePoint et [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint prennent tous les deux en charge les fonctionnalités de flux de données requises par ADO.NET Data Services.  
  
 Si ADO.NET Data Services n'est pas installé, cette erreur se produira lorsque vous demanderez un flux.  
  
## Action de l'utilisateur  
  
1.  Accédez à la documentation relative à la configuration matérielle et logicielle requise pour SharePoint 2010, [Déterminer la configuration matérielle et logicielle requise (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=169734) (http://go.microsoft.com/fwlink/?LinkId=169734).  
  
2.  Dans **Installer les logiciels requis**, recherchez le lien pour ADO.NET Data Services 3.5 correspondant au système d'exploitation que vous utilisez.  
  
3.  Cliquez sur le lien, puis exécutez le programme d'installation qui installe le service.  
  
## Voir aussi  
 [Déployer des solutions Power Pivot sur SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  