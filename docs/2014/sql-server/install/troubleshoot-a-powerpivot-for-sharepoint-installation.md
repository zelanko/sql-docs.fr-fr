---
title: Résoudre les problèmes d’une installation PowerPivot pour SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: f70af740fb3fe8310a5306368c1bf48c6f357419
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952003"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a>Dépanner une installation PowerPivot pour SharePoint
  Si vous obtenez des erreurs au lieu des pages et fonctionnalités attendues, procédez comme indiqué ci-dessous.  
  
-   Lisez les notes de publication pour SharePoint et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour prendre connaissance des solutions de contournement pour les problèmes d'installation connus. Les notes de publication sont fournies avec le support d'installation ou sur le site Microsoft à partir duquel vous avez téléchargé le logiciel.  
  
    -   [Notes de publication de SQL Server 2014](https://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).  
  
-   Consultez la rubrique wiki Technet, [Dépannage des installations de PowerPivot (et autres compléments)](https://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx).  
  
## <a name="issues"></a>Problèmes  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a>Les images miniatures de la Galerie PowerPivot s'affichent sous la forme d'une croix (X) rouge  
 L'une des causes possibles est que la **Fonctionnalité d'intégration PowerPivot pour les collections de sites** n'est pas active. Renseignez les informations suivantes :  
  
1.  Dans la bibliothèque Galerie PowerPivot, cliquez sur **paramètres du site** à partir de l’icône engrenage ![paramètres SharePoint](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "Paramètres SharePoint") ou de la liste d' **hébergement** .  
  
2.  Dans la section **Administration de la collection de sites** , cliquez sur **Fonctionnalités de la collection de sites**.  
  
3.  Cliquez sur **Fonctionnalités de la collection de sites**.  
  
4.  Vérifiez que **Fonctionnalité d'intégration PowerPivot pour les collections de sites** est **Activée**.  
  
 Pour obtenir d’autres causes de ce problème, consultez [Galerie PowerPivot affiche des X rouges pour les icônes](https://support.microsoft.com/kb/2361559) (https://support.microsoft.com/kb/2361559).  
  
  
