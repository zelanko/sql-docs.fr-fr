---
title: Attributs et hiérarchies d’attributs | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- regular attributes [Analysis Services]
- parent attributes [Analysis Services]
- hierarchies [Analysis Services], attribute
- attributes [Analysis Services], about attributes
- account attributes [Analysis Services]
- dimensions [Analysis Services], attributes
- key attributes [Analysis Services]
- OLAP objects [Analysis Services], attributes
- attributes [Analysis Services], relationships
- attributes [Analysis Services]
- relationships [Analysis Services], attributes
ms.assetid: 59de1ea2-e7a9-4a53-9ee0-14be52e95643
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6c1f1c6644e14beaee7bdcab9e3f50129f73b7bc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62727393"
---
# <a name="attributes-and-attribute-hierarchies"></a>Attributs et hiérarchies d'attributs
  Les dimensions sont des ensembles d'attributs, liés à une ou plusieurs colonnes dans une table ou une vue de la vue de source de données.  
  
## <a name="key-attribute"></a>Attribut clé  
 Chaque dimension contient un attribut clé. Chaque attribut est lié à une ou plusieurs colonnes dans une table de dimension. Un attribut clé est l'attribut d'une dimension, qui identifie les colonnes dans la table principale de la dimension qui sont utilisées dans des relations de clé étrangère avec la table de faits. Généralement, l'attribut clé représente la colonne ou les colonnes clés primaires de la table de dimension. Vous pouvez définir une clé primaire logique dans une table d'une vue de source de données qui n'a pas de clé primaire physique dans la source de données sous-jacente. **Pour plus d’informations**, consultez [définir des clés primaires logiques dans une vue de Source de données &#40;Analysis Services&#41;](../multidimensional-models/define-logical-primary-keys-in-a-data-source-view-analysis-services.md). Lorsque vous définissez des attributs clés, l'Assistant Cube et l'Assistant Dimension tentent d'utiliser les colonnes clés primaires de la table de dimension dans la vue de source de données. Si la table de dimension n'a pas une clé primaire logique ou une clé primaire physique, les Assistants ne peuvent pas définir correctement les attributs clés de la dimension.  
  
## <a name="binding-an-attribute-to-columns-in-data-source-view-tables-or-views"></a>Liaison d'un attribut à des colonnes de vues ou de tables de vue de source de données  
 Un attribut est lié à des colonnes d'une ou plusieurs vues ou tables de vue de source de données. Il est toujours lié à une ou plusieurs colonnes clés, qui déterminent les membres qui sont contenus dans l'attribut. Par défaut, il s'agit de la seule colonne à laquelle est lié un attribut. Un attribut peut aussi être lié à une ou plusieurs autres colonnes à des fins spécifiques. Par exemple, une propriété `NameColumn` d'un attribut détermine le nom qui apparaît à l'utilisateur pour chaque membre d'attribut : cette propriété de l'attribut peut être liée à une colonne de dimension particulière via une vue de source de données ou bien elle peut être liée à une colonne calculée de la vue de source de données. Pour plus d’informations, consultez [référence des propriétés d’attribut de dimension](../multidimensional-models/dimension-attribute-properties-reference.md).  
  
## <a name="attribute-hierarchies"></a>Hiérarchies d'attributs  
 Par défaut, les membres d'attribut sont organisés en hiérarchies à deux niveaux, constituées d'un niveau feuille et d'un niveau Tous. Le niveau Tous contient la valeur agrégée des membres de l'attribut à travers les mesures de chaque groupe de mesures dont la dimension à laquelle l'attribut se rapporte est membre. Cependant, si la propriété `IsAggregatable` est définie à False, le niveau Tous n'est pas créé. Pour plus d’informations, consultez [référence des propriétés d’attribut de dimension](../multidimensional-models/dimension-attribute-properties-reference.md).  
  
 Les attributs peuvent être - et c'est généralement le cas - organisés en hiérarchies définies par l'utilisateur, qui fournissent des chemins d'accès d'exploration par lesquels les utilisateurs peuvent parcourir les données dans les groupes de mesures auquel l'attribut se rapporte. Dans les applications clientes, les attributs peuvent être utilisés pour fournir des informations de regroupement et de contrainte. Lorsque les attributs sont organisés en hiérarchies définies par l’utilisateur, vous définissez des relations entre les niveaux de la hiérarchie lorsque les niveaux sont liés dans une relation plusieurs-à-un ou un-à-un (appelée relation *naturelle* ). Par exemple, dans une hiérarchie de calendrier, le niveau Jour doit être associé au niveau Mois, le niveau Mois doit être associé au niveau Trimestre, etc. La création de relations entre les niveaux dans une hiérarchie définie par l'utilisateur permet à Analysis Services de définir plusieurs agrégations utiles pour améliorer les performances des requêtes et économiser la mémoire lors du traitement, ce qui peut être crucial avec des cubes complexes et volumineux. Pour plus d’informations, consultez [hiérarchies utilisateur](user-hierarchies.md), [créer des hiérarchies définies par l’utilisateur](../multidimensional-models/user-defined-hierarchies-create.md)et définir des relations d' [attributs](../multidimensional-models/attribute-relationships-define.md).  
  
## <a name="attribute-relationships-star-schemas-and-snowflake-schemas"></a>Relations d'attributs, schémas en étoile et schémas en flocon  
 Par défaut, dans un schéma en étoile, tous les attributs sont directement liés à l'attribut clé, qui permet aux utilisateurs de parcourir les faits du cube sur la base de l'une des hiérarchies d'attributs de la dimension. Dans un schéma en flocon, tous les attributs sont soit directement liés à l'attribut clé si leur table sous-jacente est directement liée à la table de faits, soit indirectement liés au moyen de l'attribut qui est lié à la clé de la table sous-jacente qui lie la table en flocon à la table directement liée.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des hiérarchies définies par l’utilisateur](../multidimensional-models/user-defined-hierarchies-create.md)   
 [Définir des relations d’attributs](../multidimensional-models/attribute-relationships-define.md)   
 [Référence des propriétés d’attribut de dimension](../multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
