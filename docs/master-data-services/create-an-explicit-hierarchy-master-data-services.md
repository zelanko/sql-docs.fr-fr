---
title: "Cr&#233;er une hi&#233;rarchie explicite (Master Data Services) | Microsoft Docs"
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
  - "création de hiérarchies explicites [Master Data Services]"
  - "hiérarchies explicites, création"
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Cr&#233;er une hi&#233;rarchie explicite (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez une hiérarchie explicite lorsque vous avez besoin d'une hiérarchie déséquilibrée dans laquelle les membres peuvent exister à tous les niveaux. Les hiérarchies explicites contiennent des membres d'une entité unique.  
  
 Après avoir créé une hiérarchie explicite, vous pouvez lui ajouter des membres dans la zone fonctionnelle **Explorateur** .  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   L'entité doit être activée pour les hiérarchies et collections explicites.  
  
### Pour créer une hiérarchie explicite  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Gérer le modèle** , sélectionnez un modèle dans la grille et cliquez sur **Entités**.  
  
3.  Dans la grille de la page **Gérer l’entité** , sélectionnez la ligne de l’entité pour laquelle vous souhaitez créer une hiérarchie explicite.  
  
4.  Cliquez sur **Hiérarchies explicites**.  
  
5.  Dans la page **Gérer la hiérarchie explicite** , cliquez sur **Ajouter**.  
  
6.  Dans la zone **Nom** , tapez un nom pour la hiérarchie.  
  
7.  Décochez éventuellement la case **Hiérarchie obligatoire** pour créer la hiérarchie comme une hiérarchie non obligatoire. Pour plus d’informations sur les types de hiérarchies, consultez [Hiérarchies explicites &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md).  
  
8.  Cliquez sur **Enregistrer**.  
  
## Colonnes de la grille  
 Pour chaque hiérarchie explicite que vous créez, une ligne comportant sept colonnes est ajoutée à la grille. Ces différentes colonnes sont décrites ci-après.  
  
|Nom|Description|  
|----------|-----------------|  
|État|État de l’entité. Lorsque vous cliquez sur **Enregistrer** , l’image ci-après s’affiche pour indiquer que l’entité est en cours de mise à jour.<br /><br /> ![Icon for updating status](../master-data-services/media/mds-statusicon-updating.png "Icon for updating status")<br /><br /> En cas d’erreur lors de la création ou de la modification d’une entité, l’image suivante apparaît.<br /><br /> ![Icon for error status](../master-data-services/media/mds-statusicon-error.png "Icon for error status")<br /><br /> Si l’état présente la valeur OK, l’image ci-dessous s’affiche.<br /><br /> ![Icon for OK status](../master-data-services/media/mds-statusicon-ok.png "Icon for OK status")|  
|Nom|Nom de hiérarchie explicite.|  
|Obligatoire|Indique si la hiérarchie explicite est ou non obligatoire.|  
|Date de création|Nom de l’utilisateur ayant créé la hiérarchie explicite.|  
|Créée le|Date et heure de création de la hiérarchie explicite.|  
|Mise à jour par|Nom de l’utilisateur ayant effectué la dernière mise à jour de la hiérarchie explicite.|  
|Mise à jour le|Date et heure de la dernière mise à jour de la hiérarchie explicite.|  
  
## Étapes suivantes  
  
-   [Créer un membre consolidé &#40;Master Data Services&#41;](../master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [Déplacer des membres au sein d’une hiérarchie &#40;Master Data Services&#41;](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)  
  
## Voir aussi  
 [Hiérarchies explicites &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [Hiérarchies dérivées avec un niveau supérieur composé d’une hiérarchie explicite &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Modifier le nom d’une hiérarchie explicite &#40;Master Data Services&#41;](../master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  