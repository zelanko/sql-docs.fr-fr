---
title: Créer des hiérarchies définies par l’utilisateur | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f6ca49e3a7714134d554538ae4f37e267999f2c2
ms.sourcegitcommit: 38076f423663bdbb42f325e3d0624264e05beda1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2018
ms.locfileid: "52983860"
---
# <a name="user-defined-hierarchies---create"></a>Hiérarchies définies par l’utilisateur - Créer
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] permet de créer des hiérarchies définies par l’utilisateur. Une hiérarchie est une collection de niveaux basés sur des attributs. Par exemple, une hiérarchie de temps peut contenir les niveaux Année, Trimestre, Mois, Semaine et Jour. Dans certaines hiérarchies, chaque attribut de membre est lié de manière unique à l'attribut de membre du niveau supérieur. Ce type de hiérarchie est parfois appelé hiérarchie naturelle. Les utilisateurs finaux peuvent utiliser une hiérarchie pour explorer les données d'un cube. Définissez des hiérarchies à l'aide du volet Hiérarchies du Concepteur de dimensions dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Lors de la création d’une hiérarchie définie par l’utilisateur, la hiérarchie peut devenir *déséquilibrée*. Une hiérarchie déséquilibrée est une hiérarchie dans laquelle le membre parent logique d’au moins un membre ne figure pas dans le niveau immédiatement supérieur à ce membre. Si une hiérarchie est déséquilibrée, il existe des paramètres permettant de contrôler si les membres manquants sont visibles et de les afficher. Pour plus d’informations sur les hiérarchies, consultez [Hiérarchies déséquilibrées](../../analysis-services/multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md).  
  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la hiérarchie définie par l'utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [Propriétés de niveau - hiérarchies utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)   
 [Dimensions parent-enfant](../../analysis-services/multidimensional-models/parent-child-dimension.md)  
  
  
