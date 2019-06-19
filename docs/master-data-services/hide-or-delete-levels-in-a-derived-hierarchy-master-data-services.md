---
title: Masquer ou supprimer des niveaux dans une hiérarchie dérivée (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: b1d39db15c118a3f76bfc99d2236c644d71082f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65484284"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a>Masquer ou supprimer des niveaux dans une hiérarchie dérivée (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], masquez un niveau dans une hiérarchie dérivée quand le niveau est requis pour le regroupement, mais que vous n’avez pas besoin de l’afficher. Supprimez un niveau lorsque vous ne souhaitez pas l'utiliser pour le regroupement.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a>Pour masquer ou supprimer des niveaux dans une hiérarchie dérivée  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Hiérarchies dérivées**.  
  
3.  Dans la page **Maintenance de la hiérarchie dérivée** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Sélectionnez la ligne de la hiérarchie dérivée à modifier.  
  
5.  Cliquez sur **Modifier**.  
  
6.  Dans le volet **Niveaux actuels** :  
  
    -   Pour masquer un niveau, cliquez sur un niveau autre que le niveau supérieur ou inférieur. Dans la liste **Visible** , sélectionnez **Non**. Cliquez ensuite sur **Enregistrer l’élément de hiérarchie sélectionné**.  
  
    -   Pour supprimer le niveau supérieur, cliquez sur **Supprimer l’élément de hiérarchie sélectionné**. Dans la boîte de dialogue de confirmation, cliquez sur **OK**. Vous pouvez supprimer uniquement le niveau supérieur.  
  
## <a name="see-also"></a>Voir aussi  
    
 [Hiérarchies dérivées &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
  
