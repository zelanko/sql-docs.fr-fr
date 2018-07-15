---
title: Déplacer des membres dans une hiérarchie (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
caps.latest.revision: 8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8048fce8af968f0a1188f8330993977bedcac7d3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252307"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a>Déplacer des membres au sein d'une hiérarchie (Master Data Services)
  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], déplacez les membres au sein d'une hiérarchie pour modifier leur emplacement ou l'affectation du parent.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
-   Pour les hiérarchies explicites, vous devez disposer d’un minimum de **mise à jour** autorisation à l’entité.  
  
-   Pour les hiérarchies dérivées, vous devez disposer d’un minimum de **mise à jour** pour le modèle et des attributs basés sur un domaine utilisés dans la hiérarchie.  
  
### <a name="to-move-members-within-a-hierarchy"></a>Pour déplacer des membres au sein d'une hiérarchie  
  
1.  Dans la page d'accueil de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , dans la liste **Modèle** , sélectionnez un modèle.  
  
2.  Dans la liste **Version** , sélectionnez une version.  
  
3.  Cliquez sur **Explorateur**.  
  
4.  Dans la barre de menus, pointez sur **hiérarchies** et cliquez sur *hierarchy_name*.  
  
5.  Dans le **hiérarchie** volet, où la hiérarchie est affichée dans une arborescence, cliquez sur la case à cocher pour chaque membre que vous souhaitez déplacer.  
  
6.  En haut de la **hiérarchie** volet, cliquez sur **couper**.  
  
7.  Dans le **hiérarchie** volet, cliquez sur la case à cocher pour le membre que vous souhaitez déplacer les membres.  
  
8.  Cliquez sur **coller**.  
  
    > [!NOTE]  
    >  Dans les hiérarchies dérivées, vous pouvez uniquement déplacer des membres vers le même niveau. Par ailleurs, vous ne pouvez pas modifier l'ordre de tri des membres.  
  
## <a name="see-also"></a>Voir aussi  
 [Déplacer des membres de hiérarchie explicite à l’aide du processus de site &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)   
 [Hiérarchies dérivées &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [Hiérarchies explicites &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
