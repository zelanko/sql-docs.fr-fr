---
title: Attributs (onglet Structure de Dimension, Concepteur de dimensions) (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.attributespane.f1
ms.assetid: 627eaa08-7638-4edd-bdfa-0d8175a7cde5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 522bffc53240a7456ee77911b4f3044ffe0f231c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48229809"
---
# <a name="attributes-dimension-structure-tab-dimension-designer-analysis-services---multidimensional-data"></a>Attributs (onglet Structure de dimension, Concepteur de dimensions) (Analysis Services - Données multidimensionnelles)
  Utilisez ce volet pour gérer les attributs de la dimension sélectionnée. Vous pouvez faire glisser les attributs depuis ce volet vers le volet **Hiérarchies** pour créer des hiérarchies et des niveaux. Pour plus d’informations, consultez [Hierarchies &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](hierarchies-dimension-designer-analysis-services-multidimensional-data.md).  
  
 Pour créer un attribut, faites glisser une colonne depuis le volet **Vue de source de données** vers le volet **Attributs** en mode Liste, Arborescence ou Vue. Pour supprimer un attribut, sélectionnez **Supprimer** dans le menu contextuel.  
  
 **Pour afficher le volet attributs**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis ouvrez la dimension souhaitée.  
  
2.  S'il n'est pas sélectionné, cliquez sur l'onglet **Structure de dimension** .  
  
## <a name="options"></a>Options  
 **Attributs**  
 Affiche les attributs disponibles pour la dimension sélectionnée. Cette option peut être affichée dans les modes suivants :  
  
-   Liste  
  
     Utilisez ce mode pour créer et modifier des hiérarchies. Pour afficher les attributs en mode Liste, sélectionnez **Afficher les attributs dans** dans le menu contextuel et cliquez sur **Liste**.  
  
-   Arborescence  
  
     Utilisez ce mode pour créer et modifier des hiérarchies. Pour afficher les attributs en mode Arborescence, sélectionnez **Afficher les attributs dans** dans le menu contextuel et cliquez sur **Arborescence**.  
  
-   Grille  
  
     Utilisez ce mode pour créer manuellement des dimensions ou modifier les propriétés des attributs. Pour afficher les attributs en mode Grille, sélectionnez **Afficher les attributs dans** dans le menu contextuel et cliquez sur **Grille**.  
  
## <a name="grid-mode-options"></a>Options du mode Grille  
 Lorsque vous affichez les attributs en mode Grille, vous pouvez accéder aux colonnes répertoriées dans le tableau suivant.  
  
 **Nom**  
 Affiche le nom de l'attribut.  
  
 **Usage**  
 Définit l'utilisation de l'attribut sélectionné. Cliquez sur la flèche orientée vers le bas pour sélectionner l'une des options suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|Regular|Définit un attribut normal.|  
|Key|Définit l'attribut de clé de la dimension. Cela correspond aux membres de nœud terminal de la dimension. Il ne peut exister qu'un seul attribut clé par dimension. Pour modifier, cliquez sur le bouton avec les points de suspension (**...**) situé à côté de la propriété **KeyColumns** dans le volet **Propriétés** .|  
|Parent|Définit l'attribut parent d'une relation parent-enfant. L'attribut enfant de la relation doit toujours correspondre à l'attribut de clé.|  
|AccountType|Définit un attribut de type compte. Cette option est utilisée par le serveur ou le moteur lorsque la valeur « par compte » est affectée à la fonction d'agrégation d'une mesure.|  
  
 **Type**  
 Définit le type de l'attribut. Cliquez sur la flèche orientée vers le bas pour sélectionner l'un des choix proposés.  
  
 **Colonne clé**  
 Affiche le type de données de la colonne sous-jacente. Lorsque vous créez un attribut, cliquez sur la flèche orientée vers le bas pour sélectionner l'une des options disponibles.  
  
 **Colonne de nom**  
 Affiche l'emplacement de la colonne sous-jacente. Lorsque vous créez un attribut, cliquez sur la flèche orientée vers le bas pour sélectionner **Identique à la clé** ou **Colonne séparée**. Si vous choisissez **Colonne séparée** , la propriété **NameColumn** dans le volet **Propriétés** définit la colonne qui contient le nom à utiliser pour l'attribut.  
  
## <a name="see-also"></a>Voir aussi  
 [Structure de dimension &#40;Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](dimension-structure-dimension-designer-analysis-services-multidimensional-data.md)   
 [Hiérarchies &#40;onglet Structure de Dimension, Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](hierarchies-dimension-designer-analysis-services-multidimensional-data.md)   
 [Barre d’outils &#40;onglet Structure de Dimension, Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](toolbar-dimension-structure-designer-analysis-services-multidimensional-data.md)  
  
  
