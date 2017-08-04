---
title: "Masquer ou supprimer des niveaux dans une hiérarchie dérivée (Master Data Services) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: fbaed046a052c458d228ef14d851cef572b2b6e0
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a>Masquer ou supprimer des niveaux dans une hiérarchie dérivée (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], masquez un niveau dans une hiérarchie dérivée quand le niveau est requis pour le regroupement, mais que vous n’avez pas besoin de l’afficher. Supprimez un niveau lorsque vous ne souhaitez pas l'utiliser pour le regroupement.  
  
## <a name="prerequisites"></a>Conditions préalables  
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
  
  

