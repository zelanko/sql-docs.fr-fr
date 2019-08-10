---
title: Résoudre les problèmes d’une installation PowerPivot pour SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 797405386e8a6c0b9e62328699f3a73a6d845313
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892441"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a>Dépanner une installation PowerPivot pour SharePoint
  Si vous obtenez des erreurs au lieu des pages et fonctionnalités attendues, procédez comme indiqué ci-dessous.  
  
-   Lisez les notes de publication pour SharePoint et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour prendre connaissance des solutions de contournement pour les problèmes d'installation connus. Les notes de publication sont fournies avec le support d'installation ou sur le site Microsoft à partir duquel vous avez téléchargé le logiciel.  
  
    -   [Notes de mise à jour de SQL Server 2014](https://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).  
  
-   Consultez la rubrique wiki Technet, [Dépannage des installations de PowerPivot (et autres compléments)](https://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx).  
  
## <a name="issues"></a>Problèmes  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a>Les images miniatures de la Galerie PowerPivot s'affichent sous la forme d'une croix (X) rouge  
 L'une des causes possibles est que la **Fonctionnalité d'intégration PowerPivot pour les collections de sites** n'est pas active. Procédez comme suit :  
  
1.  Dans la bibliothèque Galerie PowerPivot, cliquez sur **paramètres du site** à partir de ![](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "") l’icône d’engrenage paramètres SharePoint paramètres SharePoint ou de la liste d' **hébergement** .  
  
2.  Dans la section **Administration de la collection de sites** , cliquez sur **Fonctionnalités de la collection de sites**.  
  
3.  Cliquez sur **Fonctionnalités de la collection de sites**.  
  
4.  Vérifiez que **Fonctionnalité d'intégration PowerPivot pour les collections de sites** est **Activée**.  
  
 Pour obtenir d’autres causes de ce problème, consultez [Galerie PowerPivot affiche des X rouges pour les icônes](https://support.microsoft.com/kb/2361559) (https://support.microsoft.com/kb/2361559).  
  
  
