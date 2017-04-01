---
title: "Cr&#233;er un index (Master Data Services) | Microsoft Docs"
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
ms.assetid: d694a105-69b1-4ff6-99d3-1f408b916b81
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Cr&#233;er un index (Master Data Services)
  Créez un index personnalisé sur une liste d’attributs que vous interrogez fréquemment, afin d’améliorer les performances des requêtes.  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l’autorisation d’accéder à la zone fonctionnelle Administration de système. Pour plus d’informations, consultez [Autorisations de zone fonctionnelle &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
 **Pour créer un index**  
  
1.  Dans Master Data Manager, cliquez sur **Administration de système**.  
  
2.  Dans la page **Gérer le modèle** , sélectionnez un modèle dans la grille et cliquez sur **Entités**.  
  
3.  Dans la **grille** de la page **Gérer l’entité** , sélectionnez la ligne de l’entité pour laquelle vous souhaitez créer un index.  
  
4.  Cliquez sur **Index**.  
  
5.  Dans la zone **Nom** , indiquez le nom de l’index.  
  
6.  Sélectionnez **Est unique** si vous souhaitez créer un index unique. Pour plus d’informations sur les types d’index, consultez [Index personnalisé &#40;Master Data Services&#41;](../master-data-services/custom-index-master-data-services.md).  
  
7.  Cliquez sur les attributs dans la zone **Attributs disponibles** , puis sur la flèche **Ajouter** . Pour ajouter tous les attributs, cliquez sur la flèche **Ajouter tout** .  
  
8.  Cliquez sur **Enregistrer**.  
  
 Pour chaque index créé, une ligne avec quatre colonnes est ajoutée dans la grille. Le tableau suivant décrit les colonnes.  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|État|État de l’index.<br /><br /> Quand vous cliquez sur **Enregistrer**, l’image ![Icon for updating status](../master-data-services/media/mds-statusicon-updating.png "Icon for updating status") indique que l’index est en cours de mise à jour.<br /><br /> En cas d’erreur pendant la création ou la modification d’un index, l’image ![Icon for error status](../master-data-services/media/mds-statusicon-error.png "Icon for error status") s’affiche.<br /><br /> Dans le cas contraire, l’état présente la valeur OK, et l’image ![Icon for OK status](../master-data-services/media/mds-statusicon-ok.png "Icon for OK status") s’affiche.|  
|Nom|Nom de l'index.|  
|Est unique|Indique si l’index est unique.|  
|Sur les attributs|Affiche les noms complets des attributs sur lesquels l’index est défini.|  
  
 Lorsque vous cliquez sur un index, les informations suivantes s’affichent.  
  
-   **Créé par**: nom de l’utilisateur qui a créé l’index.  
  
-   **Le**: date et heure de création de l’index.  
  
-   **Mis à jour par**: nom de l’utilisateur qui a en dernier mis à jour l’index.  
  
-   **Le**: date et heure de mise à jour de l’index.  
  
## Étapes suivantes  
 [Modifier et supprimer un index &#40;Master Data Services&#41;](../master-data-services/edit-and-delete-an-index-master-data-services.md)  
  
## Voir aussi  
 [Index personnalisé &#40;Master Data Services&#41;](../master-data-services/custom-index-master-data-services.md)  
  
  