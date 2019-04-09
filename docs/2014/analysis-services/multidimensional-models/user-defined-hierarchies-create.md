---
title: Créer des hiérarchies définies par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c35749671caabd8c6c61249d39bb3336257b1b8a
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59242487"
---
# <a name="create-user-defined-hierarchies"></a>Créer des hiérarchies définies par l'utilisateur
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lets you create user-defined hierarchies. A hierarchy is a colpermet de créer des hiérarchies définies par l’utilisateur.rUne hiérarchie est une collection de niveaux basés sur des attributs.,Par exemple, une hiérarchie de temps peut contenir les niveaux Année, Trimestre, Mois, Semaine et Jour.hDans certaines hiérarchies, chaque attribut de membre est lié de manière unique à l'attribut de membre du niveau supérieur.rCe type de hiérarchie est parfois appelé hiérarchie naturelle.iLes utilisateurs finaux peuvent utiliser une hiérarchie pour explorer les données d'un cube. Définissez des hiérarchies à l'aide du volet Hiérarchies du Concepteur de dimensions dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Lors de la création d’une hiérarchie définie par l’utilisateur, la hiérarchie peut devenir *déséquilibrée*. Une hiérarchie déséquilibrée est une hiérarchie dans laquelle le membre parent logique d’au moins un membre ne figure pas dans le niveau immédiatement supérieur à ce membre. Si une hiérarchie est déséquilibrée, il existe des paramètres permettant de contrôler si les membres manquants sont visibles et de les afficher. Pour plus d’informations sur les hiérarchies, consultez [Hiérarchies déséquilibrées](user-defined-hierarchies-ragged-hierarchies.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur les problèmes de performances liés à la conception et à la configuration des hiérarchies définies par l’utilisateur, consultez le [Guide des performances SQL Server 2005 Analysis Services](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la hiérarchie définie par l'utilisateur](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [Propriétés de niveau &#91;remplacées&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)   
 [Hiérarchie parent-enfant](parent-child-dimension.md)  
  
  
