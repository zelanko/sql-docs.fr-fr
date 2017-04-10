---
title: "Modifier le nom d’un attribut et un type de donn&#233;es (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "attributs [Master Data Services], modification de nom"
ms.assetid: d348f238-f59d-41c7-ad20-3ccd55bfd9e5
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "erikre"
caps.handback.revision: 9
---
# Modifier le nom d’un attribut et un type de donn&#233;es (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vous pouvez modifier le nom d'un attribut.  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Pour modifier le nom d’un attribut et un type  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Gérer le modèle** , sélectionnez un modèle dans la grille et cliquez sur **Entités**.  
  
3.  Dans la page **Gérer l’entité** , sélectionnez la ligne de l’entité pour laquelle vous souhaitez créer un attribut.  
  
4.  Cliquez sur **Attributs**.  
  
5.  Sur la page **Gérer les attributs** , effectuez l’une des opérations suivantes.  
  
    -   Si l’attribut concerne les membres feuille, sélectionnez **Feuille** dans la zone de liste **Types de membres** .  
  
    -   Si l’attribut concerne les membres consolidés, sélectionnez **Consolidé** dans la zone de liste **Types de membre** .  
  
    -   Si l’attribut concerne les collections, sélectionnez **Collection** dans la zone de liste **Types de membre** .  
  
6.  Sélectionnez la ligne de l’attribut que vous souhaitez modifier, puis cliquez sur **Modifier**.  
  
7.  Dans la zone **Nom** , entrez le nom mis à jour de l'attribut. Pour obtenir la liste des mots qui ne doivent pas être utilisés comme noms d’attribut, consultez [Mots réservés &#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md).  
  
8.  Dans la liste **Type d’attribut** , sélectionnez un autre type.  
  
9. Cliquez sur **Enregistrer**.  
  
## Voir aussi  
 [Créer un attribut de texte &#40;Master Data Services&#41;](../master-data-services/create-a-text-attribute-master-data-services.md)   
 [Supprimer un attribut &#40;Master Data Services&#41;](../master-data-services/delete-an-attribute-master-data-services.md)   
 [Attributs &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  