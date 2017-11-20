---
title: "Créer un groupe d’attributs (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: master-data-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 23c3065a689b282da5d44ee81f5023cffa57e361
ms.contentlocale: fr-fr
ms.lasthandoff: 09/07/2017

---
# <a name="create-an-attribute-group-master-data-services"></a>Créer un groupe d'attributs (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez des groupes d'attributs lorsque vous souhaitez afficher des attributs sous des onglets individuels dans la grille de l' **Explorateur** .  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Au moins un attribut doit exister. Pour plus d’informations, consultez [Créer un attribut de texte &#40;Master Data Services&#41;](../master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-create-an-attribute-group"></a>Pour créer un groupe d'attributs  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Gérer le modèle** , sélectionnez un modèle dans la grille, puis cliquez sur **Entités**.  
  
3.  Dans la grille de la page **Gérer l’entité** , sélectionnez la ligne de l’entité pour laquelle vous souhaitez créer un groupe d’attributs.  
  
4.  Cliquez sur **Groupes d’attributs**.  
  
5.  Dans la page Gérer les groupes d’attributs, effectuez l’une des opérations suivantes, puis cliquez sur **Ajouter**.  
  
     Si le groupe d’attributs se rapporte aux membres feuille, sélectionnez **Feuille** dans la liste déroulante **Types de membres** en haut de la page.  
  
     Si le groupe d’attributs concerne les membres consolidés, sélectionnez **Consolidé** dans la liste déroulante **Types de membres** .  
  
     Si le groupe d’attributs est associé aux collections, sélectionnez **Collection** dans la liste déroulante **Types de membres** .  
  
6.  Cliquez sur **Groupes feuille**, **Groupes consolidés**ou **Groupes de collections** pour créer respectivement un groupe d'attributs pour les membres feuille, les membres consolidés ou les collections.  
  
7.  Dans la zone **Nom** , tapez un nom pour le groupe d’attributs. Ce nom s’affiche dans l’onglet de l’ **Explorateur**.  
  
8.  Pour ajouter un attribut, cliquez sur cet attribut dans la zone **Attributs disponibles** , puis cliquez sur la flèche **Ajouter** . Pour ajouter tous les attributs, cliquez sur la flèche **Ajouter tout** .  
  
9. Cliquez sur les flèches vers le **haut** et vers le **bas** pour modifier l’ordre de gauche à droite des attributs.  
  
10. Cliquez sur les utilisateurs dans la zone **Utilisateurs disponibles** , puis cliquez sur la flèche **Ajouter** . Pour ajouter tous les utilisateurs, cliquez sur la flèche **Ajouter tout** .  
  
11. Cliquez sur les groupes dans la zone **Groupes disponibles** , puis cliquez sur la flèche **Ajouter** . Pour ajouter tous les groupes, cliquez sur la flèche **Ajouter tout** .  
  
12. Cliquez sur **Enregistrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Rendre un groupe d’attributs visible pour les utilisateurs &#40;Master Data Services&#41;](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes d’attributs &#40;Master Data Services&#41;](../master-data-services/attribute-groups-master-data-services.md)   
 [Attributs &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)   
 [Renommer un groupe d’attributs &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-group-name-master-data-services.md)   
 [Supprimer un groupe d’attributs &#40;Master Data Services&#41;](../master-data-services/delete-an-attribute-group-master-data-services.md)   
 [Autorisations de feuille &#40;Master Data Services&#41;](../master-data-services/leaf-permissions-master-data-services.md)   
   
  
  

