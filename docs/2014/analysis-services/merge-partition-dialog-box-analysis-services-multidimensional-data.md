---
title: Fusion de la boîte de dialogue Partition (Analysis Services - données multidimensionnelles) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.sqlserverstudio.mergepartition.f1
ms.assetid: 1c94e250-ee18-4f98-b112-985f6346102a
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: aae229b83f367613cc786a3910b00b45e64f31bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141076"
---
# <a name="merge-partition-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Partition de fusion (Analysis Services - Données multidimensionnelles)
  La boîte de dialogue **Partition de fusion** de **SQL Server Management Studio** permet de fusionner des partitions pour un groupe de mesures d'un cube. Vous pouvez afficher la boîte de dialogue **Partition de fusion** en cliquant avec le bouton droit sur le dossier Partitions ou sur une partition dans **Explorateur d’objets** et en sélectionnant **Fusionner des partitions** dans le menu contextuel.  
  
## <a name="options"></a>Options  
 **Server**  
 Sélectionnez le nom de l'instance Analysis Services qui contient la partition cible.  
  
 **Nom**  
 Sélectionnez le nom d'une partition existante à utiliser comme cible.  
  
 **Dossier**  
 Affiche le nom du dossier qui contient la partition cible, si la partition indiquée dans le champ Nom n'utilise pas le dossier par défaut pour l'instance Analysis Services.  
  
 **Partitions sources**  
 Affiche une grille qui contient les partitions sources pouvant être fusionnées dans la partition cible.  
  
> [!NOTE]  
>  Seules peuvent être fusionnées les partitions appartenant au même groupe de mesures qui partagent la même conception d'agrégation.  
  
 Cette grille comporte les colonnes suivantes :  
  
|colonne|Description|  
|------------|-----------------|  
|**Fusion**|Permet de fusionner la partition source dans la partition cible.|  
|**Nom de la partition**|Affiche le nom de la partition source.|  
|**Dernier traitement**|Affiche la date et l'heure du dernier traitement de la partition source.|  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Fusionner des Partitions dans Analysis Services &#40;SSAS - multidimensionnel&#41;](multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  