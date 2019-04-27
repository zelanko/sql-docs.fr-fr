---
title: Restreindre les lignes (Assistant Partition) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.typefilterexpression.f1
ms.assetid: eec8da8f-eab4-4ac4-a81d-995c814f88ca
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2b86cfeedd76af51b5f9d8cc4633c73ed9cc17ea
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62748231"
---
# <a name="restrict-rows-partition-wizard"></a>Restreindre les lignes (Assistant Partition)
  Utilisez la page **Restreindre les lignes** pour limiter les lignes qui seront extraites de la table spécifiée et qui seront agrégées et incluses dans la partition.  
  
> [!NOTE]  
>  Cette page s’affiche uniquement si vous avez sélectionné une seule table dans la page **Spécifier des informations sur la source** .  
  
> [!CAUTION]  
>  Si vous avez spécifié une table dans **Tables disponibles** dans la page **Spécifier des informations sur la source** et qu’elle est utilisée par une autre partition, vous devez fournir une requête dans la page **Restreindre les lignes** , faute de quoi il existe un risque de duplication des données dans le cube.  
  
## <a name="options"></a>Options  
 **Spécifiez une requête pour restreindre les lignes**  
 Sélectionnez cette option pour entrer dans la zone **Requête** une requête qui limite les lignes.  
  
 Si **Fournir une clause WHERE** est vide lorsque cette option est sélectionnée, celle-ci contient une instruction SQL qui extrait toutes les colonnes et toutes les lignes de la table précédemment sélectionnée.  
  
 **Requête**  
 Tapez ou modifiez l'instruction SQL utilisée pour extraire les lignes de la table lorsque la partition est traitée.  
  
> [!IMPORTANT]  
>  Si vous spécifiez une clause WHERE, vous pouvez utiliser un sous-ensemble d'enregistrements de cette partition. Ceci est essentiel pour éviter la duplication de données lorsque plusieurs partitions sont dérivées d'une seule table de faits.  
  
 **Vérifier**  
 Vérifie la validité de l’instruction SQL de la zone **Requête** .  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions &#40;Analysis Services - Données multidimensionnelles&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
