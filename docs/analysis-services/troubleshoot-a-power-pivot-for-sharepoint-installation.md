---
title: "D&#233;panner une installation Power Pivot pour SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# D&#233;panner une installation Power Pivot pour SharePoint
  Si vous obtenez des erreurs au lieu des pages et fonctionnalités attendues, procédez comme indiqué ci-dessous.  
  
-   Lisez les notes de publication pour SharePoint et [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] pour prendre connaissance des solutions de contournement pour les problèmes d'installation connus. Les notes de publication sont fournies avec le support d'installation ou sur le site Microsoft à partir duquel vous avez téléchargé le logiciel.  
  
    -   [Notes de publication de SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)  
  
-   Consultez la rubrique wiki Technet, [Troubleshooting Installations of Power Pivot (and other add-ins)](http://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx) [Dépannage des installations de Power Pivot (et d’autres compléments)].  
  
## Problèmes  
  
### Les images miniatures de la Galerie Power Pivot s’affichent sous la forme d’une croix (X) rouge  
 L’une des causes possibles est que l’option **[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour les collections de sites** n’est pas active. Procédez comme suit :  
  
1.  Dans la Galerie [!INCLUDE[ssGemini](../includes/ssgemini-md.md)], cliquez sur **Paramètres du site** à partir de l’icône représentant un engrenage ![Paramètres SharePoint](../analysis-services/media/as-sharepoint2013-settings-gear.png "Paramètres SharePoint") ou à partir de la liste **Accueil**.  
  
2.  Dans la section **Administration de la collection de sites** , cliquez sur **Fonctionnalités de la collection de sites**.  
  
3.  Cliquez sur **Fonctionnalités de la collection de sites**.  
  
4.  Vérifiez que **[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] pour les collections de sites** est définie sur **Active**.  
  
 Pour plus d’informations sur les causes de ce problème, consultez [Power Pivot Gallery shows Red X's for Icons](http://support.microsoft.com/kb/2361559) (La Galerie Power Pivot affiche des croix (X) rouges à la place des icônes) (http://support.microsoft.com/kb/2361559).  
  
  