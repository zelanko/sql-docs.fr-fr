---
title: Définir un nouvel attribut automatiquement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- automatic attribute creation
- attributes [Analysis Services], creating
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 40f9ae1f00dd0a6520c6d1b06111864fba02e8f2
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544804"
---
# <a name="define-a-new-attribute-automatically"></a>Définir un nouvel attribut automatiquement
  Vous pouvez créer un nouvel attribut dans une dimension en utilisant la modification par glisser-déplacer dans le Concepteur de dimensions.  
  
### <a name="to-create-a-new-attribute-automatically"></a>Pour créer un nouvel attribut automatiquement  
  
1.  Dans le Concepteur de dimensions, ouvrez la dimension dans laquelle vous souhaitez créer l'attribut.  
  
2.  Sous l’onglet **Structure de dimension** , sélectionnez la colonne du tableau à laquelle vous souhaitez lier l’attribut dans le volet **Vue de source de données** , puis faites-la glisser jusqu’au volet **Attributs** .  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crée l’attribut qui a le même nom que la colonne à laquelle il est lié. Si plusieurs attributs utilisent la même colonne, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ajoute un numéro au nom de l’attribut.  
  
## <a name="see-also"></a>Voir aussi  
 [Dimensions dans les modèles multidimensionnels](dimensions-in-multidimensional-models.md)   
 [Référence des propriétés d’attribut de dimension](dimension-attribute-properties-reference.md)  
  
  
