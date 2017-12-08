---
title: Afficher les attributs dans le Concepteur de dimensions | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying attributes
- attributes [Analysis Services], viewing
- viewing attributes
ms.assetid: 855bef07-b72d-4ce3-bf02-de77abeee71a
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ec4596584aafb35d54506d244855447b0ce67c7f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="attribute-properties---view-attributes-in-dimension-designer"></a>Propriétés d’attribut - afficher les attributs dans le Concepteur de dimensions
  Les attributs sont créés sur des objets de dimension. Vous pouvez afficher et configurer les attributs à l'aide du Concepteur de dimensions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Le volet **Attributs** de l'onglet **Structure de dimension** du Concepteur de dimensions répertorie les attributs qui figurent dans une dimension. Utilisez ce volet pour ajouter, supprimer ou configurer les attributs. Vous pouvez également sélectionner les attributs à utiliser comme niveau d'une nouvelle hiérarchie ou à ajouter comme niveau d'une hiérarchie existante.  
  
 Pour afficher les attributs d'une dimension, ouvrez le concepteur de la dimension. Le volet **Attributs** de l'onglet **Structure de dimension**  du concepteur affiche les attributs qui figurent dans la dimension. Vous pouvez basculer entre les modes d’affichage liste, arborescence ou grille en pointant sur **Afficher les attributs dans** dans le menu **Dimension** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , puis en cliquant sur l’une des commandes suivantes.  
  
1.  Afficher les attributs dans une **liste**. Affiche les attributs sous forme de liste. Cliquez avec le bouton droit sur un attribut pour le supprimer de la liste, le renommer ou modifier son utilisation. Utilisez ce mode d'affichage pour construire des hiérarchies. Les informations sur les attributs et les propriétés de membre ne sont pas visibles.  
  
2.  Afficher les attributs dans une **arborescence**. Affiche les attributs sous forme d'arborescence dont le nœud de premier niveau correspond à la dimension. Développez un attribut pour afficher ses relations ou créer une relation d'attribut, en procédant comme suit :  
  
    -   Cliquez sur la dimension, un attribut ou une propriété de membre pour afficher ses propriétés dans la fenêtre **Propriétés** .  
  
    -   Cliquez avec le bouton droit sur un attribut ou sur une propriété de membre pour les supprimer de la liste, les renommer ou en modifier l'utilisation.  
  
     Utilisez ce mode d'affichage pour afficher et créer des propriétés de membre. Il permet également de construire des hiérarchies.  
  
3.  Afficher les attributs dans une **grille**. Affiche les attributs sous forme de grille. La grille affiche les colonnes suivantes :  
  
    -   **Nom** affiche la valeur de la propriété **Name** . Tapez un nom différent si vous souhaitez modifier ce paramètre.  
  
    -   **Utilisation** spécifie s'il s'agit d'un attribut Regular, Key, Parent ou AccountType. Cliquez sur une valeur dans cette colonne pour sélectionner un autre paramètre.  
  
    -   **Type** spécifie la catégorie de décisionnel de l'attribut. Cliquez sur cette cellule pour sélectionner un autre paramètre.  
  
    -   **Colonne clé** affiche le type de données OLE DB de la propriété **KeyColumn** sur l'attribut. Cette colonne ne peut pas être modifiée.  
  
    -   **Colonne de nom** indique si la définition de la propriété **NameColumn** sur l'attribut correspond à la même colonne que la définition de la propriété **KeyColumn** . Cette colonne ne peut pas être modifiée.  
  
     Cliquez sur n'importe quelle ligne de la grille pour afficher les propriétés de cet attribut.  
  
     Utilisez ce mode d'affichage pour créer et configurer des attributs.  
  
 Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], les icônes affichées dans le tableau suivant marquent les attributs en fonction de leur utilisation.  
  
|Icône|Utilisation de l'attribut|  
|----------|---------------------|  
|![Icône d’attribut](../../analysis-services/multidimensional-models/media/as-icon-attribute.gif "icône d’attribut")|Regular ou AccountType|  
|![Icône d’attribut de clé](../../analysis-services/multidimensional-models/media/as-icon-key-attribute.gif "icône d’attribut de clé")|Clé|  
|![Icône d’attribut parent](../../analysis-services/multidimensional-models/media/as-icon-parent-attribute.gif "icône d’attribut Parent")|Parent|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des propriétés d'attribut de dimension](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
