---
title: Définir un nouvel attribut automatiquement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- automatic attribute creation
- attributes [Analysis Services], creating
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 74b4e1950e6a31675994b7cae1562ff92a56de4a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299189"
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
  
  
