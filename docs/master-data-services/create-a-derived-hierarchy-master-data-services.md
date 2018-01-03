---
title: "Créer une hiérarchie dérivée (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- derived hierarchies, creating
- creating derived hierarchies [Master Data Services]
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
caps.latest.revision: "7"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1a9069f215a9e1bbd997cdaffee909c6caedc1ef
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="create-a-derived-hierarchy-master-data-services"></a>Créer une hiérarchie dérivée (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez une hiérarchie dérivée lorsque vous avez besoin d'une hiérarchie basée sur le niveau qui vérifie que les membres existent au niveau correct. Les hiérarchies dérivées sont basées sur les relations d'attribut basé sur un domaine qui existent dans un modèle.  
  
> [!NOTE]  
>  S'il n'existe pas de valeur d'attribut basé sur un domaine pour un membre, le membre n'est pas inclus dans la hiérarchie dérivée. Pour demander une valeur d’attribut basé sur un domaine pour tous les membres, consultez [Requérir des valeurs d’attribut &#40;Master Data Services&#41;](../master-data-services/require-attribute-values-master-data-services.md).  
  
## <a name="prerequisites"></a>Prerequisites  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-derived-hierarchy"></a>Pour créer une hiérarchie dérivée  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Hiérarchies dérivées**.  
  
3.  Dans la page **Maintenance de la hiérarchie dérivée** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Cliquez sur **Ajouter**.  
  
5.  Dans la page **Ajouter une hiérarchie dérivée** , renseignez la zone **Nom de la hiérarchie dérivée** .  
  
    > [!TIP]  
    >  Utilisez un nom qui décrit les niveaux dans la hiérarchie, par exemple **Produit/Sous-catégorie/Catégorie**.  
  
6.  Cliquez sur **Enregistrer la hiérarchie dérivée**.  
  
7.  Dans la page **Modifier la hiérarchie dérivée** , dans le volet **Entités et hiérarchies disponibles** , cliquez sur une entité ou une hiérarchie et faites-la glisser vers la zone **Déposer le parent ici** dans le volet **Niveaux actuels** .  
  
8.  Continuez à faire glisser des entités ou des hiérarchies jusqu'à ce que votre hiérarchie soit terminée.  
  
9. Cliquez sur **Précédent**.  
  
## <a name="see-also"></a> Voir aussi  
 [Hiérarchies dérivées &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)   
 [Hiérarchies dérivées avec des niveaux supérieurs d’une hiérarchie dérivée&#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Attributs basés sur un domaine &#40;Master Data Services&#41;](../master-data-services/domain-based-attributes-master-data-services.md)  
  
  
