---
title: Objets (Analysis Services - données multidimensionnelles) de dimension | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 415cbc4527d21e6bd14945bf911bb6d6a67f5e38
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249419"
---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>Objets de dimension (Analysis Services - Données multidimensionnelles)
  Un objet <xref:Microsoft.AnalysisServices.Dimension> simple est composé des informations de base, des attributs et des hiérarchies. Les informations de base incluent le nom de la dimension, le type de dimension, la source de données, le mode de stockage et d'autres informations. Les attributs définissent les données effectives dans la dimension. Les attributs n'appartiennent pas nécessairement à une hiérarchie, mais les hiérarchies sont construites à partir d'attributs. Une hiérarchie crée des listes de niveaux triées et définit les façons dont la dimension peut être explorée par un utilisateur.  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes fournissent des informations supplémentaires sur la manière de concevoir et d'implémenter des objets de dimension.  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Dimensions &#40;Analysis Services - données multidimensionnelles&#41;](dimensions-analysis-services-multidimensional-data.md)|Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], les dimensions sont un composant fondamental des cubes. Les dimensions organisent les données en relation avec un domaine d'intérêt (clients, magasins ou employés, par exemple) pour les utilisateurs.|  
|[Attributs et hiérarchies d’attributs](attributes-and-attribute-hierarchies.md)|Les dimensions sont des ensembles d'attributs, liés à une ou plusieurs colonnes dans une table ou une vue de la vue de source de données.|  
|[Relations d’attributs](attribute-relationships.md)|Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attributs au sein d’une dimension sont toujours liés directement ou indirectement à l’attribut clé. Quand vous définissez une dimension basée sur un schéma en étoile, c'est-à-dire quand tous les attributs de la dimension sont dérivés de la même table relationnelle, une relation d'attribut est automatiquement définie entre l'attribut clé et chaque attribut non-clé de la dimension. Quand vous définissez une dimension basée sur un schéma en flocon, où les attributs de la dimension sont dérivés de plusieurs tables liées, une relation d'attribut est automatiquement définie comme suit :<br /><br /> -Entre l’attribut de clé et chaque non-clé attribut liées aux colonnes dans la table de dimension principale.<br />-Entre l’attribut de clé et l’attribut lié à la clé étrangère dans la table secondaire qui lie les tables de dimension sous-jacente.<br />-Entre l’attribut lié à foreign key dans la table secondaire et chaque attribut non-clé lié aux colonnes de la table secondaire.|  
  
  
