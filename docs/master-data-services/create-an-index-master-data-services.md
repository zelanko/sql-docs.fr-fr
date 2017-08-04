---
title: "Créer un Index (Master Data Services) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d694a105-69b1-4ff6-99d3-1f408b916b81
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a4d03606ab8a45d6c7b326fd64b6900ac7e67356
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="create-an-index-master-data-services"></a>Créer un index (Master Data Services)
  Créez un index personnalisé sur une liste d’attributs que vous interrogez fréquemment, afin d’améliorer les performances des requêtes.  
  
## <a name="prerequisites"></a>Conditions préalables  
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
|État|État de l’index.<br /><br /> Lorsque vous cliquez sur **enregistrer**, le ![icône de mise à jour d’état](../master-data-services/media/mds-statusicon-updating.png "icône de mise à jour d’état") image s’affiche, indiquant que la mise à jour de l’index.<br /><br /> S’il existe des erreurs lors de la création ou la modification d’un index, le ![icône de statut d’erreur](../master-data-services/media/mds-statusicon-error.png "icône de statut d’erreur") image s’affiche.<br /><br /> Dans le cas contraire, l’état est OK et le ![icône pour l’état OK](../master-data-services/media/mds-statusicon-ok.png "icône pour l’état OK") image s’affiche.|  
|Nom|Nom de l'index.|  
|Est unique|Indique si l’index est unique.|  
|Sur les attributs|Affiche les noms complets des attributs sur lesquels l’index est défini.|  
  
 Lorsque vous cliquez sur un index, les informations suivantes s’affichent.  
  
-   **Créé par**: nom de l’utilisateur qui a créé l’index.  
  
-   **Le**: date et heure de création de l’index.  
  
-   **Mis à jour par**: nom de l’utilisateur qui a en dernier mis à jour l’index.  
  
-   **Le**: date et heure de mise à jour de l’index.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Modifier et supprimer un index &#40;Master Data Services&#41;](../master-data-services/edit-and-delete-an-index-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Index personnalisé &#40;Master Data Services&#41;](../master-data-services/custom-index-master-data-services.md)  
  
  
