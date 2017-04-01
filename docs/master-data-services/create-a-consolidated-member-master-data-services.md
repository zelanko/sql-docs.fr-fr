---
title: "Cr&#233;er un membre consolid&#233; (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "04/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "création de membres consolidés [Master Data Services]"
  - "membres [Master Data Services], création de membres consolidés"
  - "membres consolidés [Master Data Services], création"
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
caps.latest.revision: 12
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 11
---
# Cr&#233;er un membre consolid&#233; (Master Data Services)
  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], créez un membre consolidé lorsque vous souhaitez un nœud parent pour une hiérarchie explicite. Si vous souhaitez ajouter des données en bloc, utilisez à la place des tables de mise en lots. Pour plus d’informations, consultez [Importer des données à partir de tables &#40;Master Data Services&#41;](../master-data-services/import-data-from-tables-master-data-services.md).  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
-   Vous devez au minimum disposer de l’autorisation **Mettre à jour** concernant l’objet modèle consolidé de l’entité à laquelle vous ajoutez un membre, ainsi que d’une **autorisation Créer** sur le type consolidé sous l’entité.  
  
### Pour créer un membre consolidé  
  
1.  Dans la page d'accueil de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , dans la liste **Modèle** , sélectionnez un modèle.  
  
2.  Dans la liste **Version** , sélectionnez une version.  
  
3.  Cliquez sur **Explorateur**.  
  
4.  Dans la barre de menus, pointez sur **Hiérarchies** , puis cliquez sur le nom de la hiérarchie à laquelle vous souhaitez ajouter un membre consolidé.  
  
5.  Au-dessus de la grille, sélectionnez **Membres consolidés** ou l'option **Tous les membres consolidés de la hiérarchie** .  
  
6.  Dans le volet gauche, sélectionnez le nœud racine ou le membre consolidé sous lequel vous souhaitez créer un membre consolidé.  
  
7.  Cliquez sur **Ajouter**.  
  
8.  Dans le volet de droite, remplissez les champs.  
  
9. Ce paramètre est facultatif. Dans la zone **Annotations** , tapez un commentaire pour expliquer l'ajout du membre. Tous les utilisateurs ayant accès au membre peuvent afficher l'annotation.  
  
10. Cliquez sur **OK**.  
  
## Étapes suivantes  
  
-   [Déplacer des membres au sein d’une hiérarchie &#40;Master Data Services&#41;](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)  
  
## Voir aussi  
 [Créer une hiérarchie explicite &#40;Master Data Services&#41;](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [Créer un membre feuille &#40;Master Data Services&#41;](../master-data-services/create-a-leaf-member-master-data-services.md)   
 [Membres &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)   
 [Hiérarchies explicites &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
  