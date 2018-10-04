---
title: Dépanner un PowerPivot pour SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a80e3134fc734f962fa9b082374dc3f9c4a74ba2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48147249"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a>Dépanner une installation PowerPivot pour SharePoint
  Si vous obtenez des erreurs au lieu des pages et fonctionnalités attendues, procédez comme indiqué ci-dessous.  
  
-   Lisez les notes de publication pour SharePoint et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour prendre connaissance des solutions de contournement pour les problèmes d'installation connus. Les notes de publication sont fournies avec le support d'installation ou sur le site Microsoft à partir duquel vous avez téléchargé le logiciel.  
  
    -   [Notes de mise à jour de SQL Server 2014](http://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).  
  
-   Consultez la rubrique wiki Technet, [Dépannage des installations de PowerPivot (et autres compléments)](http://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx).  
  
## <a name="issues"></a>Problèmes  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a>Les images miniatures de la Galerie PowerPivot s'affichent sous la forme d'une croix (X) rouge  
 L'une des causes possibles est que la **Fonctionnalité d'intégration PowerPivot pour les collections de sites** n'est pas active. Procédez comme suit :  
  
1.  Dans la bibliothèque galerie PowerPivot, cliquez sur **paramètres du Site** à partir de l’icône d’engrenage ![paramètres SharePoint](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "paramètres SharePoint") ou **accueil** liste.  
  
2.  Dans la section **Administration de la collection de sites** , cliquez sur **Fonctionnalités de la collection de sites**.  
  
3.  Cliquez sur **Fonctionnalités de la collection de sites**.  
  
4.  Vérifiez que **Fonctionnalité d'intégration PowerPivot pour les collections de sites** est **Activée**.  
  
 Pour d’autres causes de ce problème, consultez [galerie PowerPivot affiche des croix (x) rouge pour les icônes](http://support.microsoft.com/kb/2361559) (http://support.microsoft.com/kb/2361559).  
  
  
