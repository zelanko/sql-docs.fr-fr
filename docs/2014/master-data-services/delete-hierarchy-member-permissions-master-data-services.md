---
title: Supprimer des autorisations de membre de hiérarchie (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting member permissions [Master Data Services]
- members [Master Data Services], deleting permissions
- permissions [Master Data Services], deleting member permissions
ms.assetid: 7f22d5e2-70c1-422c-99c2-e995a47d812a
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 853bc9ce4b2f0432f74e3876f9a6234042fe5b5e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65479512"
---
# <a name="delete-hierarchy-member-permissions-master-data-services"></a>Supprimer des autorisations de membre de hiérarchie (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], supprimez les autorisations d'objet de modèle pour supprimer toutes les affectations effectuées.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Autorisations d'accès** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [administrateurs &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-delete-hierarchy-member-permissions"></a>Pour supprimer des autorisations de membre de hiérarchie  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Autorisations d'accès**.  
  
2.  Dans la page **Utilisateurs** ou **Groupes** , sélectionnez la ligne de l'utilisateur ou du groupe à modifier.  
  
3.  Cliquez sur **Modifier l'utilisateur sélectionné**.  
  
4.  Cliquez sur l'onglet **Membres de hiérarchie** .  
  
5.  Dans la liste **Modèle** , sélectionnez un modèle.  
  
6.  Dans la liste **Version** , sélectionnez une version.  
  
7.  Dans le volet **Résumé des autorisations des membres** de la hiérarchie, sélectionnez la ligne de l’autorisation que vous souhaitez supprimer.  
  
8.  Cliquez sur **Supprimer l’autorisation sélectionnée**.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas supprimer une autorisation d'un utilisateur si elle est héritée d'un groupe. Vous devez supprimer l'autorisation du groupe à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations des membres de la hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Affecter des autorisations de membre de hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
  
