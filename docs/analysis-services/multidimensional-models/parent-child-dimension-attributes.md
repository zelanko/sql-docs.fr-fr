---
title: "Attributs dans les hiérarchies Parent-enfant | Documents Microsoft"
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
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a2e7e84b9951c019440331b829aadeaa615daa9d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="parent-child-dimension-attributes"></a>Attributs de Dimension parent-enfant
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le contenu des membres d’une dimension repose habituellement sur l’hypothèse générale suivante. Les membres feuilles contiennent des données directement dérivées des sources de données sous-jacentes, et les membres non-feuilles contiennent des données dérivées d'agrégations effectuées sur les membres enfants.  
  
 Toutefois, dans une hiérarchie parent-enfant, certains membres non-feuilles peuvent contenir des données issues de sources de données sous-jacentes en plus des données d'agrégation issues des membres enfants. Pour ces membres non-feuilles de la hiérarchie parent-enfant, des membres enfants spéciaux créés par le système contiennent les données des tables de faits sous-jacentes. Appelés *membres de données*, ces membres contiennent une valeur directement associée à un membre non-feuille et indépendante de la valeur agrégée calculée à partir des descendants du membre non-feuille.  
  
 Les membres de données ne sont disponibles que dans les dimensions dotées de hiérarchies parent-enfant et ne sont visibles que si l'attribut parent le permet. Vous pouvez utiliser le Concepteur de dimensions pour contrôler la visibilité des membres de données. Pour exposer des membres de données, affectez la valeur **NonLeafDataVisible** à la propriété **MembersWithData**de l’attribut parent. Pour masquer les membres de données contenus par l’attribut parent, affectez la valeur **NonLeafDataHidden** à la propriété **MembersWithData**sur l’attribut parent.  
  
 Cette configuration ne supplante pas le fonctionnement normal de l'agrégation pour les membres non-feuilles ; le membre de données est toujours inclus comme un membre enfant pour les besoins de l'agrégation. Cependant, une formule de cumul personnalisée peut être utilisée pour remplacer le fonctionnement normal de l'agrégation. La fonction MDX (Multidimensional Expressions) [DataMember](../../mdx/datamember-mdx.md) vous permet d’accéder à la valeur du membre de données associé quelle que soit la valeur de la propriété **MembersWithData** .  
  
 La propriété **MembersWithDataCaption** de l’attribut parent fournit à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] le modèle de nom utilisé pour générer les noms des membres de données.  
  
## <a name="using-data-members"></a>Utilisation des membres de données  
 Les membres de données sont utiles lors de l'agrégation de mesures selon des dimensions d'organisation avec des hiérarchies parent-enfant. Par exemple, l'illustration suivante représente une dimension (volume brut des ventes de produits) qui comprend trois niveaux. Le premier niveau montre le volume brut des ventes, tous commerciaux confondus. Le volume brut des ventes est regroupé par directeur commercial dans le deuxième niveau et par commercial dans le troisième niveau.  
  
 ![Dimension de chiffre d’affaires brut avec trois niveaux](../../analysis-services/multidimensional-models/media/agdatamember1.gif "dimension volume brut des ventes à trois niveaux")  
  
 Habituellement, pour le membre Directeur commercial 1, la valeur est déduite de l'agrégation des valeurs des membres Commercial 1 et Commercial 2. Cependant, comme Directeur commercial 1 a aussi l'occasion de vendre des produits, ce membre peut contenir en plus des données issues de la table des faits dans la mesure où des ventes peuvent être attribuées à Directeur commercial 1.  
  
 De plus, les commissions individuelles sont variables au sein du personnel des ventes. Dans ce cas, deux barèmes différents sont appliqués pour calculer les commissions : un pour les ventes brutes réalisées personnellement par les directeurs commerciaux, l'autre pour les ventes brutes générées par les commerciaux sous leur responsabilité. Il est donc important de pouvoir accéder aux données de la table de faits sous-jacentes pour les membres non-feuilles. Vous pouvez utiliser la fonction MDX **DataMember** pour extraire le volume des ventes brutes réalisées personnellement par le membre Directeur commercial 1 ; une expression de cumul personnalisée permet d’exclure le membre de données de la valeur d’agrégation du membre Directeur commercial 1 pour obtenir le volume des ventes réalisées par les commerciaux subordonnés à ce membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des propriétés d'attribut de dimension](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)   
 [Dimensions parent-enfant](../../analysis-services/multidimensional-models/parent-child-dimension.md)  
  
  

