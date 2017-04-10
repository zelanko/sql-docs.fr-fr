---
title: "Cr&#233;er une hi&#233;rarchie d&#233;riv&#233;e (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "hiérarchies dérivées, créer"
  - "création de hiérarchies dérivées [Master Data Services]"
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Cr&#233;er une hi&#233;rarchie d&#233;riv&#233;e (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez une hiérarchie dérivée lorsque vous avez besoin d'une hiérarchie basée sur le niveau qui vérifie que les membres existent au niveau correct. Les hiérarchies dérivées sont basées sur les relations d'attribut basé sur un domaine qui existent dans un modèle.  
  
> [!NOTE]  
>  S'il n'existe pas de valeur d'attribut basé sur un domaine pour un membre, le membre n'est pas inclus dans la hiérarchie dérivée. Pour demander une valeur d’attribut basé sur un domaine pour tous les membres, consultez [Requérir des valeurs d’attribut &#40;Master Data Services&#41;](../master-data-services/require-attribute-values-master-data-services.md).  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Pour créer une hiérarchie dérivée  
  
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
  
## Voir aussi  
 [Hiérarchies dérivées &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)   
 [Hiérarchies dérivées avec un niveau supérieur composé d’une hiérarchie explicite &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Attributs basés sur un domaine &#40;Master Data Services&#41;](../master-data-services/domain-based-attributes-master-data-services.md)  
  
  