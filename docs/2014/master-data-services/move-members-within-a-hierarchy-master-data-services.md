---
title: Déplacer des membres au sein d’une hiérarchie (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8ac35aa87c25e11b81a536297b893481c667363d
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971149"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a>Déplacer des membres au sein d'une hiérarchie (Master Data Services)
  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], déplacez les membres au sein d'une hiérarchie pour modifier leur emplacement ou l'affectation du parent.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
-   Pour les hiérarchies explicites, vous devez disposer au minimum de l’autorisation **mettre à jour** sur l’entité.  
  
-   Pour les hiérarchies dérivées, vous devez disposer au minimum d’une **mise à jour** du modèle et de tous les attributs basés sur un domaine utilisés dans la hiérarchie.  
  
### <a name="to-move-members-within-a-hierarchy"></a>Pour déplacer des membres au sein d'une hiérarchie  
  
1.  Dans la page d'accueil de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , dans la liste **Modèle** , sélectionnez un modèle.  
  
2.  Dans la liste **Version** , sélectionnez une version.  
  
3.  Cliquez sur **Explorateur**.  
  
4.  Dans la barre de menus, pointez sur **hiérarchies** , puis cliquez sur *hierarchy_name*.  
  
5.  Dans le volet **hiérarchie** , où la hiérarchie est affichée dans une arborescence, activez la case à cocher de chaque membre que vous souhaitez déplacer.  
  
6.  En haut du volet **hiérarchie** , cliquez sur **couper**.  
  
7.  Dans le volet **hiérarchie** , cliquez sur la case à cocher du membre vers lequel vous souhaitez déplacer les membres.  
  
8.  Cliquez sur **coller**.  
  
    > [!NOTE]  
    >  Dans les hiérarchies dérivées, vous pouvez uniquement déplacer des membres vers le même niveau. Par ailleurs, vous ne pouvez pas modifier l'ordre de tri des membres.  
  
## <a name="see-also"></a>Voir aussi  
 [Déplacer des membres de hiérarchie explicites à l’aide du processus de site &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)   
 [Hiérarchies dérivées &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)   
 [Hiérarchies explicites &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
