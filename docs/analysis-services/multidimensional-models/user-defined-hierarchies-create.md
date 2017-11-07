---
title: "Créer des hiérarchies définies par l’utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 51e4bcb074da0b11587d8783008fd250fa8867fe
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="user-defined-hierarchies---create"></a>Créer des hiérarchies définies par l’utilisateur-
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] permet de créer des hiérarchies définies par l’utilisateur. Une hiérarchie est une collection de niveaux basés sur des attributs. Par exemple, une hiérarchie de temps peut contenir les niveaux Année, Trimestre, Mois, Semaine et Jour. Dans certaines hiérarchies, chaque attribut de membre est lié de manière unique à l'attribut de membre du niveau supérieur. Ce type de hiérarchie est parfois appelé hiérarchie naturelle. Les utilisateurs finaux peuvent utiliser une hiérarchie pour explorer les données d'un cube. Définissez des hiérarchies à l'aide du volet Hiérarchies du Concepteur de dimensions dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Lors de la création d’une hiérarchie définie par l’utilisateur, la hiérarchie peut devenir *déséquilibrée*. Une hiérarchie déséquilibrée est une hiérarchie dans laquelle le membre parent logique d’au moins un membre ne figure pas dans le niveau immédiatement supérieur à ce membre. Si une hiérarchie est déséquilibrée, il existe des paramètres permettant de contrôler si les membres manquants sont visibles et de les afficher. Pour plus d’informations sur les hiérarchies, consultez [Hiérarchies déséquilibrées](../../analysis-services/multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur les problèmes de performances liés à la conception et à la configuration des hiérarchies définies par l’utilisateur, consultez le [Guide des performances SQL Server 2005 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=81621).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la hiérarchie définie par l'utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [Propriétés de niveau - hiérarchies utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)   
 [Dimensions parent-enfant](../../analysis-services/multidimensional-models/parent-child-dimension.md)  
  
  

