---
title: Spécifiez la clé de Dimension et le Type (Assistant Dimension) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 95ff2c99f01361f82b0ec29ee404958ca076d6ae
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66068389"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a>Spécifier la clé et le type de la dimension (Assistant Dimension)
  Utilisez la page **Spécifier la clé et le type de la dimension** pour définir l’attribut de clé de la dimension et indiquer si celle-ci est une dimension à variation lente (SCD).  
  
> [!NOTE]  
>  Cette page s’affiche uniquement si vous avez sélectionné **Construire la dimension sans utiliser de source de données** dans la page **Sélectionner la méthode de construction** et **Dimension standard** dans la page **Sélectionner le type de la dimension** .  
  
## <a name="options"></a>Options  
 **Attribut de clé**  
 Sélectionnez l'attribut clé de la dimension.  
  
> [!NOTE]  
>  Si aucun attribut n’est défini pour la dimension, la seule valeur disponible pour cette option est **Créez automatiquement l’attribut clé**. Cette valeur n'est pas disponible si un ou plusieurs attributs sont définis pour la dimension.  
  
 **Il s’agit d’une dimension variable**  
 Indique que la dimension est une dimension à variation lente. Cette option crée des colonnes et des attributs supplémentaires utilisables pour suivre dans le temps le mouvement des membres dans les hiérarchies de la dimension.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 de l’Assistant Dimension](dimension-wizard-f1-help.md)   
 [Dimensions &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
