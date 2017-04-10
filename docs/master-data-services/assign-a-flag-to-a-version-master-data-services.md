---
title: "Affecter un indicateur &#224; une version (Master Data Services) | Microsoft Docs"
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
  - "indicateurs de version [Master Data Services], affectation d’indicateurs"
  - "versions [Master Data Services], affectation d’indicateurs"
ms.assetid: 6629ec7e-32e7-4a1e-8b31-eb43c5923766
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Affecter un indicateur &#224; une version (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], affectez un indicateur à une version pour indiquer la version que les utilisateurs ou les systèmes d'abonnement doivent utiliser.  
  
> [!NOTE]  
>  Les indicateurs de version ne peuvent être affectés qu'à une seule version à la fois. Si vous affectez un indicateur qui est déjà affecté à une autre version, l'indicateur est déplacé vers la version que vous avez sélectionnée.  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle **Gestion des versions**.  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Vous devez créer un indicateur de version avant de l'affecter. Pour plus d’informations, consultez [Créer un indicateur de version &#40;Master Data Services&#41;](../master-data-services/create-a-version-flag-master-data-services.md).  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle Gestion des versions. Pour plus d’informations, consultez [Autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### Pour affecter un indicateur à une version  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion des versions**.  
  
2.  Dans la page **Gérer les versions**, dans la ligne correspondant à la version à laquelle vous souhaitez affecter un indicateur, double-cliquez sur la cellule dans la colonne **Indicateur**.  
  
3.  Dans la liste, sélectionnez l'indicateur à affecter.  
  
    > [!NOTE]  
    >  Si l’indicateur n’est pas disponible, il se peut qu’il soit uniquement disponible pour les versions dont l’état est **Activé**. Pour le vérifier, allez à la page **Gérer les indicateurs de version** et recherchez l’indicateur dans le champ **Versions activées uniquement**.  
  
4.  Appuyez sur ENTRÉE pour enregistrer la modification.  
  
## Voir aussi  
 [Créer un indicateur de version &#40;Master Data Services&#41;](../master-data-services/create-a-version-flag-master-data-services.md)   
 [Versions &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)  
  
  