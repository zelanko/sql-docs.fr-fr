---
title: Boîte de dialogue affecter une conception d’agrégation (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.copyaggregationdesign.f1
ms.assetid: 50c26cb1-c294-4f17-8b9e-435fdbd4806d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 11ee89e8849155f905e3908e491184f78a8f08b7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062229"
---
# <a name="assign-aggregation-design-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Affecter une conception d'agrégation (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Affecter une conception d'agrégation** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour affecter des conceptions d'agrégation à une ou plusieurs partitions de destination. Vous pouvez afficher la boîte de dialogue **Affecter une conception d’agrégation** en cliquant avec le bouton droit sur une partition ou une conception d’agrégation dans **l’Explorateur d’objets**, puis en sélectionnant **Affecter une conception d’agrégation**.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Conceptions d’agrégation**|Sélectionnez une conception d'agrégation à affecter à une ou plusieurs partitions de destination.|  
|**Partitions de destination**|Sélectionnez les partitions auxquelles affecter la conception d'agrégation. La grille suivante permet de définir les partitions de destination :<br /><br /> \<case à cocher> : activez ou désactivez la case à cocher dans l’en-tête de colonne pour inclure ou exclure toutes les partitions de la liste comme partitions de destination. Activez ou désactivez la case à cocher située en regard d'une partition pour inclure ou exclure cette partition en tant que partition de destination.<br /><br /> **Partition**: affiche le nom de la partition.<br /><br /> **Source**: affiche la table ou la requête source de la partition.<br /><br /> **Conception d’agrégation**: affiche le nom de la conception d’agrégation existante pour la partition.|  
|**Masquer les partitions avec des conceptions d'agrégation**|Sélectionnez pour afficher uniquement les partitions auxquelles aucune conception d'agrégation n'a été affectée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Agrégations et conceptions d'agrégation](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
