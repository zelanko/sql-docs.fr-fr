---
title: Supprimer une hiérarchie explicite (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 048d0c4bc88f28274dc7efd686ad075242e926ee
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65483092"
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a>Supprimer une hiérarchie explicite (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], supprimez une hiérarchie explicite lorsque vous n'en avez plus besoin.  
  
> [!WARNING]  
>  Lorsque vous supprimez une hiérarchie explicite, tous les membres consolidés de la hiérarchie sont également supprimés. Si vous supprimez toutes les hiérarchies explicites d'une entité, toutes les collections de l'entité sont également supprimées et l'entité n'est plus activée pour les hiérarchies explicites et les collections.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-delete-an-explicit-hierarchy"></a>Pour supprimer une hiérarchie explicite  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Entités**.  
  
3.  Dans la page **Maintenance de l'entité** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Sélectionnez la ligne de l'entité qui contient la hiérarchie explicite à supprimer.  
  
5.  Cliquez sur **Modifier l'entité sélectionnée**.  
  
6.  Sur le **modifier l’entité** page, dans le **hiérarchies explicites** volet, cliquez sur la hiérarchie explicite à supprimer.  
  
7.  Cliquez sur **supprimer la hiérarchie sélectionnée**.  
  
8.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
9. Dans la boîte de dialogue de confirmation supplémentaire, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une hiérarchie explicite &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [Hiérarchies explicites &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
