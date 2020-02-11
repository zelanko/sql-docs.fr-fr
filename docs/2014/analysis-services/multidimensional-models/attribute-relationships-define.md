---
title: Définir des relations d’attributs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
ms.assetid: 9184d344-e96d-4025-ad6f-3f75129746df
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 47a46bfd482463de2377470cd11186bd3bfbd5db
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66077062"
---
# <a name="define-attribute-relationships"></a>Définir des relations d'attributs
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], les attributs constituent le bloc de construction fondamental d’une dimension. Une dimension contient un ensemble d'attributs organisés en fonction des relations d'attributs.  
  
 Pour chaque table incluse dans une dimension, il existe une relation d'attribut qui lie l'attribut de clé de la table à d'autres attributs de cette table. Vous créez cette relation lors de la création de la dimension.  
  
 Une relation d'attribut offre les avantages suivants :  
  
-   Réduit la quantité de mémoire nécessaire au traitement de dimension. Cela accélère le traitement des dimensions, des partitions et des requêtes.  
  
-   Augmente les performances des requêtes car l'accès au stockage est plus rapide et les plans d'exécution sont mieux optimisés.  
  
-   Permet la sélection d'agrégats plus efficaces par les algorithmes de conception d'agrégation, à condition que les hiérarchies définies par l'utilisateur aient été définies avec les chemins d'accès de relation.  
  
    > [!NOTE]  
    >  Pour plus d’informations sur l’importance et les implications de la définition et de la configuration des relations d’attributs, consultez la section « amélioration des performances des requêtes » dans le [Guide des performances SQL Server 2005 Analysis Services](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).  
  
## <a name="attribute-relationship-considerations"></a>Considérations sur les relations d'attributs  
 Lorsque les données sous-jacentes le prennent en charge, il est également conseillé de définir des relations d'attributs uniques entre les attributs. Pour définir des relations d’attributs uniques, utilisez l’onglet **Relations d’attributs** du Concepteur de dimensions.  
  
 Tout attribut qui a une relation sortante doit avoir une clé unique relative à son attribut associé. En d'autres termes, un membre dans un attribut source ne doit identifier qu'un seul membre dans un attribut associé. Considérons par exemple la relation Ville ->Département. Dans cette relation, l'attribut source est Ville et l'attribut associé est Département. L’attribut source est le côté « plusieurs » et le côté associé est le côté « un » de la relation plusieurs-à-un. La clé pour l'attribut source serait Ville + Département. Pour plus d’informations, consultez [Créer, modifier ou supprimer une relation d’attribut](attribute-relationships-create-modify-or-delete-relationship.md).  
  
 Pour plus d’informations sur les propriétés d’une relation d’attribut, consultez [Configurer des propriétés de relations d’attributs](attribute-relationships-configure-attribute-properties.md).  
  
> [!NOTE]  
>  La définition incorrecte de relations d'attributs peut produire des résultats de requête non valides.  
  
## <a name="see-also"></a>Voir aussi  
 [Relations d’attributs](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
