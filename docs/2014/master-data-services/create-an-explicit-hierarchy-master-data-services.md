---
title: Créer une hiérarchie explicite (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 5defabecf637a230571a954c306d207b0f1bbcfb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65483305"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a>Créer une hiérarchie explicite (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez une hiérarchie explicite lorsque vous avez besoin d'une hiérarchie déséquilibrée dans laquelle les membres peuvent exister à tous les niveaux. Les hiérarchies explicites contiennent des membres d'une entité unique.  
  
 Après avoir créé une hiérarchie explicite, vous pouvez lui ajouter des membres dans la zone fonctionnelle **Explorateur** .  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   L'entité doit être activée pour les hiérarchies et collections explicites. Pour plus d’informations, consultez [activer une entité pour les hiérarchies explicites et les Collections &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).  
  
### <a name="to-create-an-explicit-hierarchy"></a>Pour créer une hiérarchie explicite  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Entités**.  
  
3.  Dans la page **Maintenance de l'entité** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Sélectionnez la ligne de l'entité pour laquelle vous souhaitez créer une hiérarchie explicite.  
  
5.  Cliquez sur **Modifier l'entité sélectionnée**.  
  
6.  Dans la page **modifier l’entité** , dans le volet **hiérarchies explicites** , cliquez sur **Ajouter une hiérarchie explicite**.  
  
7.  Dans la page **Ajouter une hiérarchie explicite** , dans la zone nom de la **hiérarchie explicite** , tapez un nom pour la hiérarchie.  
  
8.  Décochez éventuellement la case **Hiérarchie obligatoire** pour créer la hiérarchie comme une hiérarchie non obligatoire. Pour plus d’informations sur les types de hiérarchies, consultez [Hiérarchies explicites &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).  
  
9. Cliquez sur **enregistrer la hiérarchie**.  
  
10. Dans la page **modifier l’entité** , cliquez sur enregistrer l' **entité**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Créer un membre consolidé &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [Déplacer des membres au sein d’une hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchies explicites &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [Hiérarchies dérivées avec des majuscules &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Modifier le nom d’une hiérarchie explicite &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  
