---
title: "Ajouter un filtre à un Dataset (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eed37e74-6a43-4d7c-9959-2d5fa6a6aba9
caps.latest.revision: 8
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 68838748a77567747cd7f44f7924738d87b68450
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="add-a-filter-to-a-dataset-report-builder-and-ssrs"></a>Ajouter un filtre à un dataset (Générateur de rapports et SSRS)
  Ajoutez un filtre à un dataset pour limiter les données dans un rapport après que les données ont été récupérées d'une source de données externe. Lorsque vous ajoutez un filtre à un dataset, toutes les parties de rapport ou régions de données utilisent uniquement les données qui correspondent aux conditions de filtre.  
  
 Pour un dataset partagé, un filtre qui s'applique à tous les éléments dépendants doit faire partie de la définition de dataset partagé sur le serveur de rapports. Un rapport ou une partie de rapport qui contient une instance d'un dataset partagé peut créer un filtre supplémentaire qui s'applique uniquement à l'instance.  
  
 Pour ajouter un filtre, vous devez spécifier une ou plusieurs conditions qui sont les équations de filtre. Une équation de filtre est composée d'une expression qui identifie les données que vous souhaitez filtrer, d'un opérateur et de la valeur de comparaison. Les types de données des données filtrées et de la valeur doivent correspondre. Le filtrage sur des valeurs d'agrégation n'est pas pris en charge pour les datasets.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-filter-to-a-shared-dataset"></a>Pour ajouter un filtre à un dataset partagé  
  
1.  Ouvrez un dataset partagé en mode de dataset partagé.  
  
2.  Sous l'onglet **Accueil** , dans le groupe **Datasets partagés** , cliquez sur Datasets. La boîte de dialogue **Propriétés du dataset** s'ouvre.  
  
3.  Cliquez sur **Filtres**. La liste actuelle des équations de filtre s'affiche. Par défaut, elle est vide.  
  
4.  Cliquez sur **Ajouter**. Une nouvelle équation de filtre vierge apparaît.  
  
5.  Dans **Expression**, tapez ou sélectionnez l'expression pour le champ à filtrer. Pour modifier l’expression, cliquez sur le bouton d’expression (*fx*).  
  
6.  Dans la zone de liste, sélectionnez le type de données correspondant au type de données de l'expression que vous avez créée à l'étape 5.  
  
7.  Dans la zone **Opérateur** , sélectionnez l'opérateur que le filtre doit utiliser pour comparer les valeurs des zones **Expression** et **Valeur** . L'opérateur sélectionné détermine le nombre de valeurs utilisées pour l'étape suivante.  
  
8.  Dans la zone **Valeur** , tapez l'expression ou la valeur en fonction de laquelle le filtre doit évaluer la valeur indiquée dans **Expression**.  
  
     Pour obtenir des exemples d’équations de filtre, consultez [Exemples d’équations de filtre &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/filter-equation-examples-report-builder-and-ssrs.md).  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-a-filter-to-an-embedded-dataset-or-a-shared-dataset-instance"></a>Pour ajouter un filtre à un dataset incorporé ou une instance de dataset partagé  
  
1.  Ouvrez un rapport en mode création de rapport.  
  
2.  Dans le volet **Données du rapport** , cliquez avec le bouton droit sur un dataset, puis cliquez sur **Propriétés du dataset**. La boîte de dialogue **Propriétés du dataset** s'ouvre.  
  
3.  Cliquez sur **Filtres**. La liste actuelle des équations de filtre s'affiche. Par défaut, elle est vide.  
  
4.  Cliquez sur **Ajouter**. Une nouvelle équation de filtre vierge apparaît.  
  
5.  Dans **Expression**, tapez ou sélectionnez l'expression pour le champ à filtrer. Pour modifier l’expression, cliquez sur le bouton d’expression (*fx*).  
  
6.  Dans la liste déroulante, sélectionnez le type de données correspondant au type de données de l'expression que vous avez créée à l'étape 5.  
  
7.  Dans la zone **Opérateur** , sélectionnez l'opérateur que le filtre doit utiliser pour comparer les valeurs des zones **Expression** et **Valeur** . L'opérateur sélectionné détermine le nombre de valeurs utilisées pour l'étape suivante.  
  
8.  Dans la zone **Valeur** , tapez l'expression ou la valeur en fonction de laquelle le filtre doit évaluer la valeur indiquée dans **Expression**.  
  
     Pour obtenir des exemples d’équations de filtre, consultez [Exemples d’équations de filtre &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/filter-equation-examples-report-builder-and-ssrs.md).  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des filtres de Dataset, filtres de régions de données et les filtres de groupe &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Exemples d’expressions &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Ajouter un filtre &#40; Le Générateur de rapports et SSRS &#41;](../../reporting-services/report-design/add-a-filter-report-builder-and-ssrs.md)  
  
  

