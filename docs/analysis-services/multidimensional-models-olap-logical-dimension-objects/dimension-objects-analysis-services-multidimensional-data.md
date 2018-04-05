---
title: Objets (Analysis Services - données multidimensionnelles) de dimension | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af27299b776158d34786d7f9c60badd1549f503f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>Objets de dimension (Analysis Services - Données multidimensionnelles)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Un simple <xref:Microsoft.AnalysisServices.Dimension> objet est composé des informations de base, des attributs et des hiérarchies. Les informations de base incluent le nom de la dimension, le type de dimension, la source de données, le mode de stockage et d'autres informations. Les attributs définissent les données effectives dans la dimension. Les attributs n'appartiennent pas nécessairement à une hiérarchie, mais les hiérarchies sont construites à partir d'attributs. Une hiérarchie crée des listes de niveaux triées et définit les façons dont la dimension peut être explorée par un utilisateur.  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes fournissent des informations supplémentaires sur la manière de concevoir et d'implémenter des objets de dimension.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Dimensions &#40;Analysis Services - Données multidimensionnelles&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], les dimensions sont un composant fondamental des cubes. Les dimensions organisent les données en relation avec un domaine d'intérêt (clients, magasins ou employés, par exemple) pour les utilisateurs.|  
|[Attributs et hiérarchies d’attributs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)|Les dimensions sont des ensembles d'attributs, liés à une ou plusieurs colonnes dans une table ou une vue de la vue de source de données.|  
|[Relations d’attributs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)|Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attributs au sein d’une dimension sont toujours liés directement ou indirectement à l’attribut clé. Quand vous définissez une dimension basée sur un schéma en étoile, c'est-à-dire quand tous les attributs de la dimension sont dérivés de la même table relationnelle, une relation d'attribut est automatiquement définie entre l'attribut clé et chaque attribut non-clé de la dimension. Quand vous définissez une dimension basée sur un schéma en flocon, où les attributs de la dimension sont dérivés de plusieurs tables liées, une relation d'attribut est automatiquement définie comme suit :<br /><br /> entre l'attribut clé et chaque attribut non-clé lié aux colonnes de la table de dimension principale ;<br /><br /> entre l'attribut clé et l'attribut lié à la clé étrangère dans la table secondaire qui lie les tables de dimension sous-jacentes ;<br /><br /> entre l'attribut lié à la clé étrangère de la table secondaire et chaque attribut non-clé lié aux colonnes de la table secondaire.|  
  
  
