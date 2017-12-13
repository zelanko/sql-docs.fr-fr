---
title: "Définir des relations d’attributs | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
ms.assetid: 9184d344-e96d-4025-ad6f-3f75129746df
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fd9bce97f6df5c602ce549dc3549ddaf6739f975
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="attribute-relationships---define"></a>Attribut de relations - définir
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], les attributs sont le bloc de construction fondamental d’une dimension. Une dimension contient un ensemble d'attributs organisés en fonction des relations d'attributs.  
  
 Pour chaque table incluse dans une dimension, il existe une relation d'attribut qui lie l'attribut de clé de la table à d'autres attributs de cette table. Vous créez cette relation lors de la création de la dimension.  
  
 Une relation d'attribut offre les avantages suivants :  
  
-   Réduit la quantité de mémoire nécessaire au traitement de dimension. Cela accélère le traitement des dimensions, des partitions et des requêtes.  
  
-   Augmente les performances des requêtes car l'accès au stockage est plus rapide et les plans d'exécution sont mieux optimisés.  
  
-   Permet la sélection d'agrégats plus efficaces par les algorithmes de conception d'agrégation, à condition que les hiérarchies définies par l'utilisateur aient été définies avec les chemins d'accès de relation.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur l’importance et les implications de la définition et de la configuration des relations d’attributs, consultez la section relative à l’optimisation des performances des requêtes dans le [Guide des performances SQL Server 2005 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=81621).  
  
## <a name="attribute-relationship-considerations"></a>Considérations sur les relations d'attributs  
 Lorsque les données sous-jacentes le prennent en charge, il est également conseillé de définir des relations d'attributs uniques entre les attributs. Pour définir des relations d’attributs uniques, utilisez l’onglet **Relations d’attributs** du Concepteur de dimensions.  
  
 Tout attribut qui a une relation sortante doit avoir une clé unique relative à son attribut associé. En d'autres termes, un membre dans un attribut source ne doit identifier qu'un seul membre dans un attribut associé. Considérons par exemple la relation Ville ->Département. Dans cette relation, l'attribut source est Ville et l'attribut associé est Département. L'attribut source représente le côté « plusieurs » et l'attribut associé désigne le côté « un » de la relation plusieurs-à-un. La clé pour l'attribut source serait Ville + Département. Pour plus d’informations, consultez [Créer, modifier ou supprimer une relation d’attribut](../../analysis-services/multidimensional-models/attribute-relationships-create-modify-or-delete-relationship.md).  
  
 Pour plus d’informations sur les propriétés d’une relation d’attribut, consultez [Configurer des propriétés de relations d’attributs](../../analysis-services/multidimensional-models/attribute-relationships-configure-attribute-properties.md).  
  
> [!NOTE]  
>  La définition incorrecte de relations d'attributs peut produire des résultats de requête non valides.  
  
## <a name="see-also"></a>Voir aussi  
 [Relations d’attributs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
