---
title: "Créer des hiérarchies définies par l’utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 64369f5abba3e8aa09c30a7ffdfbee6d5786b9ec
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="user-defined-hierarchies---create"></a>Créer des hiérarchies définies par l’utilisateur-
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vous permet de créer des hiérarchies définies par l’utilisateur. Une hiérarchie est une collection de niveaux basés sur des attributs. Par exemple, une hiérarchie de temps peut contenir les niveaux Année, Trimestre, Mois, Semaine et Jour. Dans certaines hiérarchies, chaque attribut de membre est lié de manière unique à l'attribut de membre du niveau supérieur. Ce type de hiérarchie est parfois appelé hiérarchie naturelle. Les utilisateurs finaux peuvent utiliser une hiérarchie pour explorer les données d'un cube. Définissez des hiérarchies à l'aide du volet Hiérarchies du Concepteur de dimensions dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Lors de la création d’une hiérarchie définie par l’utilisateur, la hiérarchie peut devenir *déséquilibrée*. Une hiérarchie déséquilibrée est une hiérarchie dans laquelle le membre parent logique d’au moins un membre ne figure pas dans le niveau immédiatement supérieur à ce membre. Si une hiérarchie est déséquilibrée, il existe des paramètres permettant de contrôler si les membres manquants sont visibles et de les afficher. Pour plus d’informations sur les hiérarchies, consultez [Hiérarchies déséquilibrées](../../analysis-services/multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur les problèmes de performances liés à la conception et à la configuration des hiérarchies définies par l’utilisateur, consultez le [Guide des performances SQL Server 2005 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=81621).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la hiérarchie définie par l'utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [Propriétés de niveau - hiérarchies utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)   
 [Dimensions parent-enfant](../../analysis-services/multidimensional-models/parent-child-dimension.md)  
  
  
