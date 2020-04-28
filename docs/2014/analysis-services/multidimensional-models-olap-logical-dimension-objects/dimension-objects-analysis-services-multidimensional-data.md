---
title: Objets de dimension (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c0c64f95b0c366453e1099c80d8e40b217fb7801
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62702462"
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>Objets de dimension (Analysis Services - Données multidimensionnelles)
  Un objet <xref:Microsoft.AnalysisServices.Dimension> simple est composé des informations de base, des attributs et des hiérarchies. Les informations de base incluent le nom de la dimension, le type de dimension, la source de données, le mode de stockage et d'autres informations. Les attributs définissent les données effectives dans la dimension. Les attributs n'appartiennent pas nécessairement à une hiérarchie, mais les hiérarchies sont construites à partir d'attributs. Une hiérarchie crée des listes de niveaux triées et définit les façons dont la dimension peut être explorée par un utilisateur.  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes fournissent des informations supplémentaires sur la manière de concevoir et d'implémenter des objets de dimension.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Dimensions &#40;Analysis Services - Données multidimensionnelles&#41;](dimensions-analysis-services-multidimensional-data.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], les dimensions sont un composant fondamental des cubes. Les dimensions organisent les données en relation avec un domaine d'intérêt (clients, magasins ou employés, par exemple) pour les utilisateurs.|  
|[Attributs et hiérarchies d'attributs](attributes-and-attribute-hierarchies.md)|Les dimensions sont des ensembles d'attributs, liés à une ou plusieurs colonnes dans une table ou une vue de la vue de source de données.|  
|[Relations d’attributs](attribute-relationships.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], les attributs d’une dimension sont toujours liés directement ou indirectement à l’attribut de clé. Quand vous définissez une dimension basée sur un schéma en étoile, c'est-à-dire quand tous les attributs de la dimension sont dérivés de la même table relationnelle, une relation d'attribut est automatiquement définie entre l'attribut clé et chaque attribut non-clé de la dimension. Quand vous définissez une dimension basée sur un schéma en flocon, où les attributs de la dimension sont dérivés de plusieurs tables liées, une relation d'attribut est automatiquement définie comme suit :<br /><br /> -Entre l’attribut clé et chaque attribut non-clé lié aux colonnes de la table de dimension principale.<br />-Entre l’attribut clé et l’attribut lié à la clé étrangère dans la table secondaire qui lie les tables de dimension sous-jacentes.<br />-Entre l’attribut lié à la clé étrangère dans la table secondaire et chaque attribut non-clé lié aux colonnes de la table secondaire.|  
  
  
