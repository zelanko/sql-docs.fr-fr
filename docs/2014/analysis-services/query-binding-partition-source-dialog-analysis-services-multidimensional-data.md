---
title: Détails (boîte de dialogue Source de Partition) de la liaison de requête (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitions.partitionfilterexpression.f1
ms.assetid: 697874d4-3f7a-4126-96f5-37cc8e2ee306
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 604a42cc0b3519f1034733e12f72dc1a7c969ce6
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66070566"
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
  
  
