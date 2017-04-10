---
title: "Approbation requise (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b475a53d-269d-49f3-bb42-965c555f80be
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Approbation requise (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], l’administrateur peut définir une entité sur Approbation requise. Toutes les modifications apportées à cette entité nécessitent que l’un des administrateurs d’entité les vérifie et les approuve.  
  
> [!NOTE]  
>  Les modifications effectuées sur les membres feuille exigent une approbation. Les modifications apportées aux hiérarchies et aux collections explicitement déconseillées contournent l’approbation.  
>   
>  Les modifications apportées au travers du processus de table de mise en lots contournent l’approbation.  
>   
>  Les modifications apportées par une règle d’entreprise contournent l’approbation.  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle Administration de système  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Une entité doit exister. Pour plus d’informations, consultez [Créer une entité &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
## Pour activer l’option Approbation requise pour une entité  
  
1.  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la grille de la page **Gérer le modèle** , sélectionnez un modèle et cliquez sur **Entités**.  
  
3.  Dans la grille de la page **Gérer l’entité** , sélectionnez la ligne de l’entité pour laquelle vous souhaitez activer  **Approbation requise** .  
  
4.  Cliquez sur **Modifier**, sélectionnez **Approbation requise**, puis cliquez sur **Enregistrer**.  
  
## Voir aussi  
 [Ensembles de modifications &#40;Master Data Services&#41;](../master-data-services/changesets-master-data-services.md)  
  
  