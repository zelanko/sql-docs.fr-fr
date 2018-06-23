---
title: Spécifiez la clé et le Type (Assistant Dimension) | Documents Microsoft
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
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1ce08115251beee6dc71509bc4d3a53420ecd678
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139668"
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
 [Aide (F1) de l’Assistant Dimension](dimension-wizard-f1-help.md)   
 [Dimensions &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  