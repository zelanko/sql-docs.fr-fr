---
title: Détails (boîte de dialogue Source de Partition) de la liaison de requête (Analysis Services - données multidimensionnelles) | Documents Microsoft
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
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3e9a9fc76282ebd231e18aec24fe6a9d28650100
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154478"
---
# <a name="query-binding-detail-partition-source-dialog-box-analysis-services---multidimensional-data"></a>Détails de la liaison de requête (boîte de dialogue Source de partition) (Analysis Services - Données multidimensionnelles)
  Utilisez l’option **Liaison de requête** de la boîte de dialogue **Source de partition** pour définir la requête qui fournit les données de la partition. Vous pouvez afficher ce volet en sélectionnant **Liaison de requête** dans l’option **Type de liaison** de la boîte de dialogue **Source de partition** .  
  
## <a name="options"></a>Options  
 **Source de données**  
 Sélectionnez la source de données sur laquelle la requête est exécutée pour fournir les données de faits de la partition.  
  
 **Requête**  
 Tapez ou modifiez l'instruction SQL utilisée lors de l'extraction des données de faits lors du traitement de la partition.  
  
> [!IMPORTANT]  
>  Si vous spécifiez une clause WHERE, vous pouvez utiliser un sous-ensemble d'enregistrements de cette partition. Ceci est essentiel pour éviter la duplication de données lorsque plusieurs partitions sont dérivées d'une seule table de faits. Pour plus d’informations, consultez [Partition Source Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Vérifier**  
 Cliquez pour vérifier que l’instruction **Requête** est une instruction SQL valide.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Source de partition &#40;Analysis Services - données multidimensionnelles&#41;](partition-source-dialog-box-analysis-services-multidimensional-data.md)  
  
  