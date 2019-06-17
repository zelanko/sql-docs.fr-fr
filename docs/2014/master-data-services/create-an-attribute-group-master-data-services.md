---
title: Créer un groupe d’attributs (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: c832fe601eb7151e438d7f93c3e39e9b249ea246
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65483321"
---
# <a name="create-an-attribute-group-master-data-services"></a>Créer un groupe d'attributs (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez des groupes d'attributs lorsque vous souhaitez afficher des attributs sous des onglets individuels dans la grille de l' **Explorateur** .  
  
> [!NOTE]  
>  Lorsque vous créez un groupe d'attributs, il est automatiquement masqué pour tous les utilisateurs, à l'exception de son créateur. Pour plus d’informations sur le fait de rendre visible le groupe, consultez [Rendre un groupe d’attributs visible pour les utilisateurs &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
-   Au moins un attribut doit exister. Pour plus d’informations, consultez [Créer un attribut de texte &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-create-an-attribute-group"></a>Pour créer un groupe d'attributs  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Sur le **vue de modèle** page, dans la barre de menus, pointez sur **gérer** et cliquez sur **groupes d’attributs**.  
  
3.  Dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Dans la liste **Entité** , sélectionnez une entité.  
  
5.  Cliquez sur **Groupes feuille**, **Groupes consolidés**ou **Groupes de collections** pour créer respectivement un groupe d'attributs pour les membres feuille, les membres consolidés ou les collections.  
  
6.  Cliquez sur **ajouter un groupe d’attribut**.  
  
7.  Dans le **nom du groupe feuille** , tapez un nom pour le groupe. C’est le nom affiché sous l’onglet dans **Explorer**.  
  
    > [!NOTE]  
    >  Si vous avez sélectionné **groupes consolidés** ou **groupes de collections** à l’étape 5, cette case est **nom du groupe consolidé** ou **nom du groupe Collection**, respectivement.  
  
8.  Cliquez sur **Enregistrer le groupe**.  
  
9. Développez le dossier du groupe.  
  
10. Cliquez sur **Attributs**.  
  
11. Cliquez sur **modifier l’élément sélectionné**.  
  
12. Cliquez sur les attributs dans le **disponible** , puis cliquez sur le **ajouter** flèche. Pour les ajouter tous, cliquez sur la flèche **Ajouter tout** .  
  
13. Si vous le souhaitez, cliquez sur le **des** et **vers le bas** flèches pour modifier l’ordre de gauche à droite des attributs.  
  
14. Cliquez sur **Enregistrer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Rendre un groupe d’attributs visible pour les utilisateurs &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes d’attributs &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md)   
 [Attributs &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)   
 [Modifier le nom d’un groupe d’attributs &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md)   
 [Supprimer un groupe d’attributs &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)   
 [Autorisations de feuille &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)   
 [Consolidés autorisations &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
