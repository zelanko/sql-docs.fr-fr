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
ms.openlocfilehash: 7cbef7b6adae6c8650b80b8c91bfd1357dde0541
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218559"
---
# <a name="create-user-defined-hierarchies"></a>Créer des hiérarchies définies par l'utilisateur
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] permet de créer des hiérarchies définies par l’utilisateur. Une hiérarchie est une collection de niveaux basés sur des attributs. Par exemple, une hiérarchie de temps peut contenir les niveaux Année, Trimestre, Mois, Semaine et Jour. Dans certaines hiérarchies, chaque attribut de membre est lié de manière unique à l'attribut de membre du niveau supérieur. Ce type de hiérarchie est parfois appelé hiérarchie naturelle. Les utilisateurs finaux peuvent utiliser une hiérarchie pour explorer les données d'un cube. Définissez des hiérarchies à l'aide du volet Hiérarchies du Concepteur de dimensions dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Lors de la création d’une hiérarchie définie par l’utilisateur, la hiérarchie peut devenir *déséquilibrée*. Une hiérarchie déséquilibrée est une hiérarchie dans laquelle le membre parent logique d’au moins un membre ne figure pas dans le niveau immédiatement supérieur à ce membre. Si une hiérarchie est déséquilibrée, il existe des paramètres permettant de contrôler si les membres manquants sont visibles et de les afficher. Pour plus d’informations sur les hiérarchies, consultez [Hiérarchies déséquilibrées](user-defined-hierarchies-ragged-hierarchies.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur les problèmes de performances liés à la conception et à la configuration des hiérarchies définies par l’utilisateur, consultez le [Guide des performances SQL Server 2005 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=81621).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la hiérarchie utilisateur](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [Propriétés de niveau &#91;remplacées&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)   
 [Hiérarchie parent-enfant](parent-child-dimension.md)  
  
  
