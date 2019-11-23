---
title: Affecter des autorisations de membre de hiérarchie
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], assigning member permissions
- members [Master Data Services], assigning permissions
ms.assetid: e1b8b46a-7cd1-4a7d-9345-dd7df081e145
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9a725ec385d72ea3719e215ea9b01c1565aadecc
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729777"
---
# <a name="assign-hierarchy-member-permissions-master-data-services"></a>Affecter des autorisations de membre de hiérarchie (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Affectez des autorisations à des membres de la hiérarchie pour permettre à des utilisateurs ou des groupes d’afficher les données dans la zone fonctionnelle **Explorateur** de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Les autorisations des membres de la hiérarchie sont facultatives. Elles améliorent la granularité des autorisations d'objet de modèle, qui sont obligatoires.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Autorisations d'accès** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-assign-hierarchy-member-permissions"></a>Pour affecter des autorisations de membre de hiérarchie  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Autorisations d'accès**.  
  
2.  Dans la page **Utilisateurs** ou **Groupes** , sélectionnez la ligne de l'utilisateur ou du groupe à modifier.  
  
3.  Cliquez sur **Modifier l'utilisateur sélectionné**.  
  
4.  Cliquez sur l'onglet **Membres de hiérarchie** .  
  
5.  Dans la liste **Modèle** , sélectionnez un modèle.  
  
6.  Dans la liste **Version** , sélectionnez une version.  
  
7.  Dans la liste **Hiérarchie** , sélectionnez une hiérarchie.  
  
8.  Cliquez sur **Modifier**.  
  
9. Développez l'arborescence, puis cliquez sur le nœud de la hiérarchie auquel vous souhaitez affecter des autorisations.  
  
10. Dans le menu, sélectionnez une combinaison d’autorisations **Créer**, **Lire, Mettre à jour** et **Supprimer** , ou **Refusez** d’octroyer des autorisation.  
  
11. Cliquez sur **Enregistrer**.  
  
    > [!NOTE]  
    >  Les autorisations des membres de la hiérarchie n'entrent pas immédiatement en vigueur. Pour plus d’informations, consultez [Appliquer immédiatement des autorisations de membre &#40;Master Data Services&#41;](../master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer des autorisations de membre de hiérarchie &#40;Master Data Services&#41;](../master-data-services/delete-hierarchy-member-permissions-master-data-services.md)   
 [Affecter des autorisations d’objet de modèle &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Autorisations des membres de la hiérarchie &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
