---
title: Afficher les attributs dans le concepteur de dimensions | Microsoft Docs
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
ms.openlocfilehash: 1eb12bd6499796ff7f2cfb09ccd4c176914c8117
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175800"
---
# <a name="view-attributes-in-dimension-designer"></a>Afficher les attributs dans le Concepteur de dimensions
  Les attributs sont créés sur des objets de dimension. Vous pouvez afficher et configurer les attributs à l’aide du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]concepteur de dimensions dans. Le volet **Attributs** de l'onglet **Structure de dimension** du Concepteur de dimensions répertorie les attributs qui figurent dans une dimension. Utilisez ce volet pour ajouter, supprimer ou configurer les attributs. Vous pouvez également sélectionner les attributs à utiliser comme niveau d'une nouvelle hiérarchie ou à ajouter comme niveau d'une hiérarchie existante.

 Pour afficher les attributs d'une dimension, ouvrez le concepteur de la dimension. Le volet **Attributs** de l'onglet **Structure de dimension**  du concepteur affiche les attributs qui figurent dans la dimension. Vous pouvez basculer entre une vue de liste, d’arborescence ou de grille en pointant sur **afficher les attributs dans** dans le menu **dimension** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , puis en cliquant sur l’une des commandes répertoriées dans le tableau suivant.

|Afficher les attributs dans|Description|
|------------------------|-----------------|
|**Tarifs**|Affiche les attributs sous forme de liste.<br /><br /> Cliquez avec le bouton droit sur un attribut pour le supprimer de la liste, le renommer ou modifier son utilisation.<br /><br /> Utilisez ce mode d'affichage pour construire des hiérarchies. Les informations sur les attributs et les propriétés de membre ne sont pas visibles.|
|**Arbres**|Affiche les attributs sous forme d'arborescence dont le nœud de premier niveau correspond à la dimension. Utilisez ce mode d'affichage pour afficher et créer des propriétés de membre. Il permet également de construire des hiérarchies. Développez un attribut pour afficher ses relations ou créer une relation d'attribut, en procédant comme suit :<br /><br /> Cliquez sur la dimension, un attribut ou une propriété de membre pour afficher ses propriétés dans la fenêtre **Propriétés** .<br /><br /> Cliquez avec le bouton droit sur un attribut ou sur une propriété de membre pour les supprimer de la liste, les renommer ou en modifier l'utilisation.|
|**Boutons**|Affiche les attributs sous forme de grille. Cliquez sur n'importe quelle ligne de la grille pour afficher les propriétés de cet attribut.  Utilisez ce mode d'affichage pour créer et configurer des attributs. La grille affiche les colonnes suivantes :<br /><br /> **Nom**: affiche la valeur de la propriété **nom** . Tapez un nom différent si vous souhaitez modifier ce paramètre.<br /><br /> **Utilisation**: spécifie s’il s’agit d’un attribut normal, Key, parent ou AccountType. Cliquez sur une valeur dans cette colonne pour sélectionner un autre paramètre.<br /><br /> **Type**: spécifie la catégorie Business Intelligence de l’attribut. Cliquez sur cette cellule pour sélectionner un autre paramètre.<br /><br /> **Colonne clé**: affiche le type de données OLE DB pour la propriété **KeyColumn** sur l’attribut. Cette colonne ne peut pas être modifiée.<br /><br /> **Colonne de nom**: indique si le paramètre de la propriété **NameColumn** sur l’attribut correspond à la même colonne que la valeur de la propriété **KeyColumn** . Cette colonne ne peut pas être modifiée.|

 Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], les icônes affichées dans le tableau suivant marquent les attributs en fonction de leur utilisation.

|Icône|Utilisation de l'attribut|
|----------|---------------------|
|![Icône d'attribut](../media/as-icon-attribute.gif "Icône d'attribut")|Regular ou AccountType|
|![Icône d'attribut de clé](../media/as-icon-key-attribute.gif "Icône d'attribut de clé")|Clé|
|![Icône d'attribut parent](../media/as-icon-parent-attribute.gif "Icône d'attribut parent")|Parent|

## <a name="see-also"></a>Voir aussi
 [Référence des propriétés d’attribut de dimension](dimension-attribute-properties-reference.md)


