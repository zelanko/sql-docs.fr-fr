---
title: Attributs dans les hiérarchies Parent-enfant | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data members [Analysis Services]
- nonleaf members
- MembersWithDataCaption property
- members [Analysis Services]
- members [Analysis Services], data
- leaf members
- parent-child dimensions [Analysis Services]
- MembersWithData property
ms.assetid: 249971cc-4bcd-44f1-8241-bdacc04d3d38
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bbf5919d44a4e36e1bdddaf5c34c5e3ab6aa4315
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220279"
---
# <a name="attributes-in-parent-child-hierarchies"></a>Attributs dans des hiérarchies de type parent-enfant
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], le contenu des membres d’une dimension repose habituellement sur l’hypothèse générale suivante. Les membres feuilles contiennent des données directement dérivées des sources de données sous-jacentes, et les membres non-feuilles contiennent des données dérivées d'agrégations effectuées sur les membres enfants.  
  
 Toutefois, dans une hiérarchie parent-enfant, certains membres non-feuilles peuvent contenir des données issues de sources de données sous-jacentes en plus des données d'agrégation issues des membres enfants. Pour ces membres non-feuilles de la hiérarchie parent-enfant, des membres enfants spéciaux créés par le système contiennent les données des tables de faits sous-jacentes. Appelés *membres de données*, ces membres contiennent une valeur directement associée à un membre non-feuille et indépendante de la valeur agrégée calculée à partir des descendants du membre non-feuille.  
  
 Les membres de données ne sont disponibles que dans les dimensions dotées de hiérarchies parent-enfant et ne sont visibles que si l'attribut parent le permet. Vous pouvez utiliser le Concepteur de dimensions pour contrôler la visibilité des membres de données. Pour exposer les membres de données, affectez la `MembersWithData` propriété pour l’attribut parent `NonLeafDataVisible.` pour masquer les membres de données contenus par l’attribut parent, définissez la `MembersWithData` propriété sur l’attribut parent `NonLeafDataHidden`.  
  
 Cette configuration ne supplante pas le fonctionnement normal de l'agrégation pour les membres non-feuilles ; le membre de données est toujours inclus comme un membre enfant pour les besoins de l'agrégation. Cependant, une formule de cumul personnalisée peut être utilisée pour remplacer le fonctionnement normal de l'agrégation. Le MDX (Multidimensional Expressions) [DataMember](/sql/mdx/datamember-mdx) fonction vous donne la possibilité d’accéder à la valeur du membre de données associé quelle que soit la valeur de la `MembersWithData` propriété.  
  
 Le `MembersWithDataCaption` fournit de la propriété de l’attribut parent [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] avec le modèle d’affectation de noms utilisé pour générer des noms de membre pour les membres de données.  
  
## <a name="using-data-members"></a>Utilisation des membres de données  
 Les membres de données sont utiles lors de l'agrégation de mesures selon des dimensions d'organisation avec des hiérarchies parent-enfant. Par exemple, l'illustration suivante représente une dimension (volume brut des ventes de produits) qui comprend trois niveaux. Le premier niveau montre le volume brut des ventes, tous commerciaux confondus. Le volume brut des ventes est regroupé par directeur commercial dans le deuxième niveau et par commercial dans le troisième niveau.  
  
 ![Dimension du volume des ventes avec trois niveaux](../media/agdatamember1.gif "dimension du volume des ventes avec trois niveaux")  
  
 Habituellement, pour le membre Directeur commercial 1, la valeur est déduite de l'agrégation des valeurs des membres Commercial 1 et Commercial 2. Cependant, comme Directeur commercial 1 a aussi l'occasion de vendre des produits, ce membre peut contenir en plus des données issues de la table des faits dans la mesure où des ventes peuvent être attribuées à Directeur commercial 1.  
  
 De plus, les commissions individuelles sont variables au sein du personnel des ventes. Dans ce cas, deux barèmes différents sont appliqués pour calculer les commissions : un pour les ventes brutes réalisées personnellement par les directeurs commerciaux, l'autre pour les ventes brutes générées par les commerciaux sous leur responsabilité. Il est donc important de pouvoir accéder aux données de la table de faits sous-jacentes pour les membres non-feuilles. L’expression MDX `DataMember` fonction peut être utilisée pour récupérer le volume des ventes brut individuel du membre directeur commercial 1, et une expression de cumul personnalisée peut être utilisée pour exclure le membre de données de la valeur d’agrégation du membre directeur commercial 1, en fournissant le chiffre d’affaires brut volume des ventes des commerciaux associés à ce membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Dimension Attribute Properties Reference](dimension-attribute-properties-reference.md)   
 [Hiérarchie parent-enfant](parent-child-dimension.md)  
  
  
