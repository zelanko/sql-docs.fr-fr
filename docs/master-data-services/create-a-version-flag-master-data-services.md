---
title: "Cr&#233;er un indicateur de version (Master Data Services) | Microsoft Docs"
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
  - "création d'indicateurs de version [Master Data Services]"
  - "indicateurs de version [Master Data Services], création"
  - "versions [Master Data Services], création d’indicateurs"
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Cr&#233;er un indicateur de version (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez un indicateur de version à affecter à une version. L’indicateur peut spécifier la version que les utilisateurs ou les systèmes d’abonnement doivent utiliser.  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle **Gestion des versions**.  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle Gestion des versions. Pour plus d’informations, consultez [Autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### Pour créer un indicateur de version  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Gestion des versions**.  
  
2.  Dans la page **Gérer les versions**, dans la barre de menus, pointez sur **Gérer**, puis cliquez sur **Indicateurs**.  
  
3.  Dans la page **Gérer les indicateurs de version**, dans le champ **Modèle**, sélectionnez le modèle pour lequel vous souhaitez créer un indicateur.  
  
4.  Cliquez sur **Ajouter**.  
  
5.  Renseignez la zone **Nom**.  
  
6.  Renseignez la zone **Description**.  
  
7.  Dans le champ **Versions activées uniquement**, sélectionnez **True** pour spécifier que l’indicateur ne peut être affecté qu’aux versions présentant l’état **Activé**. Sélectionnez **False** pour indiquer que l’indicateur peut être affecté aux versions présentant n’importe quel état.  
  
8.  Cliquez sur **Enregistrer**.  
  
## Étapes suivantes  
  
-   [Affecter un indicateur à une version &#40;Master Data Services&#41;](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## Voir aussi  
 [Versions &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)   
 [Modifier le nom d’un indicateur de version &#40;Master Data Services&#41;](../master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  