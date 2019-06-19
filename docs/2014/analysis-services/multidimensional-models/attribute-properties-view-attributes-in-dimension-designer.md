---
title: Afficher les attributs dans le Concepteur de dimensions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- displaying attributes
- attributes [Analysis Services], viewing
- viewing attributes
ms.assetid: 855bef07-b72d-4ce3-bf02-de77abeee71a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec86d5e7a910b7fb17397b1601fcc912b46c4d7f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66077127"
---
# <a name="view-attributes-in-dimension-designer"></a>Afficher les attributs dans le Concepteur de dimensions
  Les attributs sont créés sur des objets de dimension. Vous pouvez afficher et configurer les attributs à l'aide du Concepteur de dimensions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Le volet **Attributs** de l'onglet **Structure de dimension** du Concepteur de dimensions répertorie les attributs qui figurent dans une dimension. Utilisez ce volet pour ajouter, supprimer ou configurer les attributs. Vous pouvez également sélectionner les attributs à utiliser comme niveau d'une nouvelle hiérarchie ou à ajouter comme niveau d'une hiérarchie existante.  
  
 Pour afficher les attributs d'une dimension, ouvrez le concepteur de la dimension. Le volet **Attributs** de l'onglet **Structure de dimension**  du concepteur affiche les attributs qui figurent dans la dimension. Vous pouvez basculer entre un affichage de liste, arborescence ou grille en pointant sur **afficher les attributs dans** sur le **Dimension** menu de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] puis en cliquant sur une des commandes affichées dans le tableau suivant.  
  
|Afficher les attributs dans|Description|  
|------------------------|-----------------|  
|**Liste**|Affiche les attributs sous forme de liste.<br /><br /> Cliquez avec le bouton droit sur un attribut pour le supprimer de la liste, le renommer ou modifier son utilisation.<br /><br /> Utilisez ce mode d'affichage pour construire des hiérarchies. Les informations sur les attributs et les propriétés de membre ne sont pas visibles.|  
|**Arborescence**|Affiche les attributs sous forme d'arborescence dont le nœud de premier niveau correspond à la dimension. Utilisez ce mode d'affichage pour afficher et créer des propriétés de membre. Il permet également de construire des hiérarchies. Développez un attribut pour afficher ses relations ou créer une relation d'attribut, en procédant comme suit :<br /><br /> Cliquez sur la dimension, un attribut ou une propriété de membre pour afficher ses propriétés dans la fenêtre **Propriétés** .<br /><br /> Cliquez avec le bouton droit sur un attribut ou sur une propriété de membre pour les supprimer de la liste, les renommer ou en modifier l'utilisation.|  
|**Grid**|Affiche les attributs sous forme de grille. Cliquez sur n'importe quelle ligne de la grille pour afficher les propriétés de cet attribut.  Utilisez ce mode d'affichage pour créer et configurer des attributs. La grille affiche les colonnes suivantes :<br /><br /> **Nom**: affiche la valeur de la **nom** propriété. Tapez un nom différent si vous souhaitez modifier ce paramètre.<br /><br /> **Utilisation**: Spécifie s’il s’agit d’un attribut Regular, Key, Parent ou AccountType. Cliquez sur une valeur dans cette colonne pour sélectionner un autre paramètre.<br /><br /> **Type**: Spécifie la catégorie de décisionnel pour l’attribut. Cliquez sur cette cellule pour sélectionner un autre paramètre.<br /><br /> **Colonne de clé**: affiche le type de données OLE DB pour le **KeyColumn** propriété sur l’attribut. Cette colonne ne peut pas être modifiée.<br /><br /> **Nom de colonne**: indique si le **NameColumn** paramètre de propriété sur l’attribut est la même colonne que la définition de la **KeyColumn** propriété. Cette colonne ne peut pas être modifiée.|  
  
 Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], les icônes affichées dans le tableau suivant marquent les attributs en fonction de leur utilisation.  
  
|Icône|Utilisation de l'attribut|  
|----------|---------------------|  
|![Icône d’attribut](../media/as-icon-attribute.gif "icône d’attribut")|Regular ou AccountType|  
|![Icône d’attribut de clé](../media/as-icon-key-attribute.gif "icône d’attribut de clé")|Touche|  
|![Icône d’attribut parent](../media/as-icon-parent-attribute.gif "icône d’attribut Parent")|Parent|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des propriétés d'attribut de dimension](dimension-attribute-properties-reference.md)  
  
  
