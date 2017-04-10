---
title: "Utilisateurs et groupes (Master Data Services) | Microsoft Docs"
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
  - "utilisateurs [Master Data Services]"
  - "groupes [Master Data Services]"
  - "utilisateurs [Master Data Services], à propos des utilisateurs"
  - "groupes [Master Data Services], à propos des groupes"
ms.assetid: ed08dd2d-248e-4b68-91d4-e9961cb50eed
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Utilisateurs et groupes (Master Data Services)
  Pour accéder à l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , un utilisateur doit disposer d'un compte de domaine Windows ou d'un compte sur le serveur où [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] est installé. Pour accorder l'accès à [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , vous pouvez, au choix :  
  
-   Ajouter le compte d'utilisateur à un domaine ou à un groupe local, puis ajouter le groupe à la liste des groupes dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   Ajouter le compte d'utilisateur à la liste des utilisateurs dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
    > [!NOTE]  
    >  Lorsqu’un utilisateur appartient à un groupe qui a accès à [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], le nom de l’utilisateur est ajouté automatiquement à la liste la première fois où l’utilisateur accède à [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ou à MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].  
  
 Pour agir dans la zone fonctionnelle **Explorateur** de l'interface utilisateur, le groupe ou l'utilisateur doit avoir accès à la zone fonctionnelle **Explorateur** et disposer d'une autorisation sur les objets modèle.  
  
 Si un utilisateur ou un groupe a besoin d’un accès à d’autres zones fonctionnelles, l’utilisateur ou le groupe doit se voir attribuer un accès à ladite zone fonctionnelle.  
  
## Meilleure pratique  
 Pour simplifier l'administration, créez des groupes et affectez à chaque groupe l'autorisation sur des zones fonctionnelles et objets modèles. Vous pouvez ensuite ajouter et supprimer des utilisateurs dans les groupes sans accéder à l'interface utilisateur de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
 N'affectez pas d'autorisations supplémentaires à un utilisateur individuel et n'incluez pas un utilisateur dans plusieurs groupes qui ont accès à [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]. De plus, n'utilisez pas d'autorisations des membres de la hiérarchie à moins que vous ne souhaitiez qu'un groupe ait un accès limité à des membres spécifiques.  
  
## Voir aussi  
 [Ajouter un utilisateur &#40;Master Data Services&#41;](../master-data-services/add-a-user-master-data-services.md)   
 [Ajouter un groupe &#40;Master Data Services&#41;](../master-data-services/add-a-group-master-data-services.md)   
 [Supprimer des utilisateurs ou des groupes &#40;Master Data Services&#41;](../master-data-services/delete-users-or-groups-master-data-services.md)   
 [Tester les autorisations d’un utilisateur &#40;Master Data Services&#41;](../master-data-services/test-a-user-s-permissions-master-data-services.md)  
  
  