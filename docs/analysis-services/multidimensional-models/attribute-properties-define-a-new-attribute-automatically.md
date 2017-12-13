---
title: "Définir un nouvel attribut automatiquement | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automatic attribute creation
- attributes [Analysis Services], creating
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f0f9cd8d5bcae6b423be4744445a194bc66bb72a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="attribute-properties---define-a-new-attribute-automatically"></a>Propriétés d’attribut : permet de définir un nouvel attribut automatiquement
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Vous pouvez créer un nouvel attribut dans une dimension à l’aide de modification par glisser-déplacer dans le Concepteur de dimensions.  
  
### <a name="to-create-a-new-attribute-automatically"></a>Pour créer un nouvel attribut automatiquement  
  
1.  Dans le Concepteur de dimensions, ouvrez la dimension dans laquelle vous souhaitez créer l'attribut.  
  
2.  Sous l’onglet **Structure de dimension** , sélectionnez la colonne du tableau à laquelle vous souhaitez lier l’attribut dans le volet **Vue de source de données** , puis faites-la glisser jusqu’au volet **Attributs** .  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crée l’attribut qui a le même nom que la colonne à laquelle il est lié. Si plusieurs attributs utilisent la même colonne, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ajoute un numéro au nom de l’attribut.  
  
## <a name="see-also"></a>Voir aussi  
 [Dimensions dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)   
 [Référence des propriétés d’attribut de dimension](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
